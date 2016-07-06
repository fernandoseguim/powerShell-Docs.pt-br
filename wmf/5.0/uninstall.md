# Instruções de desinstalação

## Usando o Prompt de Comando
1.  Abra o **Prompt de Comando.**
2.  Execute o [Inicializador Autônomo do Windows Update](https://support.microsoft.com/en-us/kb/934307), conforme mostrado abaixo:

No Windows Server 2012 R2 e Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
No Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
No Windows Server 2008 R2 SP1 e Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

## Usando o Painel de Controle
1.  Abra o **Painel de Controle.**
2.  Abra **Programas** e, em seguida, **Desinstalar um programa.**
3.  Clique em **Exibir atualizações instaladas.**
4.  Selecione **Windows Management Framework 5.0** na lista de atualizações instaladas. Isso corresponde à *KB3134758*, *KB3134759* ou *KB3134760*. Clique em **Desinstalar.**


<!--HONumber=Jun16_HO4-->


