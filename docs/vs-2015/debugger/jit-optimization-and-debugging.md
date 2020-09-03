---
title: JIT 優化和調試 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56b010a01ccd7e40e696653e13dd7c972c97a9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690543"
---
# <a name="jit-optimization-and-debugging"></a>JIT 最佳化和偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您進行 managed 應用程式的偵錯工具時， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 預設會隱藏優化的即時 (JIT) 程式碼。 隱藏 JIT 最佳化表示您是在偵錯非最佳化的程式碼。 因為沒有最佳化，所以程式碼的執行速度較慢，但是您的偵錯經驗會更完整。 偵錯最佳化的程式碼更為困難，建議您只有在遇到發生於最佳化程式碼中的錯誤，又無法在非最佳化版本中重現錯誤時，才偵錯最佳化的程式碼。  
  
 JIT 優化的控制方式是在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **模組載入選項上隱藏 jit 優化** 。 您可以在 [**選項**] 對話方塊中 [**調試**] 節點下的 [**一般**] 頁面上找到這個選項。  
  
 如果您清除 [ **模組載入時隱藏 JIT 優化** ] 選項，就可以將優化的 jit 程式碼進行優化，但您的 debug 能力可能會受到限制，因為優化的程式碼不符合原始程式碼。 如此一來，偵錯工具視窗（例如 [區域變數 **] 和**[自動**變數**] 視窗）可能不會像您錯非優化程式碼一樣顯示最多的資訊。  
  
 另一個重要的差異是關於使用 [Just My Code] 進行偵錯。 如果您使用 [Just My Code] 進行偵錯，偵錯工具會將最佳化程式碼視為在偵錯時不應該顯示的非使用者程式碼。 因此，如果您是偵錯 JIT 最佳化程式碼，可能需要關閉 [Just My Code]。 如需詳細資訊，請參閱  [將逐步執行限制于 Just My Code](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code)。  
  
 請記住，當模組載入時， **隱藏 JIT 優化 on 模組載入** 選項會隱藏程式碼的優化。 如果是附加至已在執行中的處理序，其中可能包含已經載入的、編譯為 JIT 以及最佳化的程式碼。 [ **模組載入時隱藏 JIT 優化** ] 選項不會影響這類程式碼，不過它會影響附加之後載入的模組。 此外，[ **模組載入時隱藏 JIT 優化** ] 選項不會影響使用 NGEN 建立的模組（例如 WinForms.dll）。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 程式碼的偵錯工具](../debugger/debugging-managed-code.md)   
 [使用偵錯工具流覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)   
 [附加至正在執行的進程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Managed 執行進程](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
