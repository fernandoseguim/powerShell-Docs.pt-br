---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: relatando no JEA
ms.technology: powershell
ms.openlocfilehash: 3e7bd2755281f491bba8a905df018fb2e1cac6ff
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: pt-BR
---
# <a name="reporting-on-jea"></a><span data-ttu-id="5d0da-103">Relatando no JEA</span><span class="sxs-lookup"><span data-stu-id="5d0da-103">Reporting on JEA</span></span>
<span data-ttu-id="5d0da-104">Como JEA permite que usuários sem privilégios executem em um contexto privilegiado, registro em log e auditoria são extremamente importantes.</span><span class="sxs-lookup"><span data-stu-id="5d0da-104">Because JEA allows non-privileged users to run in a privileged context, logging and auditing are extremely important.</span></span>
<span data-ttu-id="5d0da-105">Nesta seção, vamos percorrer as ferramentas que você pode usar para ajudá-lo com o log e relatórios.</span><span class="sxs-lookup"><span data-stu-id="5d0da-105">In this section, we'll run through the tools you can use to help you with logging and reporting.</span></span>

## <a name="reporting-on-jea-actions"></a><span data-ttu-id="5d0da-106">Relatar ações do JEA</span><span class="sxs-lookup"><span data-stu-id="5d0da-106">Reporting on JEA Actions</span></span>
### <a name="over-the-shoulder-transcription"></a><span data-ttu-id="5d0da-107">Transcrição Over The Shoulder</span><span class="sxs-lookup"><span data-stu-id="5d0da-107">Over-the-Shoulder Transcription</span></span>
<span data-ttu-id="5d0da-108">Uma das maneiras mais rápidas de obter um resumo do que está acontecendo em uma sessão do PowerShell é realizar Over the Shoulder da pessoa que está digitando.</span><span class="sxs-lookup"><span data-stu-id="5d0da-108">One of the quickest ways to get a summary of what's happening in a PowerShell session is to look over the shoulder of the person typing.</span></span>
<span data-ttu-id="5d0da-109">Você pode ver os comandos, a saída desses comandos e se tudo está bem.</span><span class="sxs-lookup"><span data-stu-id="5d0da-109">You see their commands, the output of those commands, and all is well.</span></span>
<span data-ttu-id="5d0da-110">Ou não, mas pelo menos você saberá.</span><span class="sxs-lookup"><span data-stu-id="5d0da-110">Or it's not, but at least you'll know.</span></span>
<span data-ttu-id="5d0da-111">A transcrição do PowerShell foi projetada para dar a você uma exibição semelhante após o fato.</span><span class="sxs-lookup"><span data-stu-id="5d0da-111">PowerShell transcription is designed to give you a similar view after the fact.</span></span>

<span data-ttu-id="5d0da-112">Ao usar o campo "TranscriptDirectory" em sua configuração de sessão, o PowerShell gravará automaticamente uma transcrição de todas as ações executadas em uma determinada sessão.</span><span class="sxs-lookup"><span data-stu-id="5d0da-112">When using the "TranscriptDirectory" field in your Session Configuration, PowerShell will automatically record a transcript of all actions taken in a given session.</span></span>
<span data-ttu-id="5d0da-113">Você pode encontrar transcrições de suas sessões aqui neste documento: "$env: ProgramData\JEAConfiguration\Transcripts"</span><span class="sxs-lookup"><span data-stu-id="5d0da-113">You can find transcripts from your sessions in this document here: "$env:ProgramData\JEAConfiguration\Transcripts"</span></span>

<span data-ttu-id="5d0da-114">Como você pode ver, a transcrição registra informações sobre o usuário "Conectado", o usuário "Executar como", os comandos executados na sessão e muito mais.</span><span class="sxs-lookup"><span data-stu-id="5d0da-114">As you can tell, the transcript records information about the "Connected" user, the "Run As" user, the commands run in the session, and more.</span></span>
<span data-ttu-id="5d0da-115">Para obter mais informações sobre transcrições do PowerShell, confira este [post de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span><span class="sxs-lookup"><span data-stu-id="5d0da-115">For more information about PowerShell transcription, check out [this blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>

### <a name="powershell-event-logs"></a><span data-ttu-id="5d0da-116">Logs de Eventos do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d0da-116">PowerShell Event Logs</span></span>
<span data-ttu-id="5d0da-117">Após ativar o registro em log no módulo, todas as ações do PowerShell também são registradas nos logs de Eventos do Windows regulares.</span><span class="sxs-lookup"><span data-stu-id="5d0da-117">When you have module logging turned on, all PowerShell actions are also recorded in regular Windows Event logs.</span></span>
<span data-ttu-id="5d0da-118">Isso é um pouco mais complicado de lidar quando comparado às transcrições, mas o nível de detalhes fornecido pode ser útil.</span><span class="sxs-lookup"><span data-stu-id="5d0da-118">This is slightly messier to deal with when compared to transcripts, but the level of detail it gives you can be useful.</span></span>

<span data-ttu-id="5d0da-119">No log operacional do "PowerShell", a ID de Evento 4104 registrará cada comando invocado se você tiver habilitado o registro em log do módulo.</span><span class="sxs-lookup"><span data-stu-id="5d0da-119">In the "PowerShell" operational log, Event ID 4104 will record each command invoked if you have enabled module logging.</span></span>

### <a name="other-event-logs"></a><span data-ttu-id="5d0da-120">Outros logs de evento</span><span class="sxs-lookup"><span data-stu-id="5d0da-120">Other Event Logs</span></span>
<span data-ttu-id="5d0da-121">Diferentemente dos logs do PowerShell e transcrições, outros mecanismos de registro em log não capturarão o "Usuário Conectado".</span><span class="sxs-lookup"><span data-stu-id="5d0da-121">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the "Connected User".</span></span>
<span data-ttu-id="5d0da-122">Você precisará fazer alguma correlação entre outros logs e os do PowerShell para corresponder as ações tomadas.</span><span class="sxs-lookup"><span data-stu-id="5d0da-122">You will need to do some correlation between other logs and PowerShell logs to match up actions taken.</span></span>

<span data-ttu-id="5d0da-123">No log operacional do "Gerenciamento Remoto do Windows", a ID de Evento 193 registrará a SID do Usuário que se conecta e o Nome, bem como a SID da Conta Virtual RunAs auxiliar nessa correlação.</span><span class="sxs-lookup"><span data-stu-id="5d0da-123">In the "Windows Remote Management" operational log, Event ID 193 will record the Connecting User's SID and Name, as well as the RunAs Virtual Account's SID to assist with this correlation.</span></span>
<span data-ttu-id="5d0da-124">Você também pode ter observado que o nome da Conta Virtual RunAs inclui o domínio e nome de usuário do usuário conectado ao final.</span><span class="sxs-lookup"><span data-stu-id="5d0da-124">You may have also noticed that the name of the RunAs Virtual Account includes the connecting user's domain and username at the end.</span></span>

## <a name="reporting-on-jea-configuration"></a><span data-ttu-id="5d0da-125">Relatórios sobre a configuração de JEA</span><span class="sxs-lookup"><span data-stu-id="5d0da-125">Reporting on JEA Configuration</span></span>
### <a name="get-pssessionconfiguration"></a><span data-ttu-id="5d0da-126">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5d0da-126">Get-PSSessionConfiguration</span></span>
<span data-ttu-id="5d0da-127">Para relatar com precisão o estado do seu ambiente, é importante saber quantos pontos de extremidade JEA você tem configurados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="5d0da-127">In order to accurately report on the state of your environment, it's important to know how many JEA endpoints you have set up on your machine.</span></span>
<span data-ttu-id="5d0da-128">`Get-PSSessionConfiguration` faz exatamente isso.</span><span class="sxs-lookup"><span data-stu-id="5d0da-128">`Get-PSSessionConfiguration` does just that.</span></span>

### <a name="get-pssessioncapability"></a><span data-ttu-id="5d0da-129">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="5d0da-129">Get-PSSessionCapability</span></span>
<span data-ttu-id="5d0da-130">Relatar manualmente as capacidade de um dado usuário por meio de um ponto de extremidade JEA pode ser bastante complexo.</span><span class="sxs-lookup"><span data-stu-id="5d0da-130">Manually reporting on the capabilities of any given user through a JEA endpoint can be quite complex.</span></span>
<span data-ttu-id="5d0da-131">Potencialmente, você pode precisaria verificar várias capacidades de função.</span><span class="sxs-lookup"><span data-stu-id="5d0da-131">You would potentially need to inspect several role capabilities.</span></span>
<span data-ttu-id="5d0da-132">Felizmente, o cmdlet "Get-PSSessionCapability" faz isso.</span><span class="sxs-lookup"><span data-stu-id="5d0da-132">Fortunately, the "Get-PSSessionCapability" cmdlet does this.</span></span>

<span data-ttu-id="5d0da-133">Para testar isso, execute o seguinte comando do prompt do administrador do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5d0da-133">To test this out, run the following command from an administrator PowerShell prompt:</span></span>
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```

