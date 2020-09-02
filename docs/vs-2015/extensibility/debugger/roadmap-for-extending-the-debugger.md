---
title: 擴充偵錯工具的藍圖 |Microsoft Docs
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
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695964"
---
# <a name="roadmap-for-extending-the-debugger"></a>擴充偵錯工具的藍圖
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本檔提供使用擴充偵錯工具的指南和參考資訊 [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 偵錯工具檔包括範例、完整參考和數個代表性案例，示範自訂偵錯工具的一般方式。  
  
 您的編譯器和其輸出會決定在您的產品中執行偵錯工具所需執行的動作。 如果您的編譯器：  
  
- 以 Windows 原生作業系統為目標，並寫入。PDB 檔案，您可以使用原生程式碼的偵錯工具引擎來進行程式碼偵測引擎的 (DE) （整合至） [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 您不需要執行 DE 或運算式評估工具。 運算式評估工具是針對 c + + 程式設計語言的語法所撰寫的。  
  
- 產生 Microsoft 中繼語言 (MSIL) 輸出，您可以使用也整合至的 managed 程式碼偵測引擎 DE 來進行程式碼的偵錯工具 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 因此，您只需要執行運算式評估工具。 系統會為您提供範例運算式評估工具。 如需詳細資訊，請參閱下列主題：  
  
     [運算式評估](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [評估運算式](../../extensibility/debugger/evaluating-expressions.md)  
  
     [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [中斷模式中的運算式評估](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [撰寫 Common Language Runtime 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- 以專屬的作業系統或其他執行時間環境為目標，您必須自行撰寫 DE。 提供使用 ATL COM 建立簡單 DE 的教學課程。 如需詳細資訊，請參閱下列主題：  
  
     [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [教學課程：使用 ATL COM 建立 Debug Engine](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [實作連接埠提供者](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [範例](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
