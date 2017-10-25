---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Trabalhando com impressoras
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: c8b4d728c9fddd39e1aeb56d6f9b8ffffe4c7292
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-printers"></a><span data-ttu-id="2aba1-103">Trabalhando com impressoras</span><span class="sxs-lookup"><span data-stu-id="2aba1-103">Working with Printers</span></span>
<span data-ttu-id="2aba1-104">Você pode usar o Windows PowerShell para gerenciar impressoras usando o WMI e o objeto COM WScript.Network do WSH.</span><span class="sxs-lookup"><span data-stu-id="2aba1-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="2aba1-105">Usaremos uma combinação das duas ferramentas para demonstrar as tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="2aba1-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="2aba1-106">Listar conexões de impressora</span><span class="sxs-lookup"><span data-stu-id="2aba1-106">Listing Printer Connections</span></span>
<span data-ttu-id="2aba1-107">A maneira mais simples de listar as impressoras instaladas em um computador é usar o a classe do WMI **Win32_Printer**:</span><span class="sxs-lookup"><span data-stu-id="2aba1-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="2aba1-108">Você também pode listar as impressoras usando o objeto COM **WScript.Network** que normalmente é usado nos scripts do WSH:</span><span class="sxs-lookup"><span data-stu-id="2aba1-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="2aba1-109">Como esse comando retorna uma coleção simples de cadeia de caracteres de nomes de portas e nomes de dispositivo de impressora sem qualquer distinção rótulos, por isso não é fácil interpretar.</span><span class="sxs-lookup"><span data-stu-id="2aba1-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="2aba1-110">Adicionar uma impressora de rede</span><span class="sxs-lookup"><span data-stu-id="2aba1-110">Adding a Network Printer</span></span>
<span data-ttu-id="2aba1-111">Para adicionar uma nova impressora de rede, use **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="2aba1-111">To add a new network printer, use **WScript.Network**:</span></span>

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="2aba1-112">Configurar uma impressora padrão</span><span class="sxs-lookup"><span data-stu-id="2aba1-112">Setting a Default Printer</span></span>
<span data-ttu-id="2aba1-113">Para usar o WMI para definir a impressora padrão, localize a impressora na coleção **Win32_Printer** e, em seguida, invoque o método **SetDefaultPrinter**:</span><span class="sxs-lookup"><span data-stu-id="2aba1-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="2aba1-114">**WScript.Network** é um pouco mais simples de usar, pois ele tem um método **SetDefaultPrinter** que usa apenas o nome da impressora como um argumento:</span><span class="sxs-lookup"><span data-stu-id="2aba1-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="2aba1-115">Remover a conexão da impressora</span><span class="sxs-lookup"><span data-stu-id="2aba1-115">Removing a Printer Connection</span></span>
<span data-ttu-id="2aba1-116">Para remover uma conexão de impressora, use o método **WScript.Network RemovePrinterConnection**:</span><span class="sxs-lookup"><span data-stu-id="2aba1-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```

