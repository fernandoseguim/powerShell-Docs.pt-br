---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, serviço, a instalação
title: Escrever, compilar e aplicar uma configuração
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675605"
---
> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Escrever, compilar e aplicar uma configuração

Este exercício oferece instruções de como criar e aplicar uma configuração para a Configuração Estado Desejado (DSC) do início ao fim.
O exemplo a seguir, você aprenderá como escrever e aplicar uma configuração muito simple. A configuração garantirá que existe um arquivo de "HelloWorld.txt" em seu computador local. Se você excluir o arquivo, DSC irá recriá-lo na próxima vez que ele atualiza.

Para uma visão geral do DSC What ' s e como ele funciona, consulte [Desired State Configuration visão geral para desenvolvedores](../overview/overview.md).

## <a name="requirements"></a>Requisitos

Para executar este exemplo, você precisará de um computador que executa o PowerShell 4.0 ou posterior.

## <a name="write-the-configuration"></a>Gravar a configuração

Uma [Configuração](configurations.md) DSC é uma função especial do PowerShell que define como você deseja configurar um ou mais computadores de destino (nós).

No ISE do PowerShell, ou outro editor do PowerShell, digite o seguinte:

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

Definir uma configuração é como a definição de uma função. O bloco **Nó** especifica o nó de destino a ser configurado, neste caso `localhost`.

A configuração chama um [recursos](../resources/resources.md), o `File` recursos. Os recursos fazem o trabalho de garantir que o nó de destino está no estado definido pela configuração.

## <a name="compile-the-configuration"></a>Compilar a configuração

Para que uma configuração DSC seja aplicada a um nó, ela deve primeiro ser compilada em um arquivo MOF.
Executando a configuração, como uma função, compilar um arquivo ". MOF" para cada nó definido pelo `Node` bloco.
Para executar a configuração, você precisa *origem dot* seu script de "HelloWorld.ps1" no escopo atual.
Para obter mais informações, consulte [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

*Origem de ponto* seu script de "HelloWorld.ps1" digitando o caminho onde você armazenou, após o `. ` (ponto, espaço). Você pode em seguida, execute a configuração chamando-o como uma função.

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

O `Start-DscConfiguration` cmdlet informa o [Gerenciador de configurações Local (LCM)](../managing-nodes/metaConfig.md), o mecanismo de DSC para aplicar a configuração.
O LCM realiza o trabalho de chamar os recursos de DSC para aplicar a configuração.

Use o código a seguir para executar o `Start-DSCConfiguration` cmdlet. Especifique o caminho de diretório em que "localhost.mof" é armazenado para o `-Path` parâmetro. O `Start-DSCConfiguration` cmdlet examinará o diretório especificado para qualquer "\<computername\>. MOF" arquivos. O `Start-DSCConfiguration` cmdlet tenta aplicar a cada arquivo ". MOF" encontrado para o nome do computador especificado pelo nome do arquivo ("localhost", "server01", "controlador de domínio-02", etc.).

> [!NOTE]
> Se o `-Wait` parâmetro não for especificado, `Start-DSCConfiguration` cria um trabalho em segundo plano para executar a operação. Especificando o `-Verbose` parâmetro permite que você assista a **detalhado** saída da operação. `-Wait`, e `-Verbose` são ambos os parâmetros opcionais.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Testar a configuração

Uma vez o `Start-DSCConfiguration` cmdlet estiver concluída, você deverá ver um arquivo de "HelloWorld.txt" no local especificado por você. Você pode verificar o conteúdo com o [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.

Você também pode *testar* o status atual usando [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

A saída deve ser "True" se o nó é atualmente compatível com a configuração aplicada.

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

## <a name="re-applying-the-configuration"></a>Novamente, aplicando a configuração

Para ver sua configuração serão aplicadas novamente, você pode remover o arquivo de texto criado por sua configuração. O uso de `Start-DSCConfiguration` cmdlet com o `-UseExisting` parâmetro. O `-UseExisting` parâmetro instrui `Start-DSCConfiguration` para reaplicar o arquivo "Current", que representa mais recentemente com êxito aplicado configuração.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Próximas etapas

- Saiba mais sobre configurações de DSC em [Configurações de DSC](configurations.md).
- Veja quais recursos de DSC estão disponíveis e como criar recursos personalizados de DSC em [Recursos de DSC](../resources/resources.md).
- Localize as configurações e recursos de DSC na [Galeria do PowerShell](https://www.powershellgallery.com/).
