---
title: 原始檔控制外掛程式的測試指南 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 321d61175068f135aae87bff73f13ac800f4793c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905153"
---
# <a name="test-guide-for-source-control-plug-ins"></a>原始檔控制外掛程式測試指南
本節提供使用測試原始檔控制外掛程式的指導方針 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 其中提供了最常見的測試區域，以及可能有問題的一些較複雜區域的詳盡總覽。 此總覽不是完整的測試案例清單。

> [!NOTE]
> 針對最新 IDE 的一些 bug 修正和改善， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可能會發現使用舊版時，先前未遇到的現有原始檔控制外掛程式發生問題 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 強烈建議您為此區段中列舉的區域測試現有的原始檔控制外掛程式，即使自舊版以來並未對外掛程式進行任何變更也是一樣 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

## <a name="common-preparation"></a>一般準備工作
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]已安裝和目標原始檔控制外掛程式的電腦為必要項。 另一部類似設定的電腦，可用於某些從原始檔控制測試的開啟。

## <a name="definition-of-terms"></a>詞彙的定義
 基於此測試指南的目的，請使用下列詞彙定義：

 用戶端專案任何可 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援原始檔控制整合的專案類型（例如、 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 或 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ）。

 Web 專案有四種類型的 Web 專案： [檔案系統]、[本機 IIS]、[遠端網站] 和 [FTP]。

- 檔案系統專案是在本機路徑上建立，但不需要安裝 Internet Information Services （IIS），因為它們是透過 UNC 路徑從內部存取，而且可以放在 IDE 內部的原始檔控制之下，與用戶端專案很相似。

- 本機 IIS 專案會與安裝在同一部電腦上的 IIS 搭配使用，並使用指向本機電腦的 URL 來存取。

- 遠端網站專案也是在 IIS 服務下建立，但它們放在 IIS 伺服器電腦的原始檔控制之下，而不是從 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 內部。

- FTP 專案是透過遠端 FTP 伺服器來存取，但不能放在原始檔控制之下。

  針對原始檔控制下的方案或專案登記另一個詞彙。

  版本存放區：透過原始檔控制外掛程式 API 存取的原始檔控制資料庫。

## <a name="test-areas-covered-in-this-section"></a>本節涵蓋的測試區域

- [測試區域1：在原始檔控制中加入/開啟](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - 案例1a：將方案加入至原始檔控制

  - 案例1b：從原始檔控制開啟方案

  - Case 1c：從原始檔控制加入方案

- [測試區域 2︰從原始檔控制中取得](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [測試區域3：簽出/復原簽出](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - 案例3：簽出/復原簽出

  - 案例3a：簽出

  - 案例3b：中斷連線的簽出

  - 案例3c：查詢編輯/查詢儲存（QEQS）

  - 案例3d：無訊息簽出

  - 案例3e：復原簽出

- [測試區域 4︰簽入](../../extensibility/internals/test-area-4-check-in.md)

  - 案例4a：已修改的專案

  - 案例4b：新增檔案

  - Case 4c：加入專案

- [測試區域 5︰變更原始檔控制](../../extensibility/internals/test-area-5-change-source-control.md)

  - 案例5a： Bind

  - Case 5b：解除系結

  - 案例5c：重新系結

- [測試區域 6︰刪除](../../extensibility/internals/test-area-6-delete.md)

- [測試區域 7︰共用](../../extensibility/internals/test-area-7-share.md)

- [測試區域 8︰外掛程式切換](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - 案例8a：自動變更

  - 案例8b：以解決方案為基礎的變更

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)
