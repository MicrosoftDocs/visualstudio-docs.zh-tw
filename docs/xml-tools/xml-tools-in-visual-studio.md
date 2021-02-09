---
title: XML 編輯器和架構設計工具
description: 瞭解 Visual Studio 中的工具，以使用 XML、XSLT 及 XML 架構，包括 XML 編輯器、XML 架構設計工具和 XSLT 偵錯工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3e376980fb7c1e7f2378f23ae8230e6e45264ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874765"
---
# <a name="overview-of-xml-tools-in-visual-studio"></a>Visual Studio 中的 XML 工具總覽

*可延伸標記語言 (XML)  (XML)* 是提供描述資料格式的標記語言。 XML 會使用相關聯的樣式表單（例如可擴充樣式表單語言 (XSL) 和級聯樣式表 (CSS) ）來分隔資料及其呈現方式。 Visual Studio 包括一些工具及功能，讓使用 XML、XSLT 及 XML 結構描述更為容易。

## <a name="xml-editor"></a>XML 編輯器

[Xml 編輯器](xml-editor.md)是用來編輯 xml 檔。 它會在您鍵入、色彩編碼和 IntelliSense 時，提供完整的 XML 語法檢查、架構驗證。 如果已提供結構描述或文件類型定義，IntelliSense 即可使用它來列出允許的項目及屬性。

其他功能包括：

- XML 片段支援，包括架構產生的程式碼片段

- 檔大綱，以便展開及折迭元素

- 執行 XSLT 轉換並以文字、XML 或 HTML 形式來查看結果的能力

- 從 XML 實例檔產生 XML 架構定義語言 (XSD) 架構的能力

- 支援編輯 XSLT 樣式表單，包括 IntelliSense 支援

- XML 結構描述總管

## <a name="xml-schema-designer"></a>XML 結構描述設計工具

[Xml 架構設計](xml-schema-designer.md)工具與 VISUAL STUDIO 和 xml 編輯器整合，可讓您使用 xml 架構定義語言 (XSD) 架構。

## <a name="xslt-debugging"></a>XSLT 偵錯

Visual Studio 支援 [調試 XSLT 樣式表單](../xml-tools/debugging-xslt.md)。 使用偵錯工具，您可在 XSLT 樣式表中設定中斷點，從程式碼逐步執行 XSLT 樣式表等。

> [!NOTE]
> XSLT 偵錯工具僅適用于 Enterprise edition 的 Visual Studio。

## <a name="see-also"></a>另請參閱

- <xref:System.Xml?displayProperty=fullName>
- [XSLT 轉換](/dotnet/standard/data/xml/xslt-transformations)
- [使用 XPath 資料模型處理 XML 資料](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [XML 文件物件模型 (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [XML 結構描述物件模型 (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)
