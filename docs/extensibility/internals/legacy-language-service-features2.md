---
title: 傳統語言服務功能2 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33f12e816476aa54f334988b99b9e86e820784f6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707363"
---
# <a name="legacy-language-service-features"></a>舊版語言服務功能
以下主題列出了您可以提供的一些舊語言服務功能。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解有關實現語言服務的新方法的詳細資訊,請參閱[編輯器和語言服務擴展](../../extensibility/editor-and-language-service-extensions.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="in-this-section"></a>本節內容
- [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 說明如何實現語法著色。

- [舊版語言服務中的自動格式化](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 說明如何實現自動格式化。

- [舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 說明如何實現 IntelliSense 參數資訊工具提示。

- [舊版語言服務中的陳述式完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 說明如何實現 IntelliSense 語句清單和成員完成清單。

- [舊版語言服務中的大綱和隱藏文字](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 說明如何實現大綱或隱藏文本。

- [如何︰在舊版語言服務中提供展開大綱的支援](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 解釋實現調試器支援的一些步驟。

## <a name="related-sections"></a>相關章節
