---
title: 舊版語言服務的基本資訊 |Microsoft Docs
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
ms.openlocfilehash: 344a7949c5058237d8599d69ea3b234e9a6e8e72
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850165"
---
# <a name="legacy-language-service-essentials"></a>舊版語言服務的基本資訊
您必須提供語言服務以整合到 Visual Studio 的程式設計語言。 本主題說明在舊版語言服務中可用的功能。  

 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解實作語言服務的新方式，請參閱[編輯器和語言服務延伸模組](../../extensibility/editor-and-language-service-extensions.md)。  

> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  

 舊版語言服務提供下列功能：  

|功能|描述|  
|-------------|-----------------|  
|語法標色|會導致編輯器檢視來顯示不同的色彩和字型樣式語言的不同項目。 此差異可以輕鬆地讀取及編輯檔案。<br /><br /> 如需一般資訊，請參閱 <<c0> [ 語法著色舊版語言服務中](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。<br /><br /> 如需在 managed 的 package framework (MPF) 這項功能的詳細資訊，請參閱[舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。|  
|陳述式完成|完成陳述式或使用者已開始輸入的關鍵字。 陳述式完成可協助使用者更輕鬆地與少打一些字以及較少錯誤的機率輸入困難的陳述式。<br /><br /> 如需一般資訊，請參閱 <<c0> [ 舊版語言服務中的陳述式完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。<br /><br /> MPF 這項功能的相關資訊，請參閱[舊版語言服務中的文字自動完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)。|  
|括號對稱|反白顯示配對字元，例如大括號。 當使用者輸入的結尾字元例如"}"，大括號比對會反白顯示對應的開頭字元，例如"{"。 封入字元的數個層級時，這項功能可協助確認封入字元正確對應的使用者。<br /><br /> MPF 這項功能的相關資訊，請參閱[舊版語言服務中的大括號比對](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)。|  
|參數資訊工具提示|會顯示一份可能的使用者目前輸入的多載方法的簽章。<br /><br /> 如需一般資訊，請參閱 <<c0> [ 舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。<br /><br /> MPF 這項功能的相關資訊，請參閱[舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)。|  
|錯誤標記|會顯示波浪式紅色底線，也就是彎曲語法不正確的文字。 錯誤標記通常用來讓使用者了解拼錯的關鍵字、 封閉的括號、 無效的字元，與類似的錯誤。<br /><br /> 在 MPF 類別中，錯誤標記處理中自動<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>方法的<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別。|  

 這些功能需要剖析原始程式碼的語言服務。 您通常可以重複使用的 token 化和剖析您的編譯器或解譯器的程式碼。  

 下列功能與程式設計語言支援，但不是語言服務的一部分：  


| 功能 | 描述 |
|-----------------------| - |
| 運算式評估工具 | 支援[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]透過驗證中斷點，並提供一份運算式的偵錯工具，顯示在 **[自動變數]** 偵錯視窗。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 偵錯的語言服務支援](../../extensibility/internals/language-service-support-for-debugging.md)。 |
| 符號瀏覽工具 | 支援**物件瀏覽器**，**類別檢視**，**呼叫瀏覽器**，以及**尋找符號結果**。 |

