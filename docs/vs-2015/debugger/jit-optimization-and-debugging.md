---
title: JIT 最佳化和偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb73c434c978f7a8b1847976c73fe2bff47e3b89
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497425"
---
# <a name="jit-optimization-and-debugging"></a>JIT 最佳化和偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[JIT 最佳化和偵錯](https://docs.microsoft.com/visualstudio/debugger/jit-optimization-and-debugging)。  
  
當您偵錯 managed 應用程式，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]依預設會隱藏在 just-in-time (JIT) 程式碼的最佳化。 隱藏 JIT 最佳化表示您是在偵錯非最佳化的程式碼。 因為沒有最佳化，所以程式碼的執行速度較慢，但是您的偵錯經驗會更完整。 偵錯最佳化的程式碼更為困難，建議您只有在遇到發生於最佳化程式碼中的錯誤，又無法在非最佳化版本中重現錯誤時，才偵錯最佳化的程式碼。  
  
 在控制 JIT 最佳化[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]所**隱藏 JIT 最佳化模組載入**選項。 您可以找到此選項**一般**頁面**偵錯**節點中的**選項** 對話方塊。  
  
 如果您清除**隱藏 JIT 最佳化模組載入**選項時，您可以偵錯最佳化的 JIT 程式碼，但偵錯功能可能有限，因為最佳化的程式碼不相符的原始碼。 如此一來，偵錯工具視窗這類**區域變數**並**自動變數**視窗可能不會顯示的資訊量就像您所偵錯非最佳化的程式碼。  
  
 另一個重要的差異是關於使用 [Just My Code] 進行偵錯。 如果您使用 [Just My Code] 進行偵錯，偵錯工具會將最佳化程式碼視為在偵錯時不應該顯示的非使用者程式碼。 因此，如果您是偵錯 JIT 最佳化程式碼，可能需要關閉 [Just My Code]。 如需詳細資訊，請參閱 <<c0> [ 限制於 Just My Code 逐步執行](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code)。  
  
 請記住**隱藏 JIT 最佳化模組載入**選項會在載入模組時，會隱藏程式碼的最佳化。 如果是附加至已在執行中的處理序，其中可能包含已經載入的、編譯為 JIT 以及最佳化的程式碼。 **隱藏 JIT 最佳化模組載入**選項都有這類程式碼中，不會影響，雖然會影響在附加後載入的模組。 颾魤 ㄛ**隱藏 JIT 最佳化模組載入**選項不會影響模組，例如 WinForms.dll，ngen 所建立。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)   
 [附加至執行中處理程序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Managed 執行程序](http://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)



