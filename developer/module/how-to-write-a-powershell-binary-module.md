---
title: Como escrever um módulo do PowerShell binário | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856482"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Como escrever um módulo binário do Windows PowerShell

Um módulo binário pode ser qualquer assembly (. dll) que contém as classes de cmdlet. Por padrão, todos os cmdlets no assembly são importados quando o módulo binário é importado. No entanto, você pode restringir os cmdlets que são importados com a criação de um manifesto de módulo cuja raiz é o assembly. (Por exemplo, a chave de CmdletsToExport do manifesto pode ser usada para exportar apenas os cmdlets que são necessários.) Além disso, um módulo binário pode conter arquivos adicionais, uma estrutura de diretório e outras partes de informação de gerenciamento bastante úteis que um único cmdlet não pode.

O procedimento a seguir descreve como criar e instalar um módulo binário do PowerShell.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Como criar e instalar um módulo binário do PowerShell

1. Criar uma solução binária do PowerShell (como um cmdlet escrito em C#), com os recursos de que necessita e certifique-se de que ele seja executado corretamente.

   De uma perspectiva de código, o núcleo de um módulo binário é simplesmente um conjunto de módulos do cmdlet. Na verdade, o PowerShell tratará um assembly único cmdlet como um módulo, em termos de carregamento e descarregamento, sem esforço adicional por parte do desenvolvedor. Para obter mais informações sobre como escrever um cmdlet, consulte [escrevendo um Cmdlet do Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Se necessário, crie o restante de sua solução: (cmdlets adicionais, arquivos XML e assim por diante) e descrevê-los com um manifesto de módulo.

   Além de descrever os assemblies de cmdlet em sua solução, um manifesto de módulo pode descrever como você deseja que seu módulo exportados e importados, quais cmdlets serão expostas e o que irá arquivos adicionais no módulo. Conforme mencionado anteriormente no entanto, o PowerShell pode tratar um cmdlet binário como um módulo sem esforço adicional. Como tal, um manifesto de módulo é útil principalmente para combinar vários arquivos em um único pacote, ou para controlar explicitamente a publicação para um determinado assembly. Para obter mais informações, consulte [como escrever um manifesto de módulo do PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).

   O código a seguir é extremamente simples C# bloco de código que contém três cmdlets no mesmo arquivo que pode ser usado como um módulo.

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. Empacotar sua solução e salvar o pacote em algum lugar no caminho do módulo do PowerShell.

   O `PSModulePath` variável de ambiente global descreve os caminhos padrão que o PowerShell usará para localizar seu módulo. Por exemplo, um caminho comum para salvar um módulo em um sistema seria `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Se você não usar os caminhos padrão, você precisará declarar explicitamente o local do seu módulo durante a instalação. Certifique-se de criar uma pasta para salvar o módulo, pois você talvez tenha a pasta para armazenar vários assemblies e arquivos para sua solução.

   Observe que tecnicamente você não precisa instalar o módulo em qualquer lugar no `PSModulePath` -esses são simplesmente os locais padrão que irá procurar o módulo PowerShell. No entanto, ele é considerado uma prática recomendada para fazer isso, a menos que você tenha uma boa razão para armazenar seu módulo em outro lugar. Para obter mais informações, consulte [instalando um módulo do PowerShell](./installing-a-powershell-module.md) e [modificando o caminho de instalação do módulo do PowerShell](./modifying-the-psmodulepath-installation-path.md).

4. Importar o módulo do PowerShell com uma chamada para [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   Chamada para [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) carregará seu módulo na memória ativa. Se você estiver usando o PowerShell 3.0 e posterior, basta chamar o nome do seu módulo de código também serão importados Para obter mais informações, consulte [importação de um módulo do PowerShell](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importando Assemblies Snap-in como módulos

Cmdlets e provedores que existem no snap-in de assemblies carregados como módulos binários. Quando os snap-in de assemblies são carregados como módulos binários, os cmdlets e provedores do snap-in estão disponíveis para o usuário, mas a classe de snap-in no assembly será ignorada e o snap-in não está registrado. Como resultado, os cmdlets do snap-in fornecidos pelo Windows PowerShell não pode detectar o snap-in, mesmo que os cmdlets e provedores estão disponíveis para a sessão.

Além disso, qualquer formatação ou tipos de arquivos que são referenciados pelo snap-in não podem ser importados como parte de um módulo binário. Para importar os arquivos de formatação e tipos, você deve criar um manifesto de módulo. Consulte, [como escrever um manifesto de módulo do PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).

## <a name="see-also"></a>Consulte Também

[Escrevendo um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
