---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Início Rápido de Configuração de Estado Desejado"
ms.openlocfilehash: 295a78f3fd85464239d51d7be0defa04d2344689
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2017
---
> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="desired-state-configuration-quick-start"></a>Início Rápido de Configuração de Estado Desejado

Este exercício oferece instruções de como criar e aplicar uma configuração para a Configuração Estado Desejado (DSC) do início ao fim.
O exemplo que usaremos garante que o recurso `Web-Server` (IIS) do servidor esteja habilitado e que o conteúdo para um site "Hello World" simples esteja presente no diretório do `intepub\wwwroot` desse servidor.

Para obter uma visão geral sobre o que é a DSC e como ela funciona, confira [Visão Geral da Configuração do Estado Desejado para Tomadores de Decisão](decisionMaker.md).

## <a name="requirements"></a>Requisitos

Para executar este exemplo, você precisará de um computador com o Windows Server 2012 ou posterior e o PowerShell 4.0 ou posterior.

## <a name="write-and-place-the-indexhtm-file"></a>Gravar e posicionar o arquivo index.htm

Primeiro, vamos criar o arquivo HTML que usaremos como o conteúdo do site.

Na pasta-raiz, crie uma pasta chamada `test`.

Em um editor de texto, digite o texto a seguir:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Salve-o como `index.htm` na pasta `test` que você criou anteriormente. 

## <a name="write-the-configuration"></a>Gravar a configuração

Uma [Configuração DSC](configurations.md) é uma função especial do PowerShell que define como você deseja configurar um ou mais computadores de destino (nós).

No ISE do PowerShell, digite o seguinte:

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

Salve o arquivo como `WebsiteTest.ps1`.

Você pode ver que ele parece uma função do PowerShell, com a adição da palavra-chave **Configuração** usada antes do nome da função.

O bloco **Nó** especifica o nó de destino a ser configurado, neste caso `localhost`.

A configuração chama dois [recursos](resources.md), [WindowsFeature](windowsFeatureResource.md) e [Arquivo](fileResource.md).
Os recursos fazem o trabalho de garantir que o nó de destino está no estado definido pela configuração.

## <a name="compile-the-configuration"></a>Compilar a configuração

Para que uma configuração DSC seja aplicada a um nó, ela deve primeiro ser compilada em um arquivo MOF.
Para fazer isso, você deve executar a configuração como uma função.
Em um console do PowerShell, navegue até a mesma pasta em que você salvou sua configuração e execute os seguintes comandos para compilar a configuração em um arquivo MOF:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Isso gerará os seguintes resultados:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

A primeira linha torna a função de configuração disponível no console.
A segunda linha executa a configuração.
O resultado é que uma nova pasta, chamada `WebsiteTest`, é criada como uma subpasta da pasta atual.
A pasta `WebsiteTest` contém um arquivo chamado `localhost.mof`.
É o arquivo que pode ser aplicado ao nó de destino.

## <a name="apply-the-configuration"></a>Aplicar a configuração

Agora que você tem o MOF compilado, é possível aplicar a configuração ao nó de destino (neste caso, o computador local) chamando o cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration).

O cmdlet `Start-DscConfiguration` indica ao [Gerenciador de Configurações Local (LCM)](metaConfig.md), qual é o mecanismo de DSC a aplicar à configuração.
O LCM realiza o trabalho de chamar os recursos de DSC para aplicar a configuração.

Em um console do PowerShell, navegue até a mesma pasta em que você salvou sua configuração e execute o mesmo comando:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Testar a configuração

Você pode chamar o cmdlet [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) para ver se a configuração foi bem-sucedida. 

Você também pode testar os resultados diretamente, neste caso, pesquisando o `http://localhost/` em um navegador da Web.
Você deve ver a página de HTML "Hello World" que criou como a primeira etapa deste exemplo.

## <a name="next-steps"></a>Próximas etapas

- Saiba mais sobre configurações de DSC em [Configurações de DSC](configurations.md).
- Veja quais recursos de DSC estão disponíveis e como criar recursos personalizados de DSC em [Recursos de DSC](resources.md).
- Localize as configurações e recursos de DSC na [Galeria do PowerShell](https://www.powershellgallery.com/).



