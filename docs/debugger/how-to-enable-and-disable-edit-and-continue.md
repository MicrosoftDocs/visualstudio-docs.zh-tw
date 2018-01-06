---
title: "如何： 啟用和停用編輯後繼續 （C#、 VB、 c + +） |Microsoft 文件"
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
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 1c00546b983c9bbb0fd6c01717bd0a09c993e11b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>如何： 啟用和停用編輯後繼續 （C#、 VB、 c + +）
您可以停用或啟用編輯後繼續中的**選項**在執行階段 對話方塊。 但是在進行偵錯時，無法變更這項設定。  
  
[編輯後繼續] 只能用於偵錯組建中。 在原生 C++ 中，[編輯後繼續] 必須使用 /INCREMENTAL 選項。 如需 c + + 中的功能需求的詳細資訊，請參閱此[部落格文章](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)和[編輯後繼續 （Visual c + +）](../debugger/edit-and-continue-visual-cpp.md)。
  
#### <a name="to-enabledisable-edit-and-continue"></a>若要啟用/停用編輯後繼續   
  
1.  如果您是在偵錯工作階段，停止偵錯 (**Shift + F5**)。

2.  開啟偵錯的 [選項] 頁面 (**工具 > 選項 > 偵錯**)。
  
3.  選取**一般**，向下捲動至**編輯後繼續**類別 （右窗格）。  
  
4.  若要啟用，請選取**啟用編輯後繼續**核取方塊。 若要停用，請清除該核取方塊。  
  
    > [!NOTE]
    >  如果已啟用 IntelliTrace，而且您同時收集 IntelliTrace 事件和呼叫資訊，則會停用 [編輯後繼續]。 如需詳細資訊，請參閱[IntelliTrace](../debugger/intellitrace.md)。

5. （C + +）若要啟用，請選取**啟用原生編輯後繼續**。 若要停用，請清除該核取方塊。

6. （C + +）設定原生程式碼的其他選項。

    - **將變更套用在繼續 （僅限原生）**  
        當從中斷狀態繼續處理序時，Visual Studio 會自動編譯和套用任何未完成的程式碼變更。 如果未選取，您可以選擇使用 [偵錯] 功能表底下的 [套用程式碼變更] 項目套用變更。  
  
    - **警告出現過時的程式碼 （僅限原生）**  
        取得過時程式碼的警告。 
  
7.  按一下 [確定 **Deploying Office Solutions**]。    
  
## <a name="see-also"></a>請參閱  
 [編輯後繼續](../debugger/edit-and-continue.md)