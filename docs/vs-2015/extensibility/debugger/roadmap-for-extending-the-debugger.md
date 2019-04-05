---
title: 擴充偵錯工具藍圖 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f8c5995de05d5861ff407006d5926081a5b76c8b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941555"
---
# <a name="roadmap-for-extending-the-debugger"></a>擴充偵錯工具的藍圖
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

這份文件提供用於擴充的指南和參考資訊[!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)]偵錯工具與[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 偵錯文件包含範例、 完整的參考，並示範一般的方式來自訂偵錯工具的幾個代表性案例。  
  
 您的編譯器和其輸出決定您要如何實作您的產品中的偵錯。 如果您的編譯器：  
  
-   以 Windows 原生作業系統為目標，並將寫入。PDB 檔案中，您可以使用偵錯程式原生程式碼的偵錯引擎 (DE)，已整合至[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 您不需要實作 DE 或運算式的評估工具。 運算式評估工具是針對 c + + 程式設計語言的語法所撰寫。  
  
-   產生的 Microsoft intermediate language (MSIL) 的輸出，您可以使用 managed 程式碼的偵錯引擎 DE，這也會整合到偵錯程式[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 因此，您只需要實作的運算式評估工具。 為您提供的範例運算式評估工具。 如需詳細資訊，請參閱下列主題：  
  
     [運算式評估](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [評估運算式](../../extensibility/debugger/evaluating-expressions.md)  
  
     [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [中斷模式中的運算式評估](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [撰寫 Common Language Runtime 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   作業系統或某些其他執行階段環境的專屬的目標，您需要撰寫您自己的裝置。 建立簡單的規定，使用 ATL COM 的教學課程會提供。 如需詳細資訊，請參閱下列主題：  
  
     [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [教學課程：建置使用 ATL COM 偵錯引擎](http://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [實作連接埠提供者](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [範例](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
