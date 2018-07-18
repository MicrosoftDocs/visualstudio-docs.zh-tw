---
title: 舊版語言服務 Essentials |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 68b92b821ad77b050ad2116da6fd930b975dad5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135441"
---
# <a name="legacy-language-service-essentials"></a>舊版語言服務 Essentials
您必須提供整合到 Visual Studio 程式設計語言的語言服務。 本主題說明可在舊版語言服務的功能。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要了解有關實作語言服務的新方法的詳細資訊，請參閱[編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
 舊版語言服務會提供下列功能：  
  
|功能|描述|  
|-------------|-----------------|  
|語法標色|會使編輯器檢視來顯示不同的色彩和字型樣式語言的不同項目。 區分可讓它更容易閱讀及編輯檔案。<br /><br /> 如需一般資訊，請參閱[語法著色舊版語言服務在](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。<br /><br /> Managed 的 package framework (MPF) 中的這項功能的相關資訊，請參閱[語法色彩標示在舊版語言服務](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。|  
|陳述式完成|完成陳述式或使用者已開始輸入關鍵字。 陳述式完成可協助使用者更輕鬆地輸入困難的陳述式，並輸入較少，較少的錯誤機會。<br /><br /> 如需一般資訊，請參閱[舊版語言服務中的陳述式完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。<br /><br /> MPF 這項功能的相關資訊，請參閱[舊版語言服務中的文字完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)。|  
|括號對稱|反白顯示配對字元，例如大括號。 當使用者輸入的結尾字元如"}"，大括號比對會反白顯示對應的開頭字元，例如"{"。 封入字元數個層級時，這項功能可協助使用者確認正確對應的封入的字元。<br /><br /> MPF 這項功能的相關資訊，請參閱[舊版語言服務中的大括號比對](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)。|  
|參數資訊工具提示|顯示一份可能的使用者目前正在輸入的多載方法的簽章。<br /><br /> 如需一般資訊，請參閱[參數資訊，以舊版語言服務](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。<br /><br /> MPF 這項功能的相關資訊，請參閱[參數資訊，以舊版語言服務](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)。|  
|錯誤標記|顯示波浪式紅色底線，也稱為曲線，底下的語法不正確的文字。 錯誤標記通常可用來讓使用者知道拼錯的關鍵字、 封閉的括號、 無效的字元，以及類似的錯誤。<br /><br /> 在 MPF 類別中，錯誤標記處理中自動<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>方法<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別。|  
  
 許多功能都需要語言服務剖析原始程式碼。 您通常可以重複使用 token 和剖析您的編譯器或解譯器的程式碼。  
  
 下列功能與程式語言的支援，但不語言服務的一部分：  
  
|功能|描述|  
|-------------|-----------------|  
|運算式評估工具|支援[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具透過驗證中斷點，並提供運算式的清單中顯示**自動變數**偵錯視窗。<br /><br /> 如需詳細資訊，請參閱[偵錯的語言服務支援](../../extensibility/internals/language-service-support-for-debugging.md)。|  
|符號瀏覽工具|支援**物件瀏覽器**，**類別檢視**，**呼叫瀏覽器**，和**尋找符號結果**。|