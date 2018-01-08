---
title: "測試原始檔控制外掛程式的指南 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0fdab6cb0b259fe169a9ebd43c92158a5ce20d4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="test-guide-for-source-control-plug-ins"></a>測試指南的原始檔控制外掛程式
本節提供指引來測試您的原始檔控制外掛程式與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 會提供更詳盡的最常見的測試區域，以及某些更錯綜複雜區域可能有問題的概觀。 本概觀不是測試案例的完整清單。  
  
> [!NOTE]
>  某些 bug 修正和最新的增強功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 可能會發現問題的現有原始檔控制外掛程式先前不時所遇到的使用舊版[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 強烈建議您測試您現有原始檔控制外掛程式列舉在本節中的區域，即使沒有變更所做的外掛程式自前一版[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="common-preparation"></a>常見的準備工作  
 一部電腦[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和目標原始檔控制外掛程式安裝，則需要。 同樣地設定第二部電腦可用的 「 從原始檔控制測試開啟某些。  
  
## <a name="definition-of-terms"></a>詞彙定義  
 本測試指南，請使用下列詞彙定義：  
  
 用戶端專案  
 任何專案類型提供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援原始檔控制整合 (例如， [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，或[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)])。  
  
 Web 專案  
 有四種類型的 Web 專案： 檔案系統、 本機 IIS、 遠端站台和 FTP。  
  
-   本機路徑上建立檔案系統的專案，但不是需要為它們透過 UNC 路徑，在內部存取，而且可以放置在 IDE 中，非常類似用戶端專案，從原始檔控制下安裝網際網路資訊服務 (IIS)。  
  
-   本機 IIS 專案使用的 IIS 安裝在同一部電腦上，而且可存取指向本機電腦的 url。  
  
-   遠端站台的專案也會建立 IIS 的服務 下，但它們被放在 IIS 伺服器電腦上，而不是從原始檔控制下內[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
-   FTP 專案透過遠端 FTP 伺服器存取，但不能放在原始檔控制。  
  
 登記  
 方案或專案原始檔控制下的另一個詞彙。  
  
 版本存放區  
 正在透過原始檔控制外掛程式 API 存取原始檔控制資料庫。  
  
## <a name="test-areas-covered-in-this-section"></a>本章節涵蓋的測試區域  
  
-   [測試區域 1： 加入開啟從原始檔控制](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   案例 1： 將方案加入至原始檔控制  
  
    -   案例 1b： 從原始檔控制開啟方案  
  
    -   案例 1 c： 將方案加入原始檔控制中  
  
-   [測試區域 2︰從原始檔控制中取得](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [測試區域 3： 簽出/恢復簽出](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   案例 3： 簽出/恢復簽出  
  
    -   案例 3a： 簽出  
  
    -   案例 3b： 中斷連接簽出  
  
    -   案例 3 c： 查詢編輯查詢儲存 (QEQS)  
  
    -   大小寫 3d： 無訊息的簽出  
  
    -   大小寫 3e： 恢復簽出  
  
-   [測試區域 4︰簽入](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   大小寫 4a： 修改項目  
  
    -   案例 4b： 新增檔案  
  
    -   案例 4c： 加入專案  
  
-   [測試區域 5︰變更原始檔控制](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   大小寫 5a： 繫結  
  
    -   大小寫 5b： 解除繫結  
  
    -   案例 5 c： 重新繫結  
  
-   [測試區域 6︰刪除](../../extensibility/internals/test-area-6-delete.md)  
  
-   [測試區域 7︰共用](../../extensibility/internals/test-area-7-share.md)  
  
-   [測試區域 8︰外掛程式切換](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   大小寫 8a： 自動變更  
  
    -   大小寫 8b： 方案架構的變更  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)