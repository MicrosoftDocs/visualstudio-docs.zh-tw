---
title: 編輯後繼續錯誤訊息對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 06/22/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 01cd34aacb4abea5f2f3ce29fcb53ba34aaeaf21
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2018
---
# <a name="edit-and-continue-error-message-dialog-box"></a>編輯後繼續錯誤訊息對話方塊
您的語言支援 [編輯後繼續]，偵錯時，會出現此對話方塊，但**編輯後繼續**不適用於您所做的程式碼變更的類型。 方塊內的錯誤訊息會提供更詳細的說明。 出現這個對話方塊的可能原因包括：  

-   您嘗試編輯 SQL Server 程式碼。

-   您嘗試編輯最佳化程式碼。 （您可能需要從發行的組建切換至偵錯組建）。

-   您嘗試編輯的程式碼正在執行時 (而不是暫停偵錯工具時)。 再試一次[設定中斷點](../debugger/using-breakpoints.md)和編輯程式碼時暫停。

-   您嘗試在已啟用 Unmanaged 偵錯時編輯 Managed 程式碼。 編輯後繼續不適用於[混合模式偵錯](../debugger/how-to-debug-in-mixed-mode.md)。

-   您的程式設計語言中不支援編輯後繼續進行程式碼變更。 如需詳細資訊，請參閱主題中的不受支援的程式碼變更[C#](../debugger/supported-code-changes-csharp.md)， [Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)，和[c + +](../debugger/supported-code-changes-cpp.md)。
  
-   您嘗試編輯程式碼中的程式，而不是啟動從附加至**偵錯**功能表。  
  
-   您嘗試在下列項目進行偵錯時編輯程式碼：Dr.Watson 傾印。  
  
-   您嘗試編輯之後，發生未處理例外狀況的程式碼和選項"**回溯呼叫堆疊上未處理例外狀況**「 未選取。  
  
-   您嘗試在進行內嵌執行階段應用程式偵錯時編輯程式碼。
  
-   您嘗試編輯 managed 程式碼使用.NET Framework 4.5.1 之前, 的版本，而目標為 64 位元應用程式。 如果要使用 [編輯後繼續]，就必須將目標設定為 x86  (*projectname* **屬性**，**編譯**索引標籤上，**進階編譯器**設定。)。  
  
-   您嘗試在已於偵錯期間修改且已重新載入的組譯碼中編輯程式碼。  
  
-   您嘗試編輯尚未載入之組譯碼中的程式碼。  
  
-   您已開始偵錯舊版的應用程式 (因為新版本有建置錯誤)。
  
## <a name="uielement-list"></a>UIElement 清單  
 **[確定]**  
 結束對話方塊，並取消緊接在前的編輯嘗試。  
  
## <a name="see-also"></a>請參閱  
 [C + + 編輯後繼續部落格文章](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
 [支援的程式碼變更 (C++)](../debugger/supported-code-changes-cpp.md)