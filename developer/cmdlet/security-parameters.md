---
title: Parâmetros de segurança | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: c8b3f907a80d1f6125a5ac04236245503db76ed0
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251295"
---
# <a name="security-parameters"></a>Parâmetros de segurança

A tabela a seguir lista os nomes recomendados e a funcionalidade para os parâmetros usados para fornecer informações de segurança para uma operação, como parâmetros que especificam informações de privilégio e a chave do certificado.

|Parâmetro|Funcionalidade|
|---|---|
|**ACL**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para especificar o nível de controle de acesso de proteção para um catálogo ou para um identificador de recurso uniforme (URI).|
|**CertFile**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o nome de um arquivo que contém um dos seguintes:<br>-Um certificado x. 509 codificado em Base64 ou distinto codificação DER (regras)<br>-Um arquivo de chaves públicas Cryptography Standards (PKCS) #12 que contém pelo menos um certificado e chave|
|**CertIssuerName**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o nome do emissor de um certificado ou para que o usuário pode especificar uma subcadeia de caracteres.|
|**CertRequestFile**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para especificar o nome de um arquivo que contém uma solicitação de certificado PKCS #10 codificado por DER ou Base64.|
|**CertSerialNumber**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para especificar o número de série que foi emitido pela autoridade de certificação.|
|**CertStoreLocation**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o local do repositório de certificados. Normalmente, o local é um caminho de arquivo.|
|**CertSubjectName**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o emissor de um certificado ou para que o usuário pode especificar uma subcadeia de caracteres.|
|**CertUsage**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para especificar o uso da chave ou o uso avançado de chave. A chave pode ser representada como um pouco de máscara, um pouco, um identificador de objeto (OID), ou uma cadeia de caracteres.|
|**Credential**<br>Tipo de dados: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|Implemente esse parâmetro para que o cmdlet automaticamente solicitará ao usuário um nome de usuário ou senha. Um prompt para ambos é exibido se uma credencial completa não é fornecida diretamente.|
|**CSPName**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o nome do provedor de serviços de certificado (CSP).|
|**CSPType**<br>Tipo de dados: Inteiro|Implemente esse parâmetro para que o usuário pode especificar o tipo de CSP.|
|**Grupo**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar uma coleção de entidades de segurança para acesso. Para obter mais informações, consulte a descrição do **Principal** parâmetro.|
|**KeyAlgorithm**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o algoritmo de geração de chave a ser usado para segurança.|
|**KeyContainerName**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o nome do contêiner de chave.|
|**KeyLength**<br>Tipo de dados: Inteiro|Implemente esse parâmetro para que o usuário pode especificar o comprimento da chave em bits.|
|**operação**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar uma ação que pode ser executada em um objeto protegido.|
|**Entidade de segurança**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar uma entidade de identificação exclusiva para o acesso.|
|**privilégio**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o direito de que um cmdlet precisa executar uma operação de uma entidade específica.|
|**Privilégios**<br>Tipo de dados: Matriz de privilégios|Implemente esse parâmetro para que o usuário pode especificar os direitos de que precisa de um cmdlet para executar sua operação de uma entrada específica.|
|**Função**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um conjunto de operações que podem ser executadas por uma entidade.|
|**SaveCred**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que as credenciais que foram salvos anteriormente pelo usuário serão usadas quando o parâmetro for especificado.|
|**Escopo**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o grupo de objetos protegidos para o cmdlet.|
|**SID**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um identificador exclusivo que representa uma entidade de segurança.|
|**confiável**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que os níveis de confiança são suportados quando o parâmetro for especificado.|
|**TrustLevel**<br>Tipo de dados: Palavra-chave|Implemente esse parâmetro para que o usuário pode especificar o nível de confiança que é suportado. Por exemplo, os valores possíveis incluem fulltrust, intranet e internet.|

## <a name="see-also"></a>Consulte Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
