---
title: 參考 (程式設計捕獲) |Microsoft Docs
description: 使用程式設計捕獲 API，以程式設計方式控制圖形診斷的捕捉功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30cf44d6d16da46e9d6f08ffae4971d35136db58
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996106"
---
# <a name="reference-programmatic-capture"></a>參考 (程式設計擷取)
透過程式設計擷取應用程式開發介面，圖形診斷支援以程式設計方式控制其擷取功能。 您可以使用這個應用程式開發介面，在圖形診斷抬頭顯示器 (HUD) 切換並加入訊息、初始化和建立圖形記錄檔，以及擷取圖形資訊。

## <a name="programmatic-capture-apis"></a>程式設計擷取應用程式開發介面

### <a name="classes"></a>類別

|名稱|描述|
|----------|-----------------|
|[VsgDbg 類別](vsgdbg-class.md)|表示以程式設計方式控制圖形診斷應用程式內部元件的介面。|

### <a name="preprocessor-symbols"></a>前置處理器符號

|名稱|描述|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|出現時，定義圖形記錄檔是否儲存到使用者的暫存檔目錄。|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|定義圖形記錄檔的預設檔案名稱。|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|出現時，定義是否提供 `VsgDbg` 類別的預設執行個體。|

## <a name="related-articles"></a>相關文章

| 標題 | 描述 |
| - | - |
| [擷取圖形資訊](capturing-graphics-information.md) | 示範如何從 DirectX 應用程式擷取圖形資訊，以便使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 圖形診斷工具來診斷轉譯問題。 |
| [概觀](overview-of-visual-studio-graphics-diagnostics.md) | 示範圖形診斷如何協助您偵錯 DirectX 遊戲和應用程式的轉譯錯誤。 |
