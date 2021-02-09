---
title: ASP.NET 調試：系統需求 |Microsoft Docs
description: 請參閱 ASP.NET 本機偵錯工具的軟體和安全性需求，其中 Visual Studio 與 web 應用程式在相同電腦上執行，以及遠端偵錯程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 8ab32e855ee93ceb328bc33340597ce65e3ee871
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866095"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET 偵錯：系統需求
本主題描述 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 偵錯情節的軟體和安全性需求：

- 本機偵錯： [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 Web 應用程式會在同一部電腦上執行。 這個情節有兩種版本：

  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程序碼位於檔案系統上。

  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程序碼位於 IIS 網站中。

- 遠端偵錯： [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在用戶端電腦上執行，並對遠端伺服器電腦上執行的 Web 應用程式進行偵錯。

## <a name="security-requirements"></a>安全性需求
 若要進行遠端偵錯，本機和遠端電腦都必須在網域設定或工作群組設定中。

 若要對 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式集區) 所裝載的背景工作進程 (進行偵錯工具，您必須具有偵錯工具的許可權。 根據預設， [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] IIS 6.0 之前的應用程式會以 **ASPNET** 使用者的身份執行。 在 IIS 6.0 和 IIS 7.0 中， **NETWORK SERVICE** 帳戶是預設值。 如果背景工作處理序是以 **ASPNET** 或 **NETWORK SERVICE** 身分執行，則您必須具有 Administrator 權限才能對它進行偵錯。

 > [!IMPORTANT]
 > 從 Windows Server 2008 R2 開始，建議使用 [>applicationpoolidentity](/iis/manage/configuring-security/application-pool-identities) 作為每個應用程式集區的身分識別。

 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序的名稱會隨偵錯情節和 IIS 的版本而有所不同。 如需詳細資訊，請參閱 [如何：尋找 ASP.NET 處理序的名稱](../debugger/how-to-find-the-name-of-the-aspnet-process.md)。

 您可以編輯執行 IIS 的伺服器上的 machine.config 檔案，變更 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序執行的使用者帳戶。 若要執行這項操作，最好是使用 [Internet Information Services (IIS) 管理員] 。 如需詳細資訊，請參閱 [如何：在使用者帳戶下執行背景工作進程](../debugger/how-to-run-the-worker-process-under-a-user-account.md)。

 如果您將 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序變更為以您自己的使用者帳戶執行，您就不需要是執行 IIS 之伺服器上的系統管理員。

> [!CAUTION]
> 在您將 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序變更為以不同帳戶執行之前，請考慮以該帳戶執行 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序時，處理序遭到竊取的後果。 ASPNET 和 NETWORK SERVICE 使用者帳戶會以最低權限執行，因此可降低處理序遭竊取時可能造成的損害。 如果您必須將 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序變更為以具有較高權限的帳戶執行，可能造成的損害也會較大。

## <a name="see-also"></a>另請參閱

- [ASP.NET 應用程式的偵錯工具](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [如何：在使用者帳戶下執行背景工作進程](../debugger/how-to-run-the-worker-process-under-a-user-account.md)