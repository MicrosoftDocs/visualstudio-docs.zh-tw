---
title: 編輯後繼續 (Visual C#) |Microsoft Docs
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Edit and Continue
- Edit and Continue [C#]
- debugging [C#], Edit and Continue
ms.assetid: 591bd1b7-ef10-4d10-817b-3f92ca4be006
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 972ad0d772eee9b876f43bc3e2fcd032d4b7e0ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851014"
---
# <a name="edit-and-continue-visual-c"></a>編輯後繼續 (Visual C#)
 利用 C# 的 [編輯後繼續]，偵錯時您可以在中斷模式中變更程式碼。 不需要停止並重新啟動偵錯工作階段，就可以套用這些變更。 在執行模式中，原始檔編輯器是唯讀的。

 [編輯後繼續] 支援大部分您可能想要在偵錯工作階段期間進行的變更，但是有一些例外狀況。 如需詳細資訊，請參閱 <<c0> [ 支援的程式碼變更 (C#和 Visual Basic)](../debugger/supported-code-changes-csharp.md)。</c0>

 編輯後繼續支援 Windows 10 和.NET Framework 4.6 為目標的 x86 和 x64 應用程式中的 UWP 桌面或更新版本的版本 （.NET Framework 是僅限桌面版本）。

 > [!NOTE]
 > 不支援的應用程式與平台包含 ASP.NET 5、 Silverlight 5 和 Windows 8.1。

 啟用 [編輯後繼續] 時，當您使用偵錯工具執行命令 (例如 [繼續]、[逐步執行]、[設定下一個陳述式])，或在偵錯工具視窗中執行函式評估時，便會自動套用支援的變更。

 如需詳細資訊，請參閱[如何：使用編輯後繼續 (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)。

## <a name="see-also"></a>另請參閱
- [如何：使用編輯後繼續 (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [支援的程式碼變更 (C#和 Visual Basic)](../debugger/supported-code-changes-csharp.md)