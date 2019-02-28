---
title: COM 和 ActiveX 進行偵錯 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- COM, debugging
- debugging ActiveX applications
- debugging [Visual Studio], COM
- debugging COM containers
- ActiveX controls, debugging
ms.assetid: 3260b2a7-3239-493d-9271-aedf705c13c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b37522fec0438278f8cf063637132b146b3d3748
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609078"
---
# <a name="com-and-activex-debugging"></a>偵錯 COM 和 ActiveX
本章節提供有關偵錯 COM 應用程式和 ActiveX 控制項的秘訣。

## <a name="in-this-section"></a>本節內容
 [COM 伺服器和容器偵錯](../debugger/com-server-and-container-debugging.md)偵錯 COM 應用程式時，提及的特殊考量。 涉及的問題包含：在同一方案中使用兩個專案偵錯 COM 伺服器和容器 (Container)、跨處理序 (Process) 界限追蹤呼叫、設定回呼函式 (Callback Function) 的中斷點，以及逐步跨和進入容器和伺服器等的問題。

 [如何： 偵錯 ActiveX 控制項](../debugger/how-to-debug-an-activex-control.md)包含偵錯 ActiveX 控制項的相關資訊。 其中包括：指定偵錯工作階段的容器以查看您 ActiveX 控制項中的程式碼如何執行、偵錯資料繫結的 ActiveX 控制項、模擬特定的容器，以及逐步執行容器的程式碼。

 [COM 偵錯工具](../debugger/com-debugging-tools.md)列出檢視器和適用於偵錯 COM 應用程式的範例應用程式。

## <a name="related-sections"></a>相關章節
 [第一次查看偵錯工具](../debugger/debugger-feature-tour.md)提供較大的區段的 偵錯文件的連結。 這些資訊包括：偵錯工具的新功能、設定和準備、中斷點、例外狀況處理、編輯後繼續、Managed 程式碼的偵錯、Visual C++ 專案的偵錯、COM 和 ActiveX 的偵錯、DLL 偵錯、SQL 偵錯，以及使用者介面的參考。

## <a name="see-also"></a>請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [COM 簡介](/cpp/atl/introduction-to-com)
- [ActiveX 控制項](/cpp/mfc/activex-controls)
- [SDI 伺服器應用程式](../debugger/sdi-server-applications.md)