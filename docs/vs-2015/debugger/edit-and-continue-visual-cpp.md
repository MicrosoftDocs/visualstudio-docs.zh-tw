---
title: 編輯後繼續 （Visual c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e1dc97af70f575632629a13ea67e905f2ad0815
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748356"
---
# <a name="edit-and-continue-visual-c"></a>Edit and Continue (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在 Visual C++ 專案中，使用 [編輯後繼續]。 請參閱[支援的程式碼變更 （c + +）](../debugger/supported-code-changes-cpp.md)如編輯後繼續的限制的相關資訊。  
  
 從 Visual Studio 2015 Update 1 開始，您現在可以使用 編輯後繼續在 Windows 市集 c + + 應用程式和 DirectX 應用程式，因為它現在支援 **/ZI**編譯器參數和 **/bigobj**切換。 您也可以使用編譯的二進位檔使用 編輯後繼續 **/FASTLINK**切換。  
  
 其他 Update 1 改進功能包括新的可取消等待對話方塊，以及當檔案不支援 [編輯後繼續] 時的通知。 如需有關 Update 1 改進功能的詳細資訊，請參閱[c + + 編輯後繼續在 Visual Studio 2015 Update 1 改進](http://blogs.msdn.com/b/vcblog/archive/2015/11/30/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1.aspx)。  
  
 [/Zo （增強最佳化偵錯）](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) Visual Studio 2013 Update 3 中導入的編譯器選項將額外資訊加入.pdb （符號） 檔案，而不需要編譯的二進位檔[/Od （停用 （偵錯））](http://msdn.microsoft.com/library/aafb762y.aspx)選項。  
  
 **/Zo**會停用編輯後繼續。 請參閱[如何： 偵錯最佳化程式碼](../debugger/how-to-debug-optimized-code.md)。  
  
##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> 啟用或停用編輯後繼續  
 如果您不希望在目前的偵錯工作階段中套用正在編輯的程式碼內容，您可能需要停用 [編輯後繼續] 的自動引動過程。 您也可以重新啟用自動的 [編輯後繼續]。  
  
1. 在 [ **工具** ] 功能表上選擇 [ **選項**]。  
  
2. 在 [選項]  對話方塊中，選取 [偵錯/一般] 。  
  
3. 在 [編輯後繼續]  群組中，選取或清除 [啟用原生編輯後繼續]  核取方塊。  
  
   修改這個設定會影響您處理的所有專案。 變更這個設定之後不需要重建應用程式。 即使在進行偵錯時，也可以變更設定。 如果您從命令列或 makefile 建置應用程式，但是在 Visual Studio 環境中進行偵錯，只要您設定了 **/ZI** 選項，就仍然可以使用 [編輯後繼續]。  
  
##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a> 如何明確套用程式碼變更  
 在 Visual C++ 中，[編輯後繼續] 會以兩種方式套用程式碼變更。 當您選擇執行命令時，會隱含地套用程式碼變更，而您使用 [ **套用程式碼變更** ] 命令時，則會明確套用程式碼變更。  
  
 當您明確套用程式碼變更，而程式仍處於中斷模式時，則不會執行。  
  
-   若要明確套用程式碼變更，請在 [偵錯]  功能表上，選擇 [套用程式碼變更] 。  
  
##  <a name="BKMK_How_to_stop_code_changes"></a> 如何停止程式碼變更  
 當 [編輯後繼續] 正在套用程式碼變更時，您可以停止該作業。  
  
 若要停止套用程式碼變更：  
  
- 在 [偵錯]  功能表上，選擇 [停止套用程式碼變更] 。  
  
  只有套用程式碼變更時，才能看見這個功能表項目。  
  
  如果您選擇此選項，就無法認可任何的程式碼變更。  
  
##  <a name="BKMK_How_to_reset_the_point_of_execution"></a> 如何重設執行點  
 某些程式碼變更會在 [編輯後繼續] 套用該變更時，造成執行點移至新位置。 [編輯後繼續] 會盡量精確地放置執行點，但有時結果未必完全正確。  
  
 在 Visual C++ 中，當執行點變更時，會出現一個對話方塊通知您。 您應該先確認位置是否正確，再繼續偵錯。 如果位置不正確，請使用 [ **設定下一個陳述式** ] 命令。 如需詳細資訊，請參閱 [設定下一個要執行的陳述式](http://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute)。  
  
##  <a name="BKMK_How_to_work_with_stale_code"></a> 如何使用過時程式碼  
 在某些情況下，[編輯後繼續] 不能立即將程式碼變更套用至執行檔，但是如果您繼續偵錯或許能在稍後套用程式碼變更。 如果您編輯呼叫目前函式的函式，或將 64 位元組以上的新變數加入至呼叫堆疊上的某個函式時，就會發生這種情況。  
  
 在上述情形中，偵錯工具會繼續執行原始的程式碼直到套用變更為止。 過時程式碼會在不同的來源視窗中顯示為暫時原始程式檔視窗，並使用像是 `enc25.tmp`的標題。 已編輯的來源會繼續出現在原始來源視窗中。 如果您嘗試編輯過時程式碼，就會出現警告訊息。  
  
## <a name="see-also"></a>另請參閱  
 [支援的程式碼變更 (C++)](../debugger/supported-code-changes-cpp.md)



