---
title: 編輯後繼續（Visual C#） |Microsoft Docs
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
ms.openlocfilehash: 5d54673ee46c594bd1a4bea2990d3b9bbe90ce1f
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188198"
---
# <a name="edit-and-continue-visual-c"></a>編輯後繼續 (Visual C#)
 利用 C# 的 [編輯後繼續]，偵錯時您可以在中斷模式中變更程式碼。 不需要停止並重新啟動偵錯工作階段，就可以套用這些變更。 在執行模式中，原始檔編輯器是唯讀的。

 [編輯後繼續] 支援大部分您可能想要在偵錯工作階段期間進行的變更，但是有一些例外狀況。 如需詳細資訊，請參閱[支援的C#程式碼變更（和 Visual Basic）](../debugger/supported-code-changes-csharp.md)。

 Windows 10 中的 UWP 和以 .NET Framework 4.6 desktop 或更新版本為目標的 x86 和 x64 應用程式支援 [編輯後繼續] （.NET Framework 僅限桌上出版）。

 > [!NOTE]
 > 不支援的應用程式和平臺包括 ASP.NET 5、Silverlight 5 和 Windows 8.1。

 啟用 [編輯後繼續] 時，當您使用偵錯工具執行命令 (例如 [繼續]、[逐步執行]、[設定下一個陳述式])，或在偵錯工具視窗中執行函式評估時，便會自動套用支援的變更。

 如需詳細資訊，請參閱[如何：使用編輯後繼續C#（）](../debugger/how-to-use-edit-and-continue-csharp.md)。

## <a name="see-also"></a>請參閱
- [如何：使用編輯後繼續 (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [支援的程式碼C#變更（和 Visual Basic）](../debugger/supported-code-changes-csharp.md)
- [在 Visual Studio 中使用 XAML 熱重載來撰寫和偵測執行中的 XAML 程式碼](../xaml-tools/xaml-hot-reload.md)
