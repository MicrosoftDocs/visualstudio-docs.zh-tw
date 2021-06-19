---
title: 以編輯後繼續在中斷模式中套用編輯 |Microsoft Docs
description: 瞭解如何使用 [編輯後繼續] 在中斷模式中編輯您的 Visual Basic 程式碼。 有多種方式可進入中斷模式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e62c6a7a6e30bac6d054f3e5484498047426d96d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386796"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>如何：使用編輯後繼續在中斷模式中套用編輯 (Visual Basic) 
您可以在中斷模式中使用 [編輯後繼續] 編輯程式碼，並繼續進行而不需停止及重新啟動執行。

如需在偵錯工具中使用 [編輯後繼續] 的限制，請參閱支援的程式 [代碼變更 (c # 和 Visual Basic) ](../debugger/supported-code-changes-csharp.md)。

### <a name="to-edit-code-in-break-mode"></a>在中斷模式中編輯程式碼

1. 執行下列其中一種方法進入中斷模式

    - 在程式碼中設定中斷點，然後從 [偵錯] 功能表中選擇 [開始偵錯]，並等待應用程式叫用中斷點。

         -或-

    - 開始偵錯，然後從 [偵錯] 功能表中選取 [全部中斷]。

         -或-

    - 發生例外狀況時，請在 [例外狀況 **助理**] 上選擇 [**啟用編輯**]。

2. 進行任何想要和支援的程式碼變更。

     如需詳細資訊，請參閱 [ (c # 和 Visual Basic) 支援的程式碼變更 ](../debugger/supported-code-changes-csharp.md)。

    > [!NOTE]
    > 如果您嘗試進行 [編輯後繼續] 不允許的程式碼變更，您的編輯會被加上紫色波浪線，而且 [工作清單] 中會出現工作。 除非您復原不合法的程式碼變更，否則將無法繼續執行程式碼。

3. 在 [偵錯] 功能表上，按一下 [繼續] 以恢復執行。

     這時程式碼便會一併執行您套用至專案的編輯。

## <a name="see-also"></a>另請參閱
- [ (c # 和 Visual Basic 支援的程式碼變更) ](../debugger/supported-code-changes-csharp.md)
- [編輯後繼續 (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
