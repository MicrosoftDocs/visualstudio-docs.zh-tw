---
title: "舊版語言服務概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 05805e5cf4b21f4c7d233cab7dd8421ee76f626f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-language-service-overview"></a>舊版語言服務概觀
語言服務提供可讓您實作特定的編輯器支援[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能。 Managed Package Framework (MPF) 語言服務類別提供常用的功能和部分支援其他功能的完整支援。  
  
## <a name="fully-supported-features-in-the-mpf"></a>MPF 完全支援的功能  
 MPF 語言服務類別支援下列功能：  
  
-   語法醒目提示  
  
-   大綱  
  
-   註解的程式碼區塊  
  
-   括號對稱  
  
-   程式碼片段  
  
-   自訂文件屬性  
  
-   IntelliSense 參數資訊  
  
-   IntelliSense 快速諮詢  
  
-   IntelliSense 成員完成  
  
-   IntelliSense 文字自動完成  
  
## <a name="partially-supported-features-in-the-mpf"></a>MPF 部分支援的功能  
 MPF 提供下列功能僅部分支援。 這表示您必須實作 MPF 所呼叫的方法。  
  
-   重新格式化程式碼。 您提供實作重新格式化的程式碼。  
  
-   驗證識別有效的程式碼範圍的中斷點。 您提供識別程式碼範圍的程式碼。  
  
-   支援偵錯工具**自動變數**顯示變數視窗。 您提供的程式碼，決定要顯示在視窗中。  
  
-   支援**導覽列**的快速瀏覽不同的型別和成員。 實作，並傳回填入的清單中的協助程式類別**導覽列**下拉式方塊。  
  
## <a name="implementation"></a>實作  
 您必須完成數個步驟來實作語言服務本身和您想要支援您的語言的語言服務功能。 下列主題討論這些步驟：  
  
-   [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中製作大綱](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中將程式碼設為註解](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中將程式碼重新格式化](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [舊版語言服務中的自訂文件屬性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [舊版語言服務中對程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [舊版語言服務中對巡覽列的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [舊版語言服務中的文字自動完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [舊版語言服務中的成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [舊版語言服務中的快速諮詢](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [舊版語言服務中對自動變數視窗的支援](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中驗證中斷點](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>請參閱  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [舊版語言服務的擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)