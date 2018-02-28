---
title: "圖形框架驗證 |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d349222b138a8d5c359d174849faf7641befc482
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-frame-validation"></a>圖形畫面格驗證
<!-- VERSIONLESS -->
Visual Studio 2017 和更佳的支援**框架驗證**工具。  驗證框架視窗會顯示錯誤和警告相關聯的事件清單。  若要檢視此視窗，請選取**檢視 > 框架驗證**功能表。

![框架驗證](media/gfx_diag_frame_validation.png)

按一下**執行驗證**在起始分析左上角的按鈕。  可能需要幾分鐘才能完成根據畫面格的複雜度。  會出現如下的組合來自兩個來源的資料： 訊息該 D3D 本身發出時[SDK 層](https://msdn.microsoft.com/library/windows/desktop/ff476881(v=vs.85).aspx)已啟用，並收集追蹤工具自己的內部狀態的資料。 完成後，您會看到數個資料行：

**資料行**|**描述**
---|---
事件 ID | 對應中的項目 ID[事件清單](graphics-event-list.md)視窗。
嚴重性 | 損毀、 錯誤、 警告、 資訊或訊息。
分類 | 應用程式定義的其他、 初始化、 清除、 編譯、 狀態建立、 狀態設定、 取得狀態、 執行、 資源管理、 著色器的備援性，以及未使用。
訊息 | 與事件相關聯的訊息。
Event - 事件 | 相關聯的錯誤或警告事件。

## <a name="see-also"></a>請參閱  
[圖形診斷 （偵錯 DirectX 圖形）](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->