---
title: 圖形畫面格驗證 |Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2add8032a1fa5da983c66ab5cfabede78f4c65c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891770"
---
# <a name="graphics-frame-validation"></a>圖形畫面格驗證
<!-- VERSIONLESS --> Visual Studio 2017 和更新版本支援**框架驗證**工具。  [畫面格驗證] 視窗會顯示錯誤和事件清單相關聯的警告。  若要檢視此視窗，請選取**檢視 > 畫面格驗證**功能表。

![框架驗證](media/gfx_diag_frame_validation.png)

按一下 **執行驗證**在起始分析左上角的按鈕。  可能需要幾分鐘才能完成，視框架的複雜度而定。  會出現下面是結合來自兩個來源的資料： 訊息的 D3D 本身會時發出[SDK 層](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers)啟用時，和收集自追蹤工具自己的內部狀態的資料。 完成後，您會看到多個資料行：


| **資料行** | **描述** |
|------------| - |
| 事件 ID | 這會對應到中的項目 ID[事件清單](graphics-event-list.md)視窗。 |
| 嚴重性 | 損毀、 錯誤、 警告、 資訊或訊息。 |
| 分類 | 應用程式定義的其他、 初始化、 清理、 編譯、 狀態建立、 狀態設定、 狀態開始，執行、 資源操作、 著色器、 重複、 也未使用。 |
| 訊息 | 與事件相關聯的訊息。 |
| Event - 事件 | 相關聯的錯誤或警告事件。 |

## <a name="see-also"></a>請參閱  
[圖形診斷 (偵錯 DirectX 圖形)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->