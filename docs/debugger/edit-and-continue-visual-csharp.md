---
title: 'Visual c # ) 的 [編輯後繼續] (|Microsoft Docs'
description: 'Visual c # 專案可使用 [編輯後繼續]。 瞭解哪些是支援的編輯，以及如何控制是否以及何時套用您的編輯。'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 55406001e4017c853895002445d9bd5d614b4b20
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862876"
---
# <a name="edit-and-continue-visual-c"></a>編輯後繼續 (Visual C#)
 利用 C# 的 [編輯後繼續]，偵錯時您可以在中斷模式中變更程式碼。 不需要停止並重新啟動偵錯工作階段，就可以套用這些變更。 在執行模式中，原始檔編輯器是唯讀的。

 [編輯後繼續] 支援大部分您可能想要在偵錯工作階段期間進行的變更，但是有一些例外狀況。 如需詳細資訊，請參閱 [ (c # 和 Visual Basic) 支援的程式碼變更 ](../debugger/supported-code-changes-csharp.md)。

 Windows 10 中的 UWP 支援 [編輯後繼續]，而以 .NET Framework 4.6 desktop 或更新版本為目標的 x86 和 x64 應用程式 (.NET Framework 是僅) 桌上出版本。

 > [!NOTE]
 > 不支援的應用程式和平臺包括 Silverlight 5，以及 Windows 8.1。

 啟用 [編輯後繼續] 時，當您使用偵錯工具執行命令 (例如 [繼續]、[逐步執行]、[設定下一個陳述式])，或在偵錯工具視窗中執行函式評估時，便會自動套用支援的變更。

 如需詳細資訊，請參閱 [如何：使用編輯後繼續 (c # ) ](../debugger/how-to-use-edit-and-continue-csharp.md)。

## <a name="see-also"></a>另請參閱
- [如何：使用編輯後繼續 (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [ (c # 和 Visual Basic 支援的程式碼變更) ](../debugger/supported-code-changes-csharp.md)
- [使用 XAML 熱重新載入在 Visual Studio 中撰寫和偵測執行中的 XAML 程式碼](../xaml-tools/xaml-hot-reload.md)
