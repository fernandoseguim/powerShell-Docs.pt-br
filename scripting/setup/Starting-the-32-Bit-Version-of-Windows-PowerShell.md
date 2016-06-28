---
title: "Iniciando a versão de 32 bits do Windows PowerShell"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
translationtype: Human Translation
ms.sourcegitcommit: b6ab9bfdd779a865c1f543bf16e91ec17b43c4b0
ms.openlocfilehash: 41bbdd302aa3aa0d253bc4c820fdbbeb1b827ccc

---

# Iniciando a versão de 32 bits do Windows PowerShell
Quando você instala o Windows PowerShell em um computador de 64 bits, o **Windows PowerShell (x86)**, uma versão de 32 bits do Windows PowerShell é instalada juntamente com a versão de 64 bits. Quando você executa o Windows PowerShell, a versão de 64 bits é executada por padrão.

No entanto, ocasionalmente pode ser necessário executar o **Windows PowerShell (x86)**, como quando você estiver usando um módulo que requeira a versão de 32 bits ou quando você quiser se conectar remotamente a um computador de 32 bits.

Para iniciar uma versão de 32 bits do Windows PowerShell, use qualquer um dos procedimentos a seguir.

#### No Windows Server® 2012 R2

-   Na tela **Iniciar**, clique em **Windows PowerShell (x86)**. Clique no bloco **Windows PowerShell x86**.

-   Em **Gerenciador do Servidor**, no menu **Ferramentas**, selecione **Windows PowerShell (x86)**.

-   Na área de trabalho, mova o cursor para o canto superior direito, clique em **Pesquisar**, digite **PowerShell x86** e clique em **Windows PowerShell (x86)**.

-   Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### No Windows Server 2012

-   Na tela **Iniciar**, digite **PowerShell** e clique em **Windows PowerShell (x86)**.

-   Em **Gerenciador do Servidor**, no menu **Ferramentas**, selecione **Windows PowerShell (x86)**.

-   Na área de trabalho, mova o cursor para o canto superior direito, clique em **Pesquisar**, digite **PowerShell** e clique em **Windows PowerShell (x86)**.

-   Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### No Windows 8.1

-   Na tela **Iniciar**, clique em **Windows PowerShell (x86)**. Clique no bloco **Windows PowerShell x86**.

-   Se estiver executando as [Ferramentas de Administração de Servidor Remoto](http://go.microsoft.com/fwlink/?LinkID=304145) para o Windows 8.1, você também poderá abrir o Windows PowerShell x86 no menu **Ferramentas do Gerenciador do Servidor**. Selecione **Windows PowerShell (x86)**.

-   Na área de trabalho, mova o cursor para o canto superior direito, clique em **Pesquisar**, digite **PowerShell x86** e clique em **Windows PowerShell (x86)**.
   
-   Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### No Windows 8

-   Na tela **Iniciar**, mova o cursor para o canto superior direito, clique em **Configurações**, **Blocos** e mova o controle deslizante **Mostrar Ferramentas Administrativas** para Sim. Em seguida, digite **PowerShell** e clique em **Windows PowerShell (x86)**.

-   Se estiver executando as [Ferramentas de Administração de Servidor Remoto](http://www.microsoft.com/download/details.aspx?id=28972) para o Windows 8, você também poderá abrir o Windows PowerShell x86 no menu **Ferramentas do Gerenciador do Servidor**. Selecione **Windows PowerShell (x86)**.

-   Na tela **Iniciar** ou na área de trabalho, digite **PowerShell (x86)** e clique em **Windows PowerShell (x86)**.

-   Por meio da linha de comando, digite: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`



<!--HONumber=Jun16_HO4-->


