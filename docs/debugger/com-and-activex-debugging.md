---
title: COM 和 ActiveX 調試 |Microsoft Docs
description: 探索 Visual Studio 中的 COM 應用程式和 ActiveX 控制項的調試秘訣。 瞭解 COM 伺服器和容器的調試。 尋找 COM 調試工具。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f86f072a32bf9d7ff4af3c77564236fe2997f70a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865861"
---
# <a name="com-and-activex-debugging"></a>偵錯 COM 和 ActiveX
本章節提供有關偵錯 COM 應用程式和 ActiveX 控制項的秘訣。

## <a name="in-this-section"></a>本節內容
 [COM 伺服器和容器的調試](../debugger/com-server-and-container-debugging.md) 提及在偵測 COM 應用程式時的特殊考慮。 涉及的問題包含：在同一方案中使用兩個專案偵錯 COM 伺服器和容器 (Container)、跨處理序 (Process) 界限追蹤呼叫、設定回呼函式 (Callback Function) 的中斷點，以及逐步跨和進入容器和伺服器等的問題。

 [如何：對 ActiveX 控制項進行偵錯工具](../debugger/how-to-debug-an-activex-control.md) 包含有關調試 ActiveX 控制項的資訊。 其中包括：指定偵錯工作階段的容器以查看您 ActiveX 控制項中的程式碼如何執行、偵錯資料繫結的 ActiveX 控制項、模擬特定的容器，以及逐步執行容器的程式碼。

 [COM 調試工具](../debugger/com-debugging-tools.md) 列出可能有助於對 COM 應用程式進行偵錯工具的檢視器和範例應用程式。

## <a name="related-sections"></a>相關章節
 [開始查看偵錯工具](../debugger/debugger-feature-tour.md) 提供偵錯工具檔較大區段的連結。 資訊包括：偵錯工具的新功能、設定和準備、中斷點、處理例外狀況、編輯後繼續、偵測 managed 程式碼、偵錯工具 c + + 專案、偵測 COM 和 ActiveX、偵錯工具 Dll、偵錯工具，以及使用者介面參考。

## <a name="see-also"></a>另請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [COM 簡介](/cpp/atl/introduction-to-com)
- [ActiveX 控制項](/cpp/mfc/activex-controls)
- [SDI 伺服器應用程式](com-server-and-container-debugging.md)