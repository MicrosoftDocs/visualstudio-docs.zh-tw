---
title: "用於擴充偵錯工具藍圖 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af86f2b8daeffeb700b619c4ba0d9cbb00700dd8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="roadmap-for-extending-the-debugger"></a>用於擴充偵錯工具藍圖
這份文件提供用於擴充的指南和參考資訊[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]偵錯工具與[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯文件包含範例、 完整的參考及示範自訂偵錯工具的一般方法的幾個代表性案例。  
  
 編譯器和其輸出決定您需要如何做以您的產品中實作偵錯。 如果您的編譯器：  
  
-   以 Windows 原生作業系統為目標，並將寫入。PDB 檔案，您可以使用偵錯程式的原生程式碼偵錯引擎 (DE)，其中已整合至[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 您不需要實作 DE 或運算式評估工具。 運算式評估工具會寫入 c + + 程式設計語言的語法。  
  
-   產生的 Microsoft intermediate language (MSIL) 輸出，您可以使用 managed 程式碼的偵錯引擎 DE，也會整合至其偵錯程式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 因此，您只需要實作的運算式評估工具。 為您提供的範例運算式評估工具。 如需詳細資訊，請參閱下列主題：  
  
     [運算式評估](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [評估運算式](../../extensibility/debugger/evaluating-expressions.md)  
  
     [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [中斷模式中的運算式評估](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [撰寫 Common Language Runtime 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   您要撰寫您自己 DE 作業系統或其他的執行階段環境專屬的目標。 提供建立簡單的 DE 使用 ATL COM 的教學課程。 如需詳細資訊，請參閱下列主題：  
  
     [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [教學課程： 建立使用 ATL COM 偵錯引擎](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [實作連接埠提供者](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [範例](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)