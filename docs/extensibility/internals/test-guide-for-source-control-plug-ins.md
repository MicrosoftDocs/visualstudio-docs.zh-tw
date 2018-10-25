---
title: 測試原始檔控制外掛程式的指南 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8df70ef5fcaffb7fe2e06df5b6d47e526ff5162f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828256"
---
# <a name="test-guide-for-source-control-plug-ins"></a>原始檔控制外掛程式測試指南
本節提供指引來測試您的原始檔控制外掛程式與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 會提供廣泛的最常見的測試區域，以及一些更複雜的區域可能會造成問題的概觀。 本概觀旨在沒有測試案例的詳盡清單。  
  
> [!NOTE]
>  某些 bug 修正和最新的增強功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 可能會發現問題的現有原始檔控制外掛程式先前不時所發生之使用舊版[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 強烈建議您測試您現有原始檔控制外掛程式在本節中，列舉的區域，即使沒有變更已對外掛程式自舊版[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="common-preparation"></a>常見的準備  
 具有機器[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和目標原始檔控制外掛程式安裝為必要。 同樣地設定第二部電腦可用部分從原始檔控制測試開啟。  
  
## <a name="definition-of-terms"></a>詞彙定義  
 為了測試指南中，使用詞彙定義如下：  
  
 用戶端專案  
 任何專案類型提供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援原始檔控制整合 (例如[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，或[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)])。  
  
 Web 專案  
 有四種類型的 Web 專案： 檔案系統、 本機 IIS，遠端站台和 FTP。  
  
- 本機路徑上建立檔案系統的專案，但它們不需要的 「 網際網路資訊服務 (IIS) 」，因為它們透過 UNC 路徑，在內部存取，而且可以放在 IDE 中，非常類似用戶端專案的原始檔控制下進行安裝。  
  
- 本機 IIS 專案搭配使用指向本機電腦的 URL 安裝在同一部電腦上，且會存取 IIS。  
  
- 遠端站台的專案也會建立在 IIS 的服務，但它們被放在原始檔控制在 IIS 伺服器電腦上，而不是從內部[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
- FTP 專案透過遠端 FTP 伺服器存取，但無法將它們放在原始檔控制。  
  
  登記  
  針對方案或專案原始檔控制下的另一種說法。  
  
  版本存放區  
  正在透過原始檔控制外掛程式 API 存取原始檔控制資料庫。  
  
## <a name="test-areas-covered-in-this-section"></a>本章節涵蓋的測試區域  
  
-   [測試區域 1︰新增至原始檔控制或從中開啟](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   案例 1： 將方案加入原始檔控制  
  
    -   案例 1b： 從原始檔控制開啟方案  
  
    -   案例 1 c： 從原始檔控制新增解決方案  
  
-   [測試區域 2︰從原始檔控制中取得](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [測試區域 3︰簽出/復原簽出](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   案例 3： 簽出/復原簽出  
  
    -   案例 3a： 簽出  
  
    -   案例 3b： 已中斷連線簽出  
  
    -   案例 3 c： 查詢編輯查詢儲存 (QEQS)  
  
    -   案例 3d： 無訊息的簽出  
  
    -   案例 3e： 恢復簽出  
  
-   [測試區域 4︰簽入](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   案例 4a： 修改項目  
  
    -   案例 4b： 新增檔案  
  
    -   案例 4c： 新增專案  
  
-   [測試區域 5︰變更原始檔控制](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   案例 5a： 繫結  
  
    -   案例 5b： 解除繫結  
  
    -   案例 5 c： 重新繫結  
  
-   [測試區域 6︰刪除](../../extensibility/internals/test-area-6-delete.md)  
  
-   [測試區域 7︰共用](../../extensibility/internals/test-area-7-share.md)  
  
-   [測試區域 8︰外掛程式切換](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   案例 8a： 自動變更  
  
    -   案例 8b： 方案為基礎的變更  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)