---
title: 混合的模式偵錯時，才支援使用 Microsoft.NET Framework 2.0 或 3.0 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 827d3c5fcc625601019d6cbf61cdbf7c771b63b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929863"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>只有使用 Microsoft .NET Framework 2.0 或 3.0 版本時才支援混合模式偵錯
在 2.0 版之前的 Microsoft .NET Framework 沒有提供 64 位元處理序的混合模式偵錯支援。 這表示在偵錯時，您無法從 Managed 程式碼逐步執行到機器碼，或從機器碼逐步執行到 Managed 程式碼。

 若要解決這個問題，您可以：

- 更新專案，以使用 Microsoft .NET Framework 2.0 或 3.0。

- 在不同的偵錯工作階段中分別偵錯 Managed 程式碼和機器碼。

- 將混合程式碼當做 32 位元處理序來偵錯，如下列程序所述。

### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>若要將作業系統變更為 32 位元 (Visual Basic 或 C#)

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按一下捷徑功能表中的 [屬性]。

2. 在屬性頁中，按一下 [編譯] 或 [偵錯] 索引標籤。

3. 按一下 [平台]，然後從平台清單選取 [x86]。

     根據預設，Visual Basic 和 C# 編譯器會產生可針對任何 CPU 執行的程式碼。 在 64 位元電腦上，這些二進位檔會當做 64 位元處理序執行。 若要在 32 位元處理序上執行，您必須選擇 [Win32]，而非 [AnyCPU]。

### <a name="to-change-the-operating-system-to-32-bit-cc"></a>若要將作業系統變更為 32 位元 (C/C++)

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按一下捷徑功能表中的 [屬性]。

     在屬性頁中，按一下 [平台]，然後從平台清單選取 [Win32]。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請參閱[設定 SQL 偵錯](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))。

## <a name="see-also"></a>另請參閱
- [偵錯 64 位元應用程式](../debugger/debug-64-bit-applications.md)