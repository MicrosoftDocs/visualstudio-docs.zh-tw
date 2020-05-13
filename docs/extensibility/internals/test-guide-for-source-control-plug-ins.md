---
title: 源代碼管理外掛程式測試指南 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: e6b3f8e76e977472a3459697a650b32dae657c22
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704382"
---
# <a name="test-guide-for-source-control-plug-ins"></a>原始檔控制外掛程式測試指南
本節提供有關使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]測試原始程式碼管理外掛程式的指導。 提供了最常見的測試區域以及一些可能有問題的更複雜的區域的廣泛概述。 此概述並非詳盡無遺地列出了測試用例。

> [!NOTE]
> 某些錯誤修復和對最新[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 的改進可能會發現現有原始程式碼管理外掛程式的問題,這些[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]問題以前在使用的早期版本時未遇到。 強烈建議您測試現有原始程式碼管理外掛程式的項目中列舉的區域,即使自以前的版本以來未對外掛[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]程式進行任何變更 。

## <a name="common-preparation"></a>常見準備
 需要安裝具有[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和目標源控制外掛程式的電腦。 第二台計算機類似配置,可用於某些開源控制測試。

## <a name="definition-of-terms"></a>字語定義
 在本測試指南中,請使用以下術語定義:

 用戶端專案 支援原始碼管理[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合的任何可用項目類型(例如[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)][!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)],[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]或 。

 Web 專案有四種類型的 Web 專案:檔案系統、本地 IIS、遠端網站和 FTP。

- 檔案系統專案是在本地路徑上創建的,但它們不需要安裝 Internet 資訊服務 (IIS),因為它們是透過 UNC 路徑在內部訪問的,並且可以從 IDE 內部置於原始碼管理之下,就像用戶端專案一樣。

- 本地 IIS 專案使用安裝在同一台電腦上的 IIS,並且使用指向本地電腦的 URL 進行訪問。

- 遠端網站項目也根據 IIS 服務創建,但它們被置於 IIS 伺服器電腦上的原始程式碼管理[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]之下,而不是從 IDE 內部。

- FTP 專案透過遠端 FTP 伺服器存取,但不能置於原始程式碼管理之下。

  登記原始程式碼管理下的解決方案或專案的另一個術語。

  版本存儲 正在透過原始程式碼管理外掛程式 API 存取的源碼管理資料庫。

## <a name="test-areas-covered-in-this-section"></a>本節涵蓋的測試區域

- [測試區域 1: 從原始碼管理新增/開啟](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - 案例 1a:向原始碼管理新增解決方案

  - 案例 1b:原始程式碼管理的開放解決方案

  - 案例 1c:從原始碼管理新增解決方案

- [測試區域 2︰從原始檔控制中取得](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [測試區域 3:簽出/復原簽出](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - 案例 3:簽出/撤銷簽出

  - 案例 3a:簽出

  - 案例 3b:已斷開連接結帳

  - 案例 3c:查詢編輯/查詢保存 (QEQS)

  - 案例 3d:靜默結帳

  - 案例 3e:撤銷簽出

- [測試區域 4︰簽入](../../extensibility/internals/test-area-4-check-in.md)

  - 案例 4a:修改的專案

  - 案例 4b:新增檔案

  - 案例 4c:新增專案

- [測試區域 5︰變更原始檔控制](../../extensibility/internals/test-area-5-change-source-control.md)

  - 案例 5a:綁定

  - 案例 5b:取消綁定

  - 案例 5c:重新綁定

- [測試區域 6︰刪除](../../extensibility/internals/test-area-6-delete.md)

- [測試區域 7︰共用](../../extensibility/internals/test-area-7-share.md)

- [測試區域 8︰外掛程式切換](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - 案例 8a:自動變更

  - 案例 8b:基於解決方案的變更

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)
