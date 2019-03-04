---
title: Como criar um Shell do Console | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853492"
---
# <a name="how-to-create-a-console-shell"></a>Como criar um shell do console

Windows PowerShell fornece uma ferramenta de Make-Shell, também conhecida como "make-kit", que é usado para criar um shell de console que não é extensível. Shells criados com essa nova ferramenta não podem ser estendidos mais tarde por meio de um snap-in do Windows PowerShell.

## <a name="syntax"></a>Sintaxe

Aqui está a sintaxe usada para executar Make-Shell de dentro de um arquivo de marca.

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>Parâmetros

Aqui está uma breve descrição dos parâmetros de Make-Shell.

> [!CAUTION]
> Não há suporte para caminhos UNC para assemblies pelo Make-Shell.

|Parâmetro|Descrição|
|---------------|-----------------|
|-out n.exe|Obrigatório. O nome do shell para produzir. O caminho é especificado como parte desse parâmetro.<br /><br /> Make-shell acrescentará ".exe" para esse valor se não for especificado. **Cuidado:**  Não crie um arquivo de saída com o mesmo nome que o arquivo. dll referenciada. Se você tentar isso, a ferramenta de Make-Shell cria um arquivo. cs com o mesmo nome que substituirá o arquivo. cs que tem o código-fonte cmdlet.|
|-namespace ns|Obrigatório. O namespace a ser usado para a derivada [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) classe que o kit de marca gera e compila.|
|-lib libdirectory1 [, libdirectory2,...]|Os diretórios que são pesquisados para assemblies do .NET, incluindo os assemblies do Windows PowerShell, assemblies especificados pelo `reference` parâmetro, assemblies indiretamente referenciados por outro assembly e os assemblies de sistema do .NET.|
|-reference ca1.dll[,ca2.dll,...]|Uma lista separada por vírgulas dos assemblies para incluir no shell. Esses assemblies inclui todos os cmdlet e assemblies do provedor, bem como assemblies de recurso que devem ser carregados. Se esse parâmetro não for especificado, um shell será produzido que contém somente os cmdlets e provedores principais fornecidos pelo Windows PowerShell.<br /><br /> Os assemblies podem ser especificados usando seu caminho completo; caso contrário, eles serão pesquisados para usar o caminho especificado pelo `lib` parâmetro.|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|Uma lista separada por vírgulas dos dados de formato para incluir no shell. Se esse parâmetro não for especificado, um shell será produzido que contém apenas os dados de formato fornecidos pelo Windows PowerShell.|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|Uma lista separada por vírgulas de dados de tipo para incluir no shell. Se esse parâmetro não for especificado, um shell será produzido que contém apenas os dados do tipo fornecidos pelo Windows PowerShell.|
|-source c1.cs [,c2.cs,...]|O nome de um arquivo, fornecido pelo desenvolvedor do shell, que contém qualquer código-fonte necessário para criar o shell.<br /><br /> O arquivo de código de origem pode conter o seguinte código-fonte:<br /><br /> -A implementação do Gerenciador de autorização que substitui o Gerenciador de autorização padrão. (Isso pode também ser fornecido compilado em um assembly.)<br />-Declarações de atributos informativos assembly: como AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, e AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|O tipo que contém a implementação do Gerenciador de autorização. Isso pode ser definido no código-fonte ou compilado em um assembly (especificado pelo `reference` parâmetro). Se esse parâmetro não for especificado, o Gerenciador de segurança padrão será usado. O valor deve ser o nome de tipo completo, incluindo namespaces.|
|-win32icon i.ico|O ícone para o arquivo .exe para o shell. Se não for especificado, o shell terá o ícone que o compilador c# inclui (se houver).|
|-initscript p.ps1|O perfil de inicialização para o shell. O arquivo está incluído "como-está"; Nenhuma verificação de validade é feito pelo Make-Shell.|
|-builtinscript s1.ps1[,s2.ps1,...]|Uma lista de scripts internas para o shell. Esses scripts são descobertos antes de scripts no caminho, e seu conteúdo não pode ser alterado depois que o shell é compilado.<br /><br /> Os arquivos são incluídos "como-está"; Nenhuma verificação de validade é feito pelo Make-Shell.|
|-recurso resourcefile.txt|O arquivo. txt que contém a Ajuda e a faixa de recursos para o shell. O primeiro recurso chamado ShellHelp e contém o texto exibido se o shell é invocado com o `help` parâmetro. O segundo recurso chamado ShellBanner e contém o texto e as informações de direitos autorais exibida quando o shell é iniciado no modo interativo.<br /><br /> Se esse parâmetro não for fornecido ou esses recursos não estão presentes, uma ajuda genérica e faixa são usados.|
|-cscflags cscFlags|Sinalizadores que devem ser passados para o C# compilador (csc.exe). Eles são passados inalterados. Se esse parâmetro incluir espaços, deve estar entre aspas duplas.|
|-?<br /><br /> -help|Exibe a mensagem de direitos autorais e opções de linha de comando do Shell de marca.|
|-verbose|Exibe informações detalhadas enquanto o shell está sendo criado.|

## <a name="see-also"></a>Consulte Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)