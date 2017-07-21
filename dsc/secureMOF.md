---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Protegendo o Arquivo MOF
ms.openlocfilehash: 70dec03f3b883eb88661e27c411248b8e1bb2177
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="2ac57-103">Protegendo o Arquivo MOF</span><span class="sxs-lookup"><span data-stu-id="2ac57-103">Securing the MOF File</span></span>

><span data-ttu-id="2ac57-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2ac57-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2ac57-105">Para informar aos nós de destino qual configuração deveriam ter, a DSC envia um arquivo MOF com essas informações para cada nó, em que o Gerenciador de Configurações Local (LCM) implementa a configuração desejada.</span><span class="sxs-lookup"><span data-stu-id="2ac57-105">DSC tells the target nodes what configuration they should have by sending a MOF file with that information to each node, where the Local Configuration Manager (LCM) implements the desired configuration.</span></span> <span data-ttu-id="2ac57-106">Como esse arquivo contém os detalhes da configuração, é importante mantê-lo em segurança.</span><span class="sxs-lookup"><span data-stu-id="2ac57-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span> <span data-ttu-id="2ac57-107">Para fazer isso, você pode definir o LCM para verificar as credenciais de um usuário.</span><span class="sxs-lookup"><span data-stu-id="2ac57-107">To do this, you can set the LCM to check the credentials of a user.</span></span> <span data-ttu-id="2ac57-108">Este tópico descreve como transmitir essas credenciais com segurança para o nó de destino criptografando-as com certificados.</span><span class="sxs-lookup"><span data-stu-id="2ac57-108">This topic describes how to transmit those credentials securely to the target node by encrypting them with certificates.</span></span>

><span data-ttu-id="2ac57-109">**Observação:** este tópico discute os certificados usados para criptografia.</span><span class="sxs-lookup"><span data-stu-id="2ac57-109">**Note:** This topic discusses certificates used for encryption.</span></span> <span data-ttu-id="2ac57-110">Para criptografia, um certificado autoassinado é suficiente porque a chave privada é mantida sempre segredo e a criptografia não afeta a confiança do documento.</span><span class="sxs-lookup"><span data-stu-id="2ac57-110">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span> <span data-ttu-id="2ac57-111">Certificados autoassinados *não* devem ser usados para fins de autenticação.</span><span class="sxs-lookup"><span data-stu-id="2ac57-111">Self-signed certificates should *not* be used for authentication purposes.</span></span> <span data-ttu-id="2ac57-112">Você deve usar um certificado de uma AC (Autoridade de Certificação) confiável para fins de autenticação.</span><span class="sxs-lookup"><span data-stu-id="2ac57-112">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ac57-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2ac57-113">Prerequisites</span></span>

<span data-ttu-id="2ac57-114">Para criptografar com êxito as credenciais usadas para proteger uma configuração DSC, verifique se que você tem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2ac57-114">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

* <span data-ttu-id="2ac57-115">**Algum meio de emitir e distribuir certificados**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-115">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="2ac57-116">Este tópico e seus exemplos pressupõem que você está usando uma Autoridade de Certificação do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2ac57-116">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="2ac57-117">Para obter mais informações sobre os Serviços de Certificados do Active Directory, consulte [Visão Geral dos Serviços de Certificados do Active Directory](https://technet.microsoft.com/library/hh831740.aspx) e [Serviços de Certificados do Active Directory no Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="2ac57-117">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
* <span data-ttu-id="2ac57-118">**Acesso administrativo ao nó ou nós de destino**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-118">**Administrative access to the target node or nodes**.</span></span>
* <span data-ttu-id="2ac57-119">**Cada nó de destino tem um certificado com capacidade de criptografia salvo no seu Repositório Pessoal**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-119">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="2ac57-120">No Windows PowerShell, o caminho até o repositório é Cert:\LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="2ac57-120">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="2ac57-121">Os exemplos neste tópico usam o modelo “autenticação de estação de trabalho”, que você pode encontrar (junto com outros modelos de certificado) em [Modelos de Certificados Padrão](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="2ac57-121">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
* <span data-ttu-id="2ac57-122">Se você for executar essa configuração em um computador diferente do nó de destino, **exporte a chave pública do certificado** e, em seguida, importe-a para o computador no qual executará a configuração.</span><span class="sxs-lookup"><span data-stu-id="2ac57-122">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="2ac57-123">Certifique-se de exportar apenas a chave **pública**; mantenha a chave privada em segurança.</span><span class="sxs-lookup"><span data-stu-id="2ac57-123">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="2ac57-124">Processo geral</span><span class="sxs-lookup"><span data-stu-id="2ac57-124">Overall process</span></span>

 1. <span data-ttu-id="2ac57-125">Configure os certificados, chaves e as impressões digitais, certificando-se de que cada nó de destino possua cópias do certificado e que o computador de configuração tenha a chave pública e a impressão digital.</span><span class="sxs-lookup"><span data-stu-id="2ac57-125">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="2ac57-126">Crie um bloco de dados de configuração que contenha o caminho e a impressão digital da chave pública.</span><span class="sxs-lookup"><span data-stu-id="2ac57-126">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="2ac57-127">Crie um script de configuração que defina a configuração desejada para o nó de destino e configure a descriptografia em nós de destino ao ordenar que o Gerenciador de Configurações Local descriptografe os dados de configuração usando o certificado e sua impressão digital.</span><span class="sxs-lookup"><span data-stu-id="2ac57-127">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="2ac57-128">Execute a configuração, que definirá as configurações do Gerenciador de Configurações Local e iniciará a configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="2ac57-128">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagrama1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="2ac57-130">Requisitos de Certificado</span><span class="sxs-lookup"><span data-stu-id="2ac57-130">Certificate Requirements</span></span>

<span data-ttu-id="2ac57-131">Para ativar a criptografia de credenciais, um certificado de chave pública deve estar disponível no _Nó de Destino_ que é **confiável** para o computador que está sendo usado para criar a configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="2ac57-131">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="2ac57-132">Esse certificado de chave pública tem requisitos específicos para ser usado para criptografia de credencial DSC:</span><span class="sxs-lookup"><span data-stu-id="2ac57-132">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>
 1. <span data-ttu-id="2ac57-133">**Uso de chave**:</span><span class="sxs-lookup"><span data-stu-id="2ac57-133">**Key Usage**:</span></span>
   - <span data-ttu-id="2ac57-134">Deve conter: 'KeyEncipherment' e 'DataEncipherment'.</span><span class="sxs-lookup"><span data-stu-id="2ac57-134">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="2ac57-135">_Não_ deve conter: “Assinatura Digital”.</span><span class="sxs-lookup"><span data-stu-id="2ac57-135">Should _not_ contain: 'Digital Signature'.</span></span>
 2. <span data-ttu-id="2ac57-136">**Uso avançado de chave**:</span><span class="sxs-lookup"><span data-stu-id="2ac57-136">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="2ac57-137">Deve conter: Criptografia de Documento (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="2ac57-137">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="2ac57-138">_Não_ deve conter: Autenticação de Cliente (1.3.6.1.5.5.7.3.2) e Autenticação de Servidor (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="2ac57-138">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
 3. <span data-ttu-id="2ac57-139">A Chave Privada do certificado está disponível no *Nó de Destino_.</span><span class="sxs-lookup"><span data-stu-id="2ac57-139">The Private Key for the certificate is available on the *Target Node_.</span></span>
 4. <span data-ttu-id="2ac57-140">O **Provedor** para o certificado deve ser "Microsoft RSA SChannel Cryptographic Provider".</span><span class="sxs-lookup"><span data-stu-id="2ac57-140">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>
 
><span data-ttu-id="2ac57-141">**Melhor Prática Recomendada:** embora você possa usar um certificado contendo um Uso de Chave de 'Assinatura Digital' ou um dos EKUs de autenticação, isso permitirá que a chave de criptografia seja mais facilmente usada de modo incorreto e fique mais vulnerável a ataques.</span><span class="sxs-lookup"><span data-stu-id="2ac57-141">**Recommended Best Practice:** Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="2ac57-142">Assim, a melhor prática é usar um certificado criado especificamente para a finalidade de proteger credenciais DSC que omite esses Usos de Chave e EKUs.</span><span class="sxs-lookup"><span data-stu-id="2ac57-142">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>
  
<span data-ttu-id="2ac57-143">Qualquer certificado existente no _Nó de Destino_ que atende esses critérios pode ser usado para proteger credenciais DSC.</span><span class="sxs-lookup"><span data-stu-id="2ac57-143">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="2ac57-144">Criação de certificado</span><span class="sxs-lookup"><span data-stu-id="2ac57-144">Certificate creation</span></span>

<span data-ttu-id="2ac57-145">Há duas abordagens que você pode executar para criar e usar o certificado de criptografia necessário (par de chaves públicas-privadas).</span><span class="sxs-lookup"><span data-stu-id="2ac57-145">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="2ac57-146">Criá-lo no **Nó de Destino** e exportar apenas a chave pública para o **Nó de Criação**</span><span class="sxs-lookup"><span data-stu-id="2ac57-146">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="2ac57-147">Criá-lo no **Nó de Criação** e exportar o par de chaves inteiro para o **Nó de Destino**</span><span class="sxs-lookup"><span data-stu-id="2ac57-147">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="2ac57-148">O Método 1 é recomendado porque a chave privada usada para descriptografar credenciais no MOF permanece no nó de destino em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="2ac57-148">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>


### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="2ac57-149">Criando o certificado no nó de destino</span><span class="sxs-lookup"><span data-stu-id="2ac57-149">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="2ac57-150">A chave privada deve ser mantida em segredo, pois é usada para descriptografar o MOF no **Nó de Destino**. A forma mais fácil de fazer isso é criar o certificado da chave privada no **Nó de Destino** e copiar o **certificado de chave pública** no computador que está sendo usado para criar a configuração DSC em um arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="2ac57-150">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="2ac57-151">O exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2ac57-151">The following example:</span></span>
 1. <span data-ttu-id="2ac57-152">cria um certificado no **Nó de destino**</span><span class="sxs-lookup"><span data-stu-id="2ac57-152">creates a certificate on the **Target node**</span></span>
 2. <span data-ttu-id="2ac57-153">exporta o certificado de chave pública para o **Nó de destino**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-153">exports the public key certificate on the **Target node**.</span></span>
 3. <span data-ttu-id="2ac57-154">importa o certificado de chave pública para o **meu** repositório de certificados no **Nó de criação**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-154">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="2ac57-155">No Nó de destino: criar e exportar o certificado</span><span class="sxs-lookup"><span data-stu-id="2ac57-155">On the Target Node: create and export the certificate</span></span>
><span data-ttu-id="2ac57-156">Nó de Criação: Windows Server 2016 e Windows 10</span><span class="sxs-lookup"><span data-stu-id="2ac57-156">Authoring Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="2ac57-157">Uma vez exportado, o ```DscPublicKey.cer``` precisaria ser copiados no **Nó de Criação**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-157">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

><span data-ttu-id="2ac57-158">Nó de Criação: Windows Server 2012 R2/Windows 8.1 e versões anteriores</span><span class="sxs-lookup"><span data-stu-id="2ac57-158">Authoring Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="2ac57-159">Como não há suporte para o cmdlet New-SelfSignedCertificate em sistemas operacionais Windows anteriores ao Windows 10 e o Windows Server 2016 não dá suporte ao parâmetro **Type**, um método alternativo de criar esse certificado é necessário nesses sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="2ac57-159">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="2ac57-160">Nesse caso, você pode usar ```makecert.exe``` ou ```certutil.exe``` para criar o certificado.</span><span class="sxs-lookup"><span data-stu-id="2ac57-160">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="2ac57-161">Um método alternativo é [baixar o script New-SelfSignedCertificateEx.ps1 do Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e usá-lo para criar o certificado em vez disso:</span><span class="sxs-lookup"><span data-stu-id="2ac57-161">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -StoreName 'My' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="2ac57-162">Uma vez exportado, o ```DscPublicKey.cer``` precisaria ser copiados no **Nó de Criação**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-162">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="2ac57-163">No Nó de Criação: importar a chave pública do certificado</span><span class="sxs-lookup"><span data-stu-id="2ac57-163">On the Authoring Node: import the cert’s public key</span></span>
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="2ac57-164">Criando o certificado no Nó de Criação</span><span class="sxs-lookup"><span data-stu-id="2ac57-164">Creating the Certificate on the Authoring Node</span></span>
<span data-ttu-id="2ac57-165">Como alternativa, o certificado de criptografia pode ser criado no **Nó de Criação**, exportado com a **chave privada** como um arquivo PFX e, em seguida, importado no **Nó de Destino**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-165">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="2ac57-166">Esse é o método atual para implementar a criptografia de credencial DSC no _Nano Server_.</span><span class="sxs-lookup"><span data-stu-id="2ac57-166">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="2ac57-167">Embora o PFX seja protegido por uma senha, ele deve ser mantido seguro durante o trânsito.</span><span class="sxs-lookup"><span data-stu-id="2ac57-167">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="2ac57-168">O exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2ac57-168">The following example:</span></span>
 1. <span data-ttu-id="2ac57-169">cria um certificado no **Nó de criação**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-169">creates a certificate on the **Authoring node**.</span></span>
 2. <span data-ttu-id="2ac57-170">exporta o certificado, incluindo a chave privada do **Nó de criação**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-170">exports the certificate including the private key on the **Authoring node**.</span></span>
 3. <span data-ttu-id="2ac57-171">remove a chave privada do **Nó de criação**, mas mantém o certificado de chave pública no **meu** repositório.</span><span class="sxs-lookup"><span data-stu-id="2ac57-171">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
 4. <span data-ttu-id="2ac57-172">importa o certificado de chave privada para o repositório de certificados raiz no **Nó de destino**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-172">imports the private key certificate into the root certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="2ac57-173">ele deve ser adicionado ao repositório raiz para que seja confiável pelo **Nó de destino**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-173">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="2ac57-174">No Nó de criação: criar e exportar o certificado</span><span class="sxs-lookup"><span data-stu-id="2ac57-174">On the Authoring Node: create and export the certificate</span></span>
><span data-ttu-id="2ac57-175">Nó de destino: Windows Server 2016 e Windows 10</span><span class="sxs-lookup"><span data-stu-id="2ac57-175">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```
<span data-ttu-id="2ac57-176">Uma vez exportado, o ```DscPrivateKey.cer``` precisaria ser copiado no **Nó de Destino**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-176">Once exported, the ```DscPrivateKey.cer``` would need to be copied to the **Target Node**.</span></span>

><span data-ttu-id="2ac57-177">Nó de destino: Windows Server 2012 R2/Windows 8.1 e versões anteriores</span><span class="sxs-lookup"><span data-stu-id="2ac57-177">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="2ac57-178">Como não há suporte para o cmdlet New-SelfSignedCertificate em sistemas operacionais Windows anteriores ao Windows 10 e o Windows Server 2016 não dá suporte ao parâmetro **Type**, um método alternativo de criar esse certificado é necessário nesses sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="2ac57-178">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="2ac57-179">Nesse caso, você pode usar ```makecert.exe``` ou ```certutil.exe``` para criar o certificado.</span><span class="sxs-lookup"><span data-stu-id="2ac57-179">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="2ac57-180">Um método alternativo é [baixar o script New-SelfSignedCertificateEx.ps1 do Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e usá-lo para criar o certificado em vez disso:</span><span class="sxs-lookup"><span data-stu-id="2ac57-180">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="2ac57-181">No Nó de destino: importar a chave privada do certificado como uma raiz confiável</span><span class="sxs-lookup"><span data-stu-id="2ac57-181">On the Target Node: import the cert’s private key as a trusted root</span></span>
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\Root -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="2ac57-182">Dados de configuração</span><span class="sxs-lookup"><span data-stu-id="2ac57-182">Configuration data</span></span>

<span data-ttu-id="2ac57-183">O bloco de dados de configuração define em quais nós de destino vai operar, se vai criptografar as credenciais ou não, o meio de criptografia e outras informações.</span><span class="sxs-lookup"><span data-stu-id="2ac57-183">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="2ac57-184">Para obter mais informações sobre o bloco de dados de configuração, consulte [Separando Dados de Configuração e de Ambiente](configData.md).</span><span class="sxs-lookup"><span data-stu-id="2ac57-184">For more information on the configuration data block, see [Separating Configuration and Environment Data](configData.md).</span></span>

<span data-ttu-id="2ac57-185">Os elementos que podem ser configurados para cada nó que estão relacionados à criptografia de credencial são:</span><span class="sxs-lookup"><span data-stu-id="2ac57-185">The elements that can be configured for each node that are related to credential encryption are:</span></span>
* <span data-ttu-id="2ac57-186">**NodeName**: o nome do nó de destino para o qual a criptografia de credencial está sendo configurada.</span><span class="sxs-lookup"><span data-stu-id="2ac57-186">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
* <span data-ttu-id="2ac57-187">**PsDscAllowPlainTextPassword**: se credenciais sem criptografia poderão ou não ser passadas para esse nó.</span><span class="sxs-lookup"><span data-stu-id="2ac57-187">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="2ac57-188">Isso **não é recomendável**.</span><span class="sxs-lookup"><span data-stu-id="2ac57-188">This is **not recommended**.</span></span>
* <span data-ttu-id="2ac57-189">**Impressão digital**: a impressão digital do certificado que será usada para descriptografar as credenciais na Configuração DSC no _Nó de Destino_.</span><span class="sxs-lookup"><span data-stu-id="2ac57-189">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="2ac57-190">**Esse certificado deve existir no repositório de certificados do Computador Local no Nó de Destino.**</span><span class="sxs-lookup"><span data-stu-id="2ac57-190">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
* <span data-ttu-id="2ac57-191">**CertificateFile**: o arquivo de certificado (contendo somente a chave pública) que deve ser usado para criptografar as credenciais para o _Nó de Destino_.</span><span class="sxs-lookup"><span data-stu-id="2ac57-191">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="2ac57-192">Isso deve ser X.509 binário codificado por DER ou um arquivo de certificado de formato X.509 com codificação de Base 64.</span><span class="sxs-lookup"><span data-stu-id="2ac57-192">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="2ac57-193">Este exemplo mostra um bloco de dados de configuração que especifica um nó de destino para atuar no targetNode nomeado, o caminho até o arquivo de certificado de chave pública (denominado targetNode.cer) e a impressão digital da chave pública.</span><span class="sxs-lookup"><span data-stu-id="2ac57-193">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

```powershell
$ConfigData= @{ 
    AllNodes = @(     
            @{  
                # The name of the node we are describing 
                NodeName = "targetNode" 

                # The path to the .cer file containing the 
                # public key of the Encryption Certificate 
                # used to encrypt credentials for this node 
                CertificateFile = "C:\publicKeys\targetNode.cer" 

         
                # The thumbprint of the Encryption Certificate 
                # used to decrypt the credentials on target node 
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8" 
            }; 
        );    
    }
```


## <a name="configuration-script"></a><span data-ttu-id="2ac57-194">Script de configuração</span><span class="sxs-lookup"><span data-stu-id="2ac57-194">Configuration script</span></span>

<span data-ttu-id="2ac57-195">No próprio script de configuração, use o parâmetro `PsCredential` para garantir que as credenciais sejam armazenadas pelo menor tempo possível.</span><span class="sxs-lookup"><span data-stu-id="2ac57-195">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="2ac57-196">Quando você executa o exemplo fornecido, a DSC solicitará credenciais e, em seguida, criptografará o arquivo MOF usando o CertificateFile que está associado com o nó de destino no bloco de dados de configuração.</span><span class="sxs-lookup"><span data-stu-id="2ac57-196">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="2ac57-197">Este exemplo de código copia um arquivo de um compartilhamento protegido para um usuário.</span><span class="sxs-lookup"><span data-stu-id="2ac57-197">This code example copies a file from a share that is secured to a user.</span></span>

```
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
    } 
}
```

## <a name="setting-up-decryption"></a><span data-ttu-id="2ac57-198">Configurando a descriptografia</span><span class="sxs-lookup"><span data-stu-id="2ac57-198">Setting up decryption</span></span>

<span data-ttu-id="2ac57-199">Para que o [`Start-DscConfiguration`](https://technet.microsoft.com/en-us/library/dn521623.aspx) possa funcionar, você precisa informar ao Gerenciador de Configurações Local em cada nó de destino qual certificado usar para descriptografar as credenciais, usando o recurso CertificateID para verificar a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="2ac57-199">Before [`Start-DscConfiguration`](https://technet.microsoft.com/en-us/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="2ac57-200">A função neste exemplo encontrará o certificado local apropriado (talvez seja necessário personalizá-lo para ele encontrar o certificado exato que você deseja usar):</span><span class="sxs-lookup"><span data-stu-id="2ac57-200">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

```powershell
# Get the certificate that works for encryption 
function Get-LocalEncryptionCertificateThumbprint 
{ 
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid 
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify()) 
        { 
            return $_.Thumbprint 
        } 
    } 
}
```

<span data-ttu-id="2ac57-201">Com o certificado identificado por sua impressão digital, o script de configuração pode ser atualizado para usar o valor:</span><span class="sxs-lookup"><span data-stu-id="2ac57-201">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

```powershell
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
        
        LocalConfigurationManager 
        { 
             CertificateId = $node.Thumbprint 
        } 
    } 
}
```

## <a name="running-the-configuration"></a><span data-ttu-id="2ac57-202">Executando a configuração</span><span class="sxs-lookup"><span data-stu-id="2ac57-202">Running the configuration</span></span>

<span data-ttu-id="2ac57-203">Neste ponto, você pode executar a configuração, o que resultará em dois arquivos:</span><span class="sxs-lookup"><span data-stu-id="2ac57-203">At this point, you can run the configuration, which will output two files:</span></span>

 * <span data-ttu-id="2ac57-204">Um arquivo *.meta.mof que configura o Gerenciador de Configurações Local para descriptografar as credenciais usando o certificado armazenado no repositório do computador local e identificado por sua impressão digital.</span><span class="sxs-lookup"><span data-stu-id="2ac57-204">A *.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="2ac57-205">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx) aplica o arquivo *.meta.mof.</span><span class="sxs-lookup"><span data-stu-id="2ac57-205">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx) applies the *.meta.mof file.</span></span>
 * <span data-ttu-id="2ac57-206">Um arquivo MOF que realmente aplica a configuração.</span><span class="sxs-lookup"><span data-stu-id="2ac57-206">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="2ac57-207">O Start-DscConfiguration aplica a configuração.</span><span class="sxs-lookup"><span data-stu-id="2ac57-207">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="2ac57-208">Estes comandos realizarão estas etapas:</span><span class="sxs-lookup"><span data-stu-id="2ac57-208">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="2ac57-209">Este exemplo enviaria por push a configuração DSC para o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="2ac57-209">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="2ac57-210">A configuração DSC também poderá ser aplicada usando um Servidor de Pull de DSC, se houver um disponível.</span><span class="sxs-lookup"><span data-stu-id="2ac57-210">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="2ac57-211">Consulte [Configurando um cliente pull de DSC](pullClient.md) para obter mais informações sobre como aplicar configurações de DSC usando um Servidor de Pull de DSC.</span><span class="sxs-lookup"><span data-stu-id="2ac57-211">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="2ac57-212">Exemplo de Módulo de Criptografia de Credencial</span><span class="sxs-lookup"><span data-stu-id="2ac57-212">Credential Encryption Module Example</span></span>

<span data-ttu-id="2ac57-213">Aqui está um exemplo completo que incorpora todas essas etapas, além de um cmdlet auxiliar que exporta e copia as chaves públicas:</span><span class="sxs-lookup"><span data-stu-id="2ac57-213">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )
    

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }
        
        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key 
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"         

    $ConfigData=    @{
        AllNodes = @(     
                        @{  
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );    
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration") 

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer") 

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```

