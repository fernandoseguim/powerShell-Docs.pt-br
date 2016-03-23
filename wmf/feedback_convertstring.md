# Convert-String
**Convert-String** expõe a funcionalidade “replace by magic”. Forneça exemplos do tipo “antes e depois” de como deseja que o texto se assemelhe, e **Convert-String** formatará o texto automaticamente. Aqui está uma demonstração: usar o nome e sobrenome de alguém e substituí-lo pelo sobrenome, uma vírgula, a primeira inicial do sobrenome e um ponto. Experimente com um regex e veja quanto tempo isso leva.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
<!--HONumber=Mar16_HO2-->
