# Permitindo recursos duplicados idênticos em uma configuração

O DSC não permite nem manipula definições de recursos conflitantes dentro de uma configuração. Em vez de tentar resolver o conflito, ele simplesmente falha. Como a reutilização de configuração é cada mais utilizada por meio de recursos de composição, etc., os conflitos ocorrerão com mais frequência. Quando definições de recursos conflitantes forem idênticas, o DSC deverá ter inteligência para permiti-las. Com esta versão, damos suporte a várias instâncias de recursos com definições idênticas:

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

Em versões anteriores, o resultado seria uma compilação com falha devido a um conflito entre as instâncias de WindowsFeature FE_IIS e WindowsFeature Worker_IIS tentando garantir que a função “Web-Server” está instalada. Observe que *todas* as propriedades que estão sendo configuradas são idênticas nessas duas configurações. Uma vez que *todas* as propriedades nesses dois recursos são idênticas, agora isso resultará em uma compilação bem-sucedida. 

Se alguma das propriedades for diferente entre os dois recursos, elas não serão consideradas idênticas e a compilação falhará:

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

Essa configuração bem semelhante falhará porque os recursos WindowsFeature FE_IIS e WindowsFeature Worker_IIS não serão mais idênticos e, portanto, entrarão em conflito.

<!--HONumber=Jun16_HO4-->


