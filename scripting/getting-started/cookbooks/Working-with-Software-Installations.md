---
title: "Trabalhando com instalações de software"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 9f60be9bebe9dfaa98f495c8e9a9c0d8c2fa5cc2

---

# Trabalhando com instalações de software
Aplicativos que foram projetados para usar o Windows Installer podem ser acessados por meio da classe **Win32\_Product** do WMI, mas nem todos os aplicativos usados atualmente usam o Windows Installer. Como o Windows Installer fornece a mais ampla variedade de técnicas padrão para trabalhar com aplicativos instalados, abordaremos principalmente estes aplicativos. Aplicativos que usam rotinas de instalação alternativas geralmente não serão gerenciados pelo Windows Installer. Técnicas específicas para trabalhar com esses aplicativos dependem do instalador do software e as decisões tomadas pelo desenvolvedor do aplicativo.

> [!NOTE]
> Aplicativos que estão instalados copiando os arquivos do aplicativo para o computador geralmente não podem ser gerenciados usando técnicas discutidas aqui. Você pode gerenciar esses aplicativos como arquivos e pastas usando as técnicas discutidas na seção "Trabalhando com arquivos e pastas".

### Listando aplicativos do Windows Installer
Para listar os aplicativos instalados com o Windows Installer em um sistema local ou remoto, use a seguinte consulta simples do WMI:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Para exibir todas as propriedades do objeto Win32\_Product na tela, use o parâmetro Properties dos cmdlets de formatação, como o cmdlet Format\-List, com um valor de \* (all).

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *
Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

Se preferir, você poderá usar o parâmetro **Get\-WmiObject Filter** para selecionar apenas o Microsoft .NET Framework 2.0. Como o filtro usado neste comando é um filtro WMI, ele usa a sintaxe de linguagem de consulta WMI (WQL), não a sintaxe do Windows PowerShell. Em vez disso:

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

Observe que as consultas WQL frequentemente usam caracteres que têm um significado especial no Windows PowerShell, como espaços ou sinais de igual. Por esse motivo, é recomendável sempre colocar o valor do parâmetro Filter entre aspas. Você também pode usar o caractere de escape do Windows PowerShell, um acento grave (\`), embora isso possa não melhorar a legibilidade. O comando a seguir é equivalente ao comando anterior e retorna os mesmos resultados, mas usa o acento grave como escape de caracteres especiais, em vez de delimitar toda a cadeia de caracteres do filtro.

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

Para listar somente as propriedades que lhe interessam, use o parâmetro Property dos cmdlets formatação para listar as propriedades desejadas.

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

Por fim, para encontrar apenas os nomes dos aplicativos instalados, uma simples instrução **Format\-Wide** simplifica o resultado:

```
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Embora haja várias maneiras de ver aplicativos que usaram o Windows Installer para a instalação, outros aplicativos não foram considerados. Como a maioria dos aplicativos padrão registram seu desinstalador com o Windows, podemos trabalhar com aqueles localmente, localizando-os no registro do Windows.

### Listando todos os aplicativos desinstaláveis
Embora não haja nenhuma forma garantida para localizar todos os aplicativos em um sistema, é possível encontrar todos os programas com listagens exibidas na caixa de diálogo Adicionar ou Remover Programas. Adicionar ou Remover Programas encontra esses aplicativos na seguinte chave do registro:

**HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Desinstalar**.

Podemos também examinar essa chave para encontrar aplicativos. Para facilitar ainda mais a exibição da Chave de desinstalação, podemos mapear uma unidade do Windows PowerShell neste local do registro:

```
PS>    

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> A unidade **HKLM:** é mapeada para a raiz do **HKEY\_LOCAL\_MACHINE**; portanto, usamos essa unidade no caminho para a Chave de desinstalação. Em vez do **HKLM:**, também é possível especificar o caminho do Registro usando **HKLM** ou **HKEY\_LOCAL\_MACHINE**. A vantagem de usar uma unidade do Registro existente é que podemos usar o preenchimento com Tab para preencher os nomes de chaves, não sendo necessário digitá-los.

Agora temos uma unidade chamada "Desinstalação" que pode ser usada como uma maneira rápida e conveniente de procurar as instalações de aplicativos. Podemos encontrar o número de aplicativos instalados contando o número de chaves de Registro na Desinstalação: unidade do Windows PowerShell:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

Podemos pesquisar esta lista de aplicativos ainda mais detalhadamente usando uma variedade de técnicas, começando com **Get\-ChildItem**. Para obter uma lista de aplicativos e salvá-los na variável **$UninstallableApplications**, use o seguinte comando:

```
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> Estamos usando um longo nome de variável aqui para maior clareza. Na utilização real, não há nenhum motivo para usar nomes longos. Embora você possa usar o preenchimento com Tab para nomes de variáveis, também é possível usar nomes com um ou dois caracteres para maior velocidade. Nomes mais longos e descritivos são mais úteis quando você estiver desenvolvendo código para reutilização.

Para exibir os valores das entradas do registro nas chaves do registro em Desinstalação, use o método GetValue das chaves do registro. O valor do método é o nome da entrada do registro.

Por exemplo, para localizar os nomes para exibição dos aplicativos na Chave de desinstalação, use o seguinte comando:

```
PS> Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("DisplayName") }
```

Não há nenhuma garantia de que esses valores sejam exclusivos. No exemplo a seguir, dois itens instalados aparecem como "Windows Media Encoder 9 Series":

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### Instalando aplicativos
Você pode usar a classe **Win32\_Product** para instalar os pacotes do Windows Installer, local ou remotamente.

> [!NOTE]
> Para instalar um aplicativo no Windows Vista, Windows Server 2008 e versões posteriores do Windows, você deve iniciar o Windows PowerShell com a opção "Executar como administrador".

Ao instalar remotamente, use um caminho de rede da Convenção de Nomenclatura Universal (UNC) para especificar o caminho para o pacote .msi, porque o subsistema WMI não entende caminhos do Windows PowerShell. Por exemplo, para instalar o pacote NewPackage.msi localizado no compartilhamento de rede \\\\AppServ\\dsp no computador remoto PC01, digite o seguinte comando no prompt do Windows PowerShell:

```
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq "Win32_Product"}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Aplicativos que não usam a tecnologia Windows Installer podem ter métodos específicos do aplicativo disponíveis para a implantação automatizada. Para determinar se há um método para a automação de implantação, consulte a documentação do aplicativo ou consulte o sistema de suporte do fornecedor do aplicativo. Em alguns casos, mesmo que o fornecedor do aplicativo não tenha projetado especificamente o aplicativo para a automação da instalação, o fabricante do instalador de software pode conter algumas técnicas de automação.

### Removendo aplicativos
Remover um pacote do Windows Installer usando o Windows PowerShell funciona quase da mesma forma que a instalação de um pacote. Aqui está um exemplo que seleciona o pacote para desinstalar com base em seu nome; em alguns casos pode ser mais fácil de filtrar com o **IdentifyingNumber**:

```
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

Remover outros aplicativos não é tão simples, mesmo quando feito localmente. Podemos encontrar as cadeias de caracteres de desinstalação de linha de comando para esses aplicativos por meio da extração da propriedade **UninstallString**. Esse método funciona para aplicativos do Windows Installer em programas mais antigos que aparecem sob a Chave de desinstalação:

```
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

Você pode filtrar a saída pelo nome da exibição, se desejar:

```
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -like "Win*"} | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

No entanto, essas cadeias de caracteres podem não ser diretamente utilizáveis no prompt do Windows PowerShell sem modificação.

### Atualizando aplicativos do Windows Installer
Para atualizar um aplicativo, você precisa saber o nome do aplicativo e o caminho para o pacote de atualização do aplicativo. Com essas informações, você pode atualizar um aplicativo com um único comando do Windows PowerShell:

```
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```




<!--HONumber=Jun16_HO4-->


