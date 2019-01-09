---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Instruções condicionais e loops em configurações
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400145"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Instruções condicionais e loops em configurações

Você pode fazer sua [configurações](configurations.md) mais dinâmicos usando as palavras-chave de controle de fluxo do PowerShell. Este artigo mostrará como você pode usar instruções condicionais e loops para tornar as configurações mais dinâmico. Combinando condicionais e loops com [parâmetros](add-parameters-to-a-configuration.md) e [dados de configuração](configData.md) permite que você mais flexibilidade e controle quando suas configurações de compilação.

Assim como uma função ou um bloco de Script, você pode usar qualquer linguagem do PowerShell dentro de uma configuração. As instruções que você usa serão avaliadas apenas quando você chama a sua configuração para compilar um arquivo ". MOF". Os exemplos abaixo mostram cenários simples para demonstrar conceitos. Condicionais são loops com mais frequência são usados com parâmetros e dados de configuração.

Neste exemplo simples, o **serviço** bloco de recursos recupera o estado atual de um serviço em tempo de compilação para gerar um arquivo ". MOF" que mantém seu estado atual.

> [!NOTE]
> Usar blocos de recurso dinâmicos antecipará a eficácia do Intellisense. O analisador do PowerShell não pode determinar se os valores especificados são aceitáveis, até que a configuração for compilada.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

Além disso, você poderia criar uma **Service** bloquear recursos para todos os serviços no computador atual, usando um `foreach` loop.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

Também só pode criar configurações para computadores que estão online, usando um simples `if` instrução.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> Blocos de recurso dinâmico na referência exemplos acima no computador atual. Nesse caso, o que seria a máquina que você está criando a configuração no, não o nó de destino.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Resumo

Em resumo, você pode usar qualquer linguagem do PowerShell dentro de uma configuração.

Isso inclui coisas como:

- Objetos personalizados
- Tabelas de hash
- Manipulação de cadeia de caracteres
- Comunicação remota
- WMI e CIM
- Objetos do Active Directory
- e mais...

Qualquer código do PowerShell definido em uma configuração será avaliado um tempo de compilação, mas você também pode colocar o código no script que contém sua configuração. Qualquer código fora do bloco de configuração será executado quando você importar sua configuração.

## <a name="see-also"></a>Consulte também

- [Adicionar parâmetros a uma configuração](add-parameters-to-a-configuration.md)
- [Separar dados de configuração das Configurações](configData.md)
