---
title: 傳統語言服務要點 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 501bccf755293e86e8a9dc23fce125a10c882376
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707416"
---
# <a name="legacy-language-service-essentials"></a>舊版語言服務的基本資訊
您必須提供語言服務,以便將程式設計語言整合到 Visual Studio 中。 本主題介紹舊語言服務中可用的功能。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解有關實現語言服務的新方法的詳細資訊,請參閱[編輯器和語言服務擴展](../../extensibility/editor-and-language-service-extensions.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

 傳統語言服務提供以下功能:

|功能|描述|
|-------------|-----------------|
|語法標色|使編輯器檢視顯示不同語言元素的不同顏色和字體樣式。 這種區別可以使讀取和編輯檔變得更加容易。<br /><br /> 有關一般資訊,請參閱[舊語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。<br /><br /> 有關託管套件框架 (MPF) 中此功能的資訊,請參閱[舊語言服務中的語法著色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。|
|陳述式完成|完成使用者已開始鍵入的語句或關鍵字。 語句完成可幫助使用者更輕鬆地輸入困難語句,減少鍵入次數和錯誤機會。<br /><br /> 有關一般資訊,請參閱[舊語言服務中的語句完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。<br /><br /> 有關 MPF 中此功能的資訊,請參考[舊語言服務中的字完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)。|
|括號對稱|突出顯示配對的字元,如大括弧。 當用戶鍵入結束字元(如"*")時,大括弧匹配將突出顯示相應的開口字元,如"*"。 當包含字元有多個級別時,此功能可幫助使用者確認封閉字元正確配對。<br /><br /> 有關 MPF 中此功能的資訊,請參閱[舊語言服務中的「大括弧匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)」。|
|參數資訊工具提示|顯示使用者當前鍵入的重載方法的可能簽名的清單。<br /><br /> 有關一般資訊,請參閱[舊語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。<br /><br /> 有關 MPF 中此功能的資訊,請參考[舊語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)。|
|錯誤標記|在語法不正確的文本下顯示波浪紅色下劃線,也稱為波浪形下劃線。 錯誤標記通常用於使用戶瞭解拼字、未閉合括弧、無效字元和類似的錯誤。<br /><br /> 在 MPF 類中,錯誤標<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A><xref:Microsoft.VisualStudio.Package.AuthoringSink>記在 類的方法中自動處理。|

 其中許多功能需要語言服務來分析原始碼。 通常,您可以為編譯器或解釋器重用標記和解析代碼。

 以下功能與對程式設計語言的支援相關,但不是語言服務的一部分:

| 功能 | 描述 |
|-----------------------| - |
| 運算式賦值器 | 通過驗證[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]斷點並提供要在**Autos**調試視窗中顯示的表達式清單,支援調試器。<br /><br /> 有關詳細資訊,請參閱[除錯的語言服務支援](../../extensibility/internals/language-service-support-for-debugging.md)。 |
| 符號瀏覽工具 | 支援**物件瀏覽器**,**類別檢視**、**除錯瀏覽器**與**尋找器的瀏覽器**。 |
