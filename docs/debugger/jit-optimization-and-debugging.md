---
title: "JIT 最佳化和偵錯 |Microsoft 文件"
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
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: acf75c0fbf6f5c3cfcf645d288c4e5e2eb2450d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="jit-optimization-and-debugging"></a>JIT 最佳化和偵錯
當您偵錯 managed 應用程式，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]依預設會隱藏在 just-in-time (JIT) 程式碼的最佳化。 隱藏 JIT 最佳化表示您是在偵錯非最佳化的程式碼。 因為沒有最佳化，所以程式碼的執行速度較慢，但是您的偵錯經驗會更完整。 偵錯最佳化的程式碼更為困難，建議您只有在遇到發生於最佳化程式碼中的錯誤，又無法在非最佳化版本中重現錯誤時，才偵錯最佳化的程式碼。  
  
 在控制 JIT 最佳化[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]由**模組載入時隱藏 JIT 最佳化**選項。 您可以找到這個選項在**一般**頁面**偵錯**節點**選項** 對話方塊。  
  
 如果您清除**模組載入時隱藏 JIT 最佳化**選項，您可以偵錯最佳化的 JIT 程式碼，但是因為最佳化程式碼不符合原始程式碼，偵錯功能可能會有所限制。 如此一來，偵錯工具視窗例如**區域變數**和**自動變數**視窗可能不會顯示最多的資訊，就像偵錯非最佳化的程式碼。  
  
 另一個重要的差異是關於使用 [Just My Code] 進行偵錯。 如果您使用 [Just My Code] 進行偵錯，偵錯工具會將最佳化程式碼視為在偵錯時不應該顯示的非使用者程式碼。 因此，如果您是偵錯 JIT 最佳化程式碼，可能需要關閉 [Just My Code]。 如需詳細資訊，請參閱[限制於 Just My Code 逐步執行](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)。  
  
 請記住，**模組載入時隱藏 JIT 最佳化**選項會在模組載入時隱藏程式碼的最佳化。 如果是附加至已在執行中的處理序，其中可能包含已經載入的、編譯為 JIT 以及最佳化的程式碼。 **模組載入時隱藏 JIT 最佳化**選項無效這類程式碼，雖然會影響在附加後載入的模組。 此外，**模組載入時隱藏 JIT 最佳化**選項不會影響模組，例如 WinForms.dll 使用 NGEN 建立的。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)   
 [附加至執行中處理程序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Managed 執行程序](/dotnet/standard/managed-execution-process)