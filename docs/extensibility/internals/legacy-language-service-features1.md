---
title: 舊版語言服務 Features1 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c931147d20454a920e20cec61e1f6000a9b043d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131728"
---
# <a name="legacy-language-service-features"></a>舊版語言服務功能
Managed 的封裝架構 (MPF) 語言服務可支援一或多個[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能，例如語法反白顯示、 IntelliSense 和中斷點驗證。 每項功能可以獨立於其他實作，但所有需要的剖析器和除了語法反白顯示，這需要掃描程式的掃描器。  
  
## <a name="in-this-section"></a>本節內容  
 [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 描述支援的語言組比對，也稱為括號對稱的必要條件。  
  
 [在舊版語言服務中將程式碼設為註解](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 描述什麼是用來支援註解和取消選取的程式碼的註解。  
  
 [舊版語言服務中的自訂文件屬性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 描述什麼是用來支援內嵌在原始程式檔中的文件屬性。  
  
 [在舊版語言服務中製作大綱](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 描述什麼是用來支援透過隱藏區域實作大綱。  
  
 [在舊版語言服務中將程式碼重新格式化](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 描述什麼是用來支援重新格式化程式碼。  
  
 [舊版語言服務中對程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 描述什麼是用來支援程式碼片段，也就是，會插入，且可供編輯的程式碼區段。  
  
 [在舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 描述什麼是用來支援顯示依照輸入方法的方法簽章的 IntelliSense 參數資訊作業。  
  
 [舊版語言服務中的快速諮詢](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 描述什麼是用來支援顯示識別項的相關資訊的 IntelliSense 快速諮詢作業。  
  
 [舊版語言服務中的成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 描述什麼才能支援從清單中選取命名空間成員的 IntelliSense 成員完成作業。  
  
 [舊版語言服務中的文字自動完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 描述什麼是用來支援 Intellisense 自動完成作業的完成齊部分輸入的文字。  
  
 [舊版語言服務中對自動變數視窗的支援](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 說明該語言服務如何支援**自動變數**您偵錯時的視窗。  
  
 [舊版語言服務中對巡覽列的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 描述如何使用**導覽列**橫跨頂端的編輯器檢視，以提供快速瀏覽至任何類型或成員中所示，在該檢視中的檔案...  
  
 [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 描述什麼是用來支援語法反白顯示的原始程式碼。  
  
 [在舊版語言服務中驗證中斷點](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 說明該語言服務如何支援驗證的中斷點，偵錯工具外部。  
  
## <a name="related-sections"></a>相關章節  
 [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 描述剖析器和實作使用 managed 的封裝架構的語言服務的所有功能所需的掃描器。  
  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 描述使用 MPF 實作語言服務的必要條件。  
  
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 描述使用 MPF 為基礎的語言服務登錄所需的步驟[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [使用 IntelliSense](../../ide/using-intellisense.md)  
 說明 IntelliSense 如何進行語言參考容易存取。  
  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 提供有關如何使用 managed 的 package framework (MPF) 來實作在 managed 程式碼的完整語言服務的資訊。