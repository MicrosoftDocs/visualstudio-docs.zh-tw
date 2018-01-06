---
title: "如何： 使用編輯後繼續 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: fe77428d1d9cfb5ff12554e87ec9afe15d6c86b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-edit-and-continue-c"></a>如何：使用編輯後繼續 (C#)
利用 C# 的 [編輯後繼續]，偵錯時您可以在中斷模式中變更程式碼。 不需要停止並重新啟動偵錯工作階段，就可以套用這些變更。  
  
 編輯後繼續] 會自動叫用您在中斷模式中進行變更，然後選擇 [偵錯工具執行命令，例如**繼續**，**步驟**，或**設定下一個陳述式**，或評估在偵錯工具視窗中的函式。  
  
> [!NOTE]
>  偵錯最佳化程式碼、 混合的原生程式碼或 SQL Server common language runtime (CLR) 整合程式碼時，不支援編輯後繼續。 如需其他不支援的案例，請參閱[（C# 和 Visual Basic），支援程式碼變更](../debugger/supported-code-changes-csharp.md)。 如果您嘗試套用程式碼變更，在這些案例中，偵錯工具會顯示一個對話方塊說明，編輯後繼續 不支援的其中一個。  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>若要叫用 編輯後自動繼續  
  
1.  在中斷模式，請對原始程式碼進行變更。  
  
2.  從**偵錯**功能表上，按一下 **繼續**，**步驟**，或**設定下一個陳述式**或評估在偵錯工具視窗中的函式。  
  
     新的程式碼會編譯和偵錯會繼續進行新的程式碼。 編輯後繼續不支援某些變更。 如需詳細資訊，請參閱[（C# 和 Visual Basic），支援程式碼變更](../debugger/supported-code-changes-csharp.md)。  
  
### <a name="to-enabledisable-edit-and-continue"></a>若要啟用/停用編輯後繼續   
  
1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2.  在**選項**對話方塊方塊中，展開 **偵錯**節點，然後選取**編輯後繼續**。  
  
3.  在**選項**對話方塊**編輯後繼續**頁面上，選取或清除**啟用編輯後繼續**核取方塊。  
  
     當您重新啟動偵錯工作階段，設定會生效。  
  
## <a name="see-also"></a>請參閱  
 [編輯後繼續 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [支援的程式碼變更 （C# 和 Visual Basic）](../debugger/supported-code-changes-csharp.md)   