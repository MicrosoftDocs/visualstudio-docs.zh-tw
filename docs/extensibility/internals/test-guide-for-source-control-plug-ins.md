---
title: 原始檔控制外掛程式的測試指南 |Microsoft Docs
description: 瞭解如何使用 Visual Studio 測試您的原始檔控制外掛程式。 本總覽包含常見的測試區域。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 465378069c5ac5d5a516e94bdaa2120a843d9914
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090781"
---
# <a name="test-guide-for-source-control-plug-ins"></a>原始檔控制外掛程式測試指南
本節提供使用測試原始檔控制外掛程式的指引 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 提供最常見的測試區域，以及某些可能有問題的更複雜區域的廣泛總覽。 本總覽並非完整的測試案例清單。

> [!NOTE]
> 針對最新 IDE 的部分 bug 修正和改善， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可能會發現現有的原始檔控制外掛程式發生問題，這些外掛程式先前在使用舊版時並未遇到 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 強烈建議您針對本節列舉的區域測試現有的原始檔控制外掛程式，即使自舊版以來尚未對外掛程式進行任何變更也是一樣 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

## <a name="common-preparation"></a>一般準備工作
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]需要已安裝和目標原始檔控制外掛程式的電腦。 以同樣設定的第二部機器可用於某些從原始檔控制測試中開啟的。

## <a name="definition-of-terms"></a>詞彙定義
 基於此測試指南的目的，請使用下列詞彙定義：

 用戶端專案中的任何可用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的專案類型都支援原始檔控制整合 (例如、、 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 或 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]) 。

 Web 專案有四種類型的 Web 專案： [檔案系統]、[本機 IIS]、[遠端網站] 和 [FTP]。

- 檔案系統專案是在本機路徑上建立的，但不需要安裝 Internet Information Services (IIS) ，因為它們是透過 UNC 路徑從內部存取，而且可以放在 IDE 內部的原始檔控制之下，就像用戶端專案一樣。

- 本機 IIS 專案與安裝在同一部電腦上的 IIS 搭配使用，並使用指向本機電腦的 URL 來存取。

- 遠端網站專案也是在 IIS 服務下建立的，但會放在 IIS 伺服器電腦的原始檔控制下，而不是放在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 內。

- FTP 專案是透過遠端 FTP 伺服器來存取，但是無法放置在原始檔控制之下。

  在原始檔控制下登記方案或專案的另一個詞彙。

  版本存放區：透過原始檔控制外掛程式 API 存取的原始檔控制資料庫。

## <a name="test-areas-covered-in-this-section"></a>本節涵蓋的測試區域

- [測試區域 1：新增至原始檔控制/從原始檔控制開啟](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - 案例1a：將方案加入至原始檔控制

  - 案例1b：從原始檔控制開啟方案

  - 案例1c：從原始檔控制加入方案

- [測試區域 2：從原始檔控制取得](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [測試區域 3：簽出/復原簽出](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - 案例3：簽出/復原簽出

  - 案例3a：簽出

  - 案例3b：中斷連線簽出

  - 案例3c：查詢編輯/查詢儲存 (QEQS) 

  - 案例3d：無訊息簽出

  - 案例3e：復原簽出

- [測試區域 4：簽入](../../extensibility/internals/test-area-4-check-in.md)

  - 案例4a：修改的專案

  - 案例4b：新增檔案

  - 案例4c：加入專案

- [測試區域 5：變更原始檔控制](../../extensibility/internals/test-area-5-change-source-control.md)

  - 案例5a：系結

  - 案例5b：解除系結

  - 案例5c：重新綁定

- [測試區域 6：刪除](../../extensibility/internals/test-area-6-delete.md)

- [測試區域 7：共用](../../extensibility/internals/test-area-7-share.md)

- [測試區域 8：外掛程式切換](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - 案例8a：自動變更

  - 案例8b：以方案為基礎的變更

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)
