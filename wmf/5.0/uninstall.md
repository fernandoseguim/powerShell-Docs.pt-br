---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="426a0-102">Instruções de desinstalação</span><span class="sxs-lookup"><span data-stu-id="426a0-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="426a0-103">Usando o Prompt de Comando</span><span class="sxs-lookup"><span data-stu-id="426a0-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="426a0-104">Abra o **Prompt de Comando.**</span><span class="sxs-lookup"><span data-stu-id="426a0-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="426a0-105">Execute o [Inicializador Autônomo do Windows Update](https://support.microsoft.com/en-us/kb/934307), conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="426a0-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="426a0-106">No Windows Server 2012 R2 e Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="426a0-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="426a0-107">No Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="426a0-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="426a0-108">No Windows Server 2008 R2 SP1 e Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="426a0-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="426a0-109">Usando o Painel de Controle</span><span class="sxs-lookup"><span data-stu-id="426a0-109">Using Control Panel</span></span>
1.  <span data-ttu-id="426a0-110">Abra o **Painel de Controle.**</span><span class="sxs-lookup"><span data-stu-id="426a0-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="426a0-111">Abra **Programas** e, em seguida, **Desinstalar um programa.**</span><span class="sxs-lookup"><span data-stu-id="426a0-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="426a0-112">Clique em **Exibir atualizações instaladas.**</span><span class="sxs-lookup"><span data-stu-id="426a0-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="426a0-113">Selecione **Windows Management Framework 5.0** na lista de atualizações instaladas.</span><span class="sxs-lookup"><span data-stu-id="426a0-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="426a0-114">Isso corresponde à *KB3134758*, *KB3134759* ou *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="426a0-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="426a0-115">Clique em **Desinstalar.**</span><span class="sxs-lookup"><span data-stu-id="426a0-115">Click **Uninstall.**</span></span>
