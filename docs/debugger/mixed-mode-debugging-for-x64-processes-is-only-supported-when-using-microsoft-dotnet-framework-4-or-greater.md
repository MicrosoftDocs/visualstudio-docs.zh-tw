---
title: 只有使用 Microsoft.NET Framework 4 或更新版本時才支援 x64 處理序的混合模式偵錯
description: 在第 4 版之前的 .NET Framework 版本沒有提供 x64 處理序的混合模式偵錯支援。 請參閱這篇文章以瞭解因應措施。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92ec1022842e44f9f87069c48d4de3259dcf8e99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913197"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>只有使用 Microsoft.NET Framework 4 或更新版本時才支援 x64 處理序的混合模式偵錯
在第 4 版之前的 .NET Framework 版本沒有提供 x64 處理序的混合模式偵錯支援。 這表示在偵錯時，您無法從 Managed 程式碼逐步執行到機器碼，或從機器碼逐步執行到 Managed 程式碼。

### <a name="workarounds"></a>因應措施

- 更新專案，以使用 Microsoft .NET Framework 4 (含) 以後版本。

     -或-

     在不同的偵錯工作階段中分別偵錯 Managed 程式碼和機器碼。

     -或-

     將混合程式碼當做 32 位元處理序來偵錯，如下列程序所述。

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>若要將平台變更為 32 位元 (Visual Basic 或 C#)

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按一下 [屬性]。

2. 在屬性頁中，按一下 [編譯] 或 [偵錯] 索引標籤。

3. 按一下 [平台]，並從平台清單中選取 [x86]。

     根據預設，Visual Basic 和 C# 編譯器會產生可在任何 CPU 上執行的程式碼。 在 64 位元電腦上，這些二進位檔會當做 64 位元處理序執行。 若要在 32 位元處理序上執行，您必須選擇 [Win32]，而非 [AnyCPU]。

### <a name="to-change-the-platform-to-32-bit-cc"></a>若要將平台變更為 32 位元 (C/C++)

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按一下 [屬性]。

2. 在屬性頁中，按一下 [ **平臺** ]，然後從平臺清單中選取 [Win32]。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請參閱 [設定 SQL 調試](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))。

## <a name="see-also"></a>另請參閱
- [Debug 64 位應用程式](../debugger/debug-64-bit-applications.md)