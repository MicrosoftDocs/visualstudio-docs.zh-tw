---
title: 圖形畫面格驗證 |Microsoft Docs
description: 瞭解 Visual Studio 中圖形的畫面格驗證工具。 此工具會顯示與事件清單相關聯的錯誤和警告。
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d52d04565b03d988d5d01a64e561fc0da8a16e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885244"
---
# <a name="graphics-frame-validation"></a>圖形畫面格驗證
<!-- VERSIONLESS -->
Visual Studio 2017 及更高版本的支援 **畫面格驗證** 工具。  [畫面格驗證] 視窗會顯示與事件清單相關聯的錯誤和警告。  若要查看這個視窗，請選取 [ **> 畫面格驗證** ] 功能表上的 [視圖]。

![框架驗證](media/gfx_diag_frame_validation.png)

按一下左上角的 [ **執行驗證** ] 按鈕，以起始分析。  這可能需要幾分鐘的時間才能完成，視框架的複雜度而定。  此處所顯示的資料是來自兩個來源的組合：當啟用 [SDK 層](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) 時，D3D 本身會發出的訊息，以及從工具本身的內部狀態追蹤收集的資料。 完成之後，您會看到數個數據行：

| **資料行** | **說明** |
|------------| - |
| 事件識別碼 | 對應到 [事件清單](graphics-event-list.md) 視窗中專案的識別碼。 |
| 嚴重性 | 損毀、錯誤、警告、資訊或訊息。 |
| 類別 | 應用程式定義、其他、初始化、清除、編譯、狀態建立、狀態設定、狀態取得、執行、資源操作、著色器、多餘和未使用。 |
| 訊息 | 與事件關聯的訊息。 |
| 事件 | 與錯誤或警告相關聯的事件。 |

## <a name="see-also"></a>另請參閱
[圖形診斷 (對 DirectX 圖形進行偵錯)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->