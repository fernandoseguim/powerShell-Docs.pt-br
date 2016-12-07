# <a name="class-based-dsc-resources"></a>Recursos DSC baseados em classe

## <a name="defining-dsc-resources-with-classes"></a>Definindo recursos DSC com classes

Com base nos comentários, tornamos a criação de recursos DSC baseados em classe mais simples e mais fácil de entender. As principais diferenças entre um recurso DSC baseado em classe e um provedor de recursos DSC de cmdlet são:

* Um arquivo MOF para o esquema não é necessário.
* Uma subpasta **DSCResource** na pasta do módulo não é necessária.
* Um arquivo de módulo do PowerShell pode conter várias classes de recursos DSC.

Para obter mais informações, veja [Escrevendo um recurso personalizado de DSC com classes do PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).
