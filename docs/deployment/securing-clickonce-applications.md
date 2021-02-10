---
title: 設定 ClickOnce 應用程式的安全性 | Microsoft Docs
description: 瞭解 .NET Framework 中代碼啟用安全性條件約束的含意，這些限制可能會限制 ClickOnce 應用程式程式碼的存取。
ms.custom: SEO-VS-2020
ms.date: 02/17/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa698fc0ac0e46fa645ede54d6608b79dd031655
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949658"
---
# <a name="secure-clickonce-applications"></a>保護 ClickOnce 應用程式
在 .NET Framework 中，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式受到程式碼存取安全性條件約束的限制，因此能夠協助限制程式碼對受保護之資源和作業的存取。 因此，很重要的是您必須了解程式碼存取安全性的含意，照著撰寫 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。 您的應用程式可以使用完全信任或部分信任區域 (例如網際網路和內部網路區域) 以限制存取。

 此外，ClickOnce 會使用憑證以驗證應用程式發行者的真偽，並且會簽署應用程式和部署資訊清單，以證明檔案未遭修改。 簽署是選擇性步驟，讓您更方便在資訊清單產生之後變更應用程式檔案。 不過，若沒有簽署的資訊清單，就很難確保應用程式安裝程式未在攔截式安全攻擊中遭到竄改。 基於這個理由，我們建議您簽署應用程式和部署資訊清單，以協助保護應用程式的安全。

## <a name="zones"></a>區域
 使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 技術部署的應用程式受限於根據安全性區域定義的一組權限和動作。 安全性區域是在 Internet Explorer 中定義，根據應用程式的位置而有所不同。 下表依據部署位置列出預設的使用權限：

|部署位置|安全性區域|
|-------------------------|-------------------|
|從 Web 執行|網際網路區域|
|從 Web 安裝|網際網路區域|
|從網路檔案共用安裝|近端內部網路區域|
|從 CD-ROM 安裝|完全信任|

 預設的使用權限是根據應用程式原始版本的部署位置而定，此應用程式的更新仍會繼承這些使用權限。 如果將應用程式設定為從 Web 或網路位置檢查是否有更新，且發現有新版本可用時，原始安裝程序可能會取得網際網路或內部網路區域的使用權限，而非「完全信任」使用權限。 若要避免使用者看到提示，系統管理員可以指定 ClickOnce 部署原則，將特定的應用程式發行者定義為受信任的來源。 在部署此原則的電腦上，會自動授與使用權限，因此使用者就不會看到提示。 如需詳細資訊，請參閱 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)。 若要設定信任的應用程式部署，可以在電腦或企業層級安裝憑證。 如需詳細資訊，請參閱 [ 如何： 新增 ClickOnce 應用程式的用戶端電腦受信任的發行者](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)。

## <a name="code-access-security-policies"></a>程式碼存取安全性原則
 應用程式的許可權取決於應用程式資訊清單的[ \<trustInfo> element](../deployment/trustinfo-element-clickonce-application.md)元素中的設定。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會根據專案的 [安全性]  屬性頁設定，自動產生此資訊。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式只能取得它所要求的特定權限， 例如，假設檔案存取需要「完全信任」權限，如果應用程式要求「檔案存取」權限，那麼它只能取得「檔案存取」權限，而不是「完全信任」權限。 當您開發 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，應該確定只要求應用程式所需的特定權限。 在大部分情況下，您可以使用 [網際網路] 或 [近端內部網路] 區域將應用程式限制為部分信任。 如需詳細資訊，請參閱 [如何：設定 ClickOnce 應用程式的安全性區域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)。 如果應用程式需要自訂權限，您可以建立自訂區域。 如需詳細資訊，請參閱 [如何：設定 ClickOnce 應用程式的自訂許可權](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)。

 若包含部署應用程式的區域預設權限以外的權限，在安裝或更新期間，將會造成提示使用者授權。 若要避免使用者看到提示，系統管理員可以指定 ClickOnce 部署原則，將特定的應用程式發行者定義為受信任的來源。 在部署此原則的電腦上，使用權限會自動授與，因此使用者就不會看到提示。

 身為開發人員，您有責任確保您的應用程式能以適當的使用權限執行。 如果應用時間在執行階段要求區域外的權限，可能會發生安全性例外狀況。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可讓您在目標安全性區域中偵錯工具，並提供開發安全應用程式的協助。 如需詳細資訊，請參閱 [使用 System. Deployment 的 Debug ClickOnce 應用](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)程式。

 如需代碼啟用安全性和 ClickOnce 的詳細資訊，請參閱 [ClickOnce 應用程式的代碼啟用安全性](../deployment/code-access-security-for-clickonce-applications.md)。

## <a name="code-signing-certificates"></a>程式碼簽署憑證
 若要使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署發行應用程式，您必須以公開/私密金鑰組簽署應用程式和部署資訊清單。 您可以在 [專案設計工具]  的 [簽署] 頁面上找到簽署資訊清單的工具。 如需詳細資訊，請參閱 [Signing Page, Project Designer](../ide/reference/signing-page-project-designer.md)。

 簽署資訊清單之後，在安裝時，根據 Authenticode 簽章的發行者資訊會顯示在使用權限對話方塊中，讓使用者得知此應用程式是來自受信任的來源。

 如需有關 ClickOnce 及憑證的詳細資訊，請參閱 [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md)。

## <a name="aspnet-form-based-authentication"></a>ASP.NET 表單架構驗證
 如果您想要控制每一個使用者可以存取的部署，就不應該讓匿名存取部署在 Web 伺服器上的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。 您應該使用 Windows 驗證，依據使用者的識別身分讓使用者存取已經安裝好的部署。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 不支援 ASP.NET 表單架構驗證，因為它會使用持續性的 Cookie；這表示有安全性風險存在，因為 Cookie 會存在於 Internet Explorer 的快取中，而且可能會遭竊取。 因此，如果您正在部署 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，則除了 Windows 驗證之外，並不支援其他任何驗證案例。

## <a name="pass-arguments"></a>傳遞引數
 如果您需要傳遞引數到 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式中，那麼還要考量其他安全性問題。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 可讓程式開發人員提供查詢字串給透過 Web 部署的應用程式。 查詢字串會採用一系列位於 URL 結尾的名稱/值組格式，以啟動應用程式：

 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`

 查詢字串引數預設是停用狀態。 若要啟用查詢字串引數，必須在應用程式的部署資訊清單中設定 `trustUrlParameters` 屬性 (Attribute)。 這個值可以從 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 MageUI.exe 進行設定。 如需如何啟用傳遞查詢字串的詳細步驟，請參閱[如何：在線上 ClickOnce 應用程式中擷取查詢字串資訊](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)。

 請絕對不要將透過查詢字串擷取的引數傳遞給資料庫或命令列，而沒有檢查這些引數來確定其是否安全。 不安全的引數為包含資料庫或命令列逸出字元 (Escape Character) 的引數，這些引數可讓惡意使用者操縱您的應用程式來執行任意命令。

> [!NOTE]
> 查詢字串引數是在啟動 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時傳遞引數給它的唯一方法； 您不能從命令列傳遞引數給 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。

## <a name="deploying-obfuscated-assemblies"></a>部署模糊化組件
 Visual Studio 包含免費的 [PreEmptive Protection-Dotfuscator Community](../ide/dotfuscator/index.md)，可用來透過程式碼混淆和作用中的保護措施，保護您的 ClickOnce 應用程式。  如需詳細資訊，請參閱 [Dotfuscator Community 使用者指南的 ClickOnce 一節](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html)。

## <a name="see-also"></a>另請參閱
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)
