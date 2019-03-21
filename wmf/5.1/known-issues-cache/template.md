---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.topic: conceptual
title: exemplo de modelo de um problema conhecido ou writeup de limitação
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794478"
---
 >Observação: dê um título descritivo proposto e uma breve descrição

## <a name="example-erroneous-executionpolicy-errors"></a>Exemplo: erros de ExecutionPolicy incorreta
No Windows 7, o uso de módulos PowerShell e recursos DSC pode fazer com que erros sobre ExecutionPolicy sejam relatados.

### <a name="resolution"></a>Resolução

Para resolver, defina **ExecutionPolicy** como **RemoteSigned** executando o seguinte comando em uma sessão do PowerShell com privilégios elevados (Executar como Administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```
