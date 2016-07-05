# Recursos DSC baseados em classe

## Definindo recursos DSC com classes

Com base nos comentários, tornamos a criação de recursos DSC baseados em classe mais simples e mais fácil de entender. As principais diferenças entre um recurso DSC baseado em classe e um provedor de recursos DSC de cmdlet são:

* Um arquivo MOF para o esquema não é necessário.
* Uma subpasta **DSCResource** na pasta do módulo não é necessária.
* Um arquivo de módulo do PowerShell pode conter várias classes de recursos DSC.

Para obter mais informações, veja [Writing a custom DSC resource with PowerShell classes](../dsc/authoringResourceClass.md) (Escrevendo um recurso de DSC personalizado com classes do PowerShell).


<!--HONumber=Jun16_HO4-->


