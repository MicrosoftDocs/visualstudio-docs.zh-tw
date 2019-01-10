---
title: 編輯後繼續 (Visual Basic) |Microsoft Docs
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3e1305a67fa4347a8b39b677c5be31ada257b65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838017"
---
# <a name="edit-and-continue-visual-basic"></a>編輯後繼續 (Visual Basic)
「編輯後繼續」是 [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] 偵錯的一個功能，當程式碼在中斷模式中執行時，這項功能可讓您變更程式碼。 套用程式碼編輯之後，您可以繼續以新的編輯執行程式碼，並查看其效果。  
  
 只要進入中斷模式，隨時都可以使用編輯後繼續功能。 在中斷模式下，指令指標，在來源視窗中的黃色箭頭，指向包含在方法或屬性主體中將會執行陳述式的那一行會執行下一步。

 [編輯後繼續] 支援大部分您可能想要在偵錯工作階段期間進行的變更，但是有一些例外狀況。 如需詳細資訊，請參閱 <<c0> [ 支援的程式碼變更 (C#和 Visual Basic)](../debugger/supported-code-changes-csharp.md)。</c0>   
  
 當您進行未經授權的編輯時，會以紫色波浪底線標示這個變更，而且 [工作清單] 中會顯示工作。 如果您要繼續使用 [編輯後繼續]，必須復原未經授權的編輯。 如果在 [編輯後繼續] 以外進行某些未經授權的編輯，則可能會允許進行這些編輯。 如果您要保留這種未經授權的編輯結果，必須先停止偵錯並重新啟動應用程式。  
  
 編輯後繼續適用於 Windows 10 UWP 應用程式和支援 x86 和 x64.NET Framework 4.6 為目標的應用程式 （.NET Framework 是僅限桌面版本） 中，桌面或更新版本。

 > [!NOTE]
 > 不支援的應用程式與平台包含 ASP.NET 5、 Silverlight 5 和 Windows 8.1。
  
 當您使用 [附加至處理序] 開始偵錯時，並不支援 [編輯後繼續]。 編輯後繼續不支援最佳化程式碼或混合的 managed 和原生程式碼。 如需詳細資訊，請參閱 <<c0> [ 支援的程式碼變更 (C#和 Visual Basic)](../debugger/supported-code-changes-csharp.md)。</c0>
  
 本章節中的主題提供其他詳細資訊，說明使用這項功能的方法以及不允許進行的變更種類。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：以編輯後繼續在中斷模式中套用編輯](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 說明在中斷模式中套用程式碼編輯的方式。  
  
 [支援的程式碼變更 (C#和 Visual Basic)](../debugger/supported-code-changes-csharp.md)   
 描述哪些類型的編輯內容無法在 [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] [編輯後繼續] 中執行。  
  
## <a name="related-sections"></a>相關章節  
 [編輯後繼續](../debugger/edit-and-continue.md)  
 提供編輯後繼續的主題清單。
