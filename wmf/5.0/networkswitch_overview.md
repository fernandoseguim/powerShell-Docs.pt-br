---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: 4868cf657f678ee43a6c92d5ee286e9ddb490964
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="0c9ec-102">Gerenciamento de comutador de rede com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c9ec-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="0c9ec-103">O cmdlet **Get-NetworkSwitchEthernetPort** agora retorna as seguintes informações adicionais com instâncias:</span><span class="sxs-lookup"><span data-stu-id="0c9ec-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="0c9ec-104">IPAddress – o endereço IP associado à porta</span><span class="sxs-lookup"><span data-stu-id="0c9ec-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="0c9ec-105">PortMode – o modo da porta: acesso, roteiro ou tronco</span><span class="sxs-lookup"><span data-stu-id="0c9ec-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="0c9ec-106">AccessVLAN – a ID da VLAN associada a essa porta no modo de acesso</span><span class="sxs-lookup"><span data-stu-id="0c9ec-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="0c9ec-107">TrunkedVLANList – uma lista de IDs de VLANs associadas a essa porta no modo de tronco</span><span class="sxs-lookup"><span data-stu-id="0c9ec-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="0c9ec-108">Gerenciamento fundamental de comutador de rede com o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c9ec-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="0c9ec-109">Os cmdlets Network Switch, introduzidos no WMF 5.0, permitem aplicar a configuração do comutador, da VLAN (LAN virtual) e a configuração básica de porta do comutador de rede da Camada 2 a comutadores de rede certificados com o logotipo do Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="0c9ec-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="0c9ec-110">A Microsoft mantém seu compromisso em dar suporte à visão da DAL (Camada de [Abstração de Datacenter](http://technet.microsoft.com/cloud/dal.aspx)) e em mostrar o valor para nossos clientes e parceiros neste espaço.</span><span class="sxs-lookup"><span data-stu-id="0c9ec-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="0c9ec-111">Com esses cmdlets, é possível executar:</span><span class="sxs-lookup"><span data-stu-id="0c9ec-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="0c9ec-112">Configuração do comutador global, como:</span><span class="sxs-lookup"><span data-stu-id="0c9ec-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="0c9ec-113">Definir nome do host</span><span class="sxs-lookup"><span data-stu-id="0c9ec-113">Set host name</span></span>
    - <span data-ttu-id="0c9ec-114">Definir faixa do comutador</span><span class="sxs-lookup"><span data-stu-id="0c9ec-114">Set switch banner</span></span>
    - <span data-ttu-id="0c9ec-115">Persistir a configuração</span><span class="sxs-lookup"><span data-stu-id="0c9ec-115">Persist configuration</span></span>
    - <span data-ttu-id="0c9ec-116">Habilitar ou desabilitar um recurso</span><span class="sxs-lookup"><span data-stu-id="0c9ec-116">Enable or disable feature</span></span>

- <span data-ttu-id="0c9ec-117">Configuração de VLAN:</span><span class="sxs-lookup"><span data-stu-id="0c9ec-117">VLAN configuration:</span></span>
    - <span data-ttu-id="0c9ec-118">Criar ou remover uma VLAN</span><span class="sxs-lookup"><span data-stu-id="0c9ec-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="0c9ec-119">Habilitar ou desabilitar uma VLAN</span><span class="sxs-lookup"><span data-stu-id="0c9ec-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="0c9ec-120">Enumerar uma VLAN</span><span class="sxs-lookup"><span data-stu-id="0c9ec-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="0c9ec-121">Definir o nome amigável de uma VLAN</span><span class="sxs-lookup"><span data-stu-id="0c9ec-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="0c9ec-122">Configuração de porta da Camada 2:</span><span class="sxs-lookup"><span data-stu-id="0c9ec-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="0c9ec-123">Enumerar portas</span><span class="sxs-lookup"><span data-stu-id="0c9ec-123">Enumerate ports</span></span>
    - <span data-ttu-id="0c9ec-124">Habilitar ou desabilitar portas</span><span class="sxs-lookup"><span data-stu-id="0c9ec-124">Enable or disable ports</span></span>
    - <span data-ttu-id="0c9ec-125">Definir modos e propriedades de porta</span><span class="sxs-lookup"><span data-stu-id="0c9ec-125">Set port modes and properties</span></span>
    - <span data-ttu-id="0c9ec-126">Adicionar ou associar a VLAN ao Tronco ou Acesso na porta</span><span class="sxs-lookup"><span data-stu-id="0c9ec-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="0c9ec-127">Comece a explorar procurando todos os cmdlets NetworkSwitch!</span><span class="sxs-lookup"><span data-stu-id="0c9ec-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

<span data-ttu-id="0c9ec-128">Mais informações estão disponíveis na postagem no blog de Jeffrey Snover sobre o comunicado da versão prévia do WMF 5.0: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="0c9ec-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>

