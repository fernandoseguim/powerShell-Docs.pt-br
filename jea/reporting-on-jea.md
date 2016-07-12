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
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: d867a6462e9fa8b6e16c8c2103899c72b380116c

---

# Relatando no JEA
Como JEA permite que usuários sem privilégios executem em um contexto privilegiado, registro em log e auditoria são extremamente importantes.
Nesta seção, vamos percorrer as ferramentas que você pode usar para ajudá-lo com o log e relatórios.

## Relatar ações do JEA
### Transcrição Over The Shoulder
Uma das maneiras mais rápidas de obter um resumo do que está acontecendo em uma sessão do PowerShell é realizar Over the Shoulder da pessoa que está digitando.
Você pode ver os comandos, a saída desses comandos e se tudo está bem.
Ou não, mas pelo menos você saberá.
A transcrição do PowerShell foi projetada para dar a você uma exibição semelhante após o fato.

Ao usar o campo "TranscriptDirectory" em sua configuração de sessão, o PowerShell gravará automaticamente uma transcrição de todas as ações executadas em uma determinada sessão.
Você pode encontrar transcrições de suas sessões aqui neste documento: "$env: ProgramData\JEAConfiguration\Transcripts"

Como você pode ver, a transcrição registra informações sobre o usuário "Conectado", o usuário "Executar como", os comandos executados na sessão e muito mais.
Para obter mais informações sobre transcrições do PowerShell, confira este [post de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).

### Logs de Eventos do PowerShell
Após ativar o registro em log no módulo, todas as ações do PowerShell também são registradas nos logs de Eventos do Windows regulares.
Isso é um pouco mais complicado de lidar quando comparado às transcrições, mas o nível de detalhes fornecido pode ser útil.

No log operacional do "PowerShell", a ID de Evento 4104 registrará cada comando invocado se você tiver habilitado o registro em log do módulo.

### Outros logs de evento
Diferentemente dos logs do PowerShell e transcrições, outros mecanismos de registro em log não capturarão o "Usuário Conectado".
Você precisará fazer alguma correlação entre outros logs e os do PowerShell para corresponder as ações tomadas.

No log operacional do "Gerenciamento Remoto do Windows", a ID de Evento 193 registrará a SID do Usuário que se conecta e o Nome, bem como a SID da Conta Virtual RunAs auxiliar nessa correlação.
Você também pode ter observado que o nome da Conta Virtual RunAs inclui o domínio e nome de usuário do usuário conectado ao final.

## Relatórios sobre a configuração de JEA
### Get-PSSessionConfiguration
Para relatar com precisão o estado do seu ambiente, é importante saber quantos pontos de extremidade JEA você tem configurados em seu computador.
`Get-PSSessionConfiguration` faz exatamente isso.

### Get-PSSessionCapability
Relatar manualmente as capacidade de um dado usuário por meio de um ponto de extremidade JEA pode ser bastante complexo.
Potencialmente, você pode precisaria verificar várias capacidades de função.
Felizmente, o cmdlet "Get-PSSessionCapability" faz isso.

Para testar isso, execute o seguinte comando do prompt do administrador do PowerShell:
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```




<!--HONumber=Jul16_HO1-->


