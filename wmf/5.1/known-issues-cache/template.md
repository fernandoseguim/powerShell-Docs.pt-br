---
title: "exemplo de modelo de um problema conhecido ou writeup de limitação"
contributor: 
ms.openlocfilehash: e3b98044902cb6665e06582c8259bd5defd6f2ca
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
>Observação: dê um título descritivo proposto e uma breve descrição

## <a name="example-erroneous-executionpolicy-errors"></a>Exemplo: erros de ExecutionPolicy incorreta ##
No Windows 7, o uso de módulos PowerShell e recursos DSC pode fazer com que erros sobre ExecutionPolicy sejam relatados.

### <a name="resolution"></a>Resolução

Para resolver, defina **ExecutionPolicy** como **RemoteSigned** executando o seguinte comando em uma sessão do PowerShell com privilégios elevados (Executar como Administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```
