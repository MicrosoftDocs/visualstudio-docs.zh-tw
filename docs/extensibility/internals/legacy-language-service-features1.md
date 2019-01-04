---
title: 舊版語言服務功能 1 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0580e9a7482e6de7403de8fca6c6b33fdbaa6ded
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830440"
---
# <a name="legacy-language-service-features"></a>舊版語言服務功能
Managed 的封裝架構 (MPF) 語言服務可支援一或多個[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能，例如語法醒目提示、 IntelliSense 和中斷點驗證。 獨立於其他實作每個功能，但所有需要剖析器和語法反白顯示，除了需要掃描程式掃描程式。  
  
## <a name="in-this-section"></a>本節內容  
 [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 描述支援的語言組比對，也就大括號比對的必要條件。  
  
 [在舊版語言服務中將程式碼設為註解](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 描述需要支援註解和取消註解選取的程式碼的哪些項目。  
  
 [舊版語言服務中的自訂文件屬性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 說明什麼是用來支援在原始程式檔中內嵌的文件屬性。  
  
 [在舊版語言服務中製作大綱](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 說明什麼是用來支援透過隱藏區域的大綱。  
  
 [在舊版語言服務中將程式碼重新格式化](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 說明什麼是用來支援重新格式化程式碼。  
  
 [舊版語言服務中對程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 說明什麼是支援的插入，而且可以編輯程式碼區段的程式碼片段所需。  
  
 [舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 說明什麼是用來支援 IntelliSense 參數資訊 」 作業，來顯示方法簽章，依照輸入的方法。  
  
 [舊版語言服務中的快速諮詢](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 說明什麼是用來支援 IntelliSense 快速諮詢作業顯示識別項的相關資訊。  
  
 [舊版語言服務中的成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 描述項目，才能支援從清單中選取的命名空間成員的 IntelliSense 成員自動完成作業。  
  
 [舊版語言服務中的文字自動完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 說明什麼是用來支援 Intellisense 自動完成作業完成部分輸入的文字。  
  
 [舊版語言服務中對自動變數視窗的支援](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 描述的語言服務可執行以支援**自動變數**視窗時進行偵錯。  
  
 [舊版語言服務中對巡覽列的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 描述如何使用**瀏覽列**頂端的 [編輯器] 檢視提供快速瀏覽至任何類型或成員在該檢視中顯示的檔案...  
  
 [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 描述支援的原始碼的語法反白顯示的必要條件。  
  
 [在舊版語言服務中驗證中斷點](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 說明語言服務可以支援驗證的中斷點，偵錯工具之外。  
  
## <a name="related-sections"></a>相關章節  
 [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 描述實作使用 managed 的封裝架構的語言服務的所有功能所需的掃描器與剖析器。  
  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 描述使用 MPF 實作語言服務的必要條件。  
  
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 描述的步驟，才能註冊使用 MPF 型語言服務[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [使用 IntelliSense](../../ide/using-intellisense.md)  
 說明 IntelliSense 如何使語言參考，輕鬆地存取。  
  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 提供有關如何使用 managed 的 package framework (MPF) 來實作 managed 程式碼中的功能完整的語言服務的資訊。