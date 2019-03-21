---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,serviço,instalação
title: Escrever, compilar e aplicar uma configuração
ms.openlocfilehash: c884af9d92ac375457d6eb75d815ae9a9159e273
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795412"
---
> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Escrever, compilar e aplicar uma configuração

Este exercício oferece instruções de como criar e aplicar uma configuração para a Configuração Estado Desejado (DSC) do início ao fim.
No exemplo a seguir, você aprenderá como escrever e aplicar uma configuração muito simples. A configuração garantirá que um arquivo "HelloWorld.txt" existe em seu computador local. Se você excluir o arquivo, a DSC o criará novamente em sua próxima atualização.

Para ter uma visão geral sobre o que é a DSC e como ela funciona, confira [Visão geral da Desired State Configuration para desenvolvedores](../overview/overview.md).

## <a name="requirements"></a>Requisitos

Para executar este exemplo, você precisará de um computador com o PowerShell 4.0 ou posterior.

## <a name="write-the-configuration"></a>Gravar a configuração

Uma [Configuração](configurations.md) DSC é uma função especial do PowerShell que define como você deseja configurar um ou mais computadores de destino (nós).

No ISE do PowerShell ou em outro editor do PowerShell, digite o seguinte:

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

Salve o arquivo como "HelloWorld.ps1".

Definir uma configuração é semelhante a definir uma função. O bloco **Nó** especifica o nó de destino a ser configurado, neste caso `localhost`.

A configuração chama um [recurso](../resources/resources.md), o recurso `File`. Os recursos fazem o trabalho de garantir que o nó de destino está no estado definido pela configuração.

## <a name="compile-the-configuration"></a>Compilar a configuração

Para que uma configuração DSC seja aplicada a um nó, ela deve primeiro ser compilada em um arquivo MOF.
Executar a configuração, assim como ocorre com uma função, compila um arquivo ".mof" para cada nó definido pelo bloco `Node`.
Para executar a configuração, você precisa aplicar *dot source* ao seu script de "HelloWorld.ps1" no escopo atual.
Para obter mais informações, confira [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

<!-- markdownlint-disable MD038 -->
*Aplique dot source* ao seu script de "HelloWorld.ps1" digitando o caminho em que você o armazenou, após o `. ` (ponto, espaço). Em seguida, você pode executar a configuração chamando-a como uma função.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

Isso gerará os seguintes resultados:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Aplicar a configuração

Agora que você tem o MOF compilado, é possível aplicar a configuração ao nó de destino (neste caso, o computador local) chamando o cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

O cmdlet `Start-DscConfiguration` instrui o [LCM (Gerenciador de Configurações Local)](../managing-nodes/metaConfig.md), que é o mecanismo da DSC, a aplicar a configuração.
O LCM realiza o trabalho de chamar os recursos de DSC para aplicar a configuração.

Use o código a seguir para executar o cmdlet `Start-DSCConfiguration`. Especifique o caminho do diretório em que seu "localhost.mof" está armazenado para o parâmetro `-Path`. O cmdlet `Start-DSCConfiguration` examina o diretório especificado para ver se há arquivos "\<nome de computador\>.mof". O cmdlet `Start-DSCConfiguration` tenta aplicar a cada arquivo ".mof" encontrado ao nome de computador especificado pelo nome do arquivo ("localhost", "server01", "dc-02", etc.).

> [!NOTE]
> Se o parâmetro `-Wait` não for especificado, `Start-DSCConfiguration` criará um trabalho em segundo plano para executar a operação. Especificar o parâmetro `-Verbose` permite que você inspecione a saída **Detalhada** da operação. `-Wait` e `-Verbose` são parâmetros opcionais.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Testar a configuração

Quando o cmdlet `Start-DSCConfiguration` estiver concluído, você deverá ver um arquivo "HelloWorld.txt" na localização especificada. Você pode verificar o conteúdo com o cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content).

Você também pode *testar* o status atual usando [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

A saída deverá ser "True" se o nó for estiver em conformidade com a configuração aplicada.

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>Reaplicando a configuração

Para ver sua configuração ser aplicada novamente, você pode remover o arquivo de texto criado por ela. Em seguida, use o cmdlet `Start-DSCConfiguration` com o parâmetro `-UseExisting`. O parâmetro `-UseExisting` instrui `Start-DSCConfiguration` a reaplicar o arquivo "current.mof", que representa a configuração aplicada com sucesso mais recentemente.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Próximas etapas

- Saiba mais sobre configurações de DSC em [Configurações de DSC](configurations.md).
- Veja quais recursos de DSC estão disponíveis e como criar recursos personalizados de DSC em [Recursos de DSC](../resources/resources.md).
- Localize as configurações e recursos de DSC na [Galeria do PowerShell](https://www.powershellgallery.com/).
