---
title: XML 編輯器和結構描述設計工具
ms.date: 11/04/2016
ms.topic: conceptual
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
- XML [Visual Studio], .NET Framework classes
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8854aee047fa961c4f0973397cfc2fe6ac6e6ad
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526564"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio 中的 XML 工具

*可延伸標記語言 (XML)* 是一種標記語言，提供用來描述資料格式。 XML 會將資料與它所使用的呈現樣式表等 Extensible Stylesheet Language (XSL) 和階層式樣式表 (CSS)。 Visual Studio 包括一些工具及功能，讓使用 XML、XSLT 及 XML 結構描述更為容易。

## <a name="xml-editor"></a>XML 編輯器

[XML 編輯器](xml-editor.md)用來編輯 XML 文件。 它會提供完整的 XML 語法檢查、 結構描述驗證時，您的型別、 色彩編碼及 IntelliSense。 如果已提供結構描述或文件類型定義，IntelliSense 即可使用它來列出允許的項目及屬性。

其他功能包括：

- XML 程式碼片段支援，包括結構描述產生的程式碼片段

- 文件大綱，以便展開及摺疊項目

- 執行 XSLT 轉換，並做為文字、 XML 或 HTML 檢視結果的能力

- 從 XML 執行個體文件產生 XML 結構描述定義語言 (XSD) 結構描述的功能

- 支援編輯 XSLT 樣式表，包括 IntelliSense 支援

- XML 結構描述總管

## <a name="xml-schema-designer"></a>XML 結構描述設計工具

[XML 結構描述設計工具](xml-schema-designer.md)整合於 Visual Studio 和 XML 編輯器可讓您使用 XML 結構描述定義語言 (XSD) 結構描述。

## <a name="xslt-debugging"></a>XSLT 偵錯

Visual Studio 支援[XSLT 樣式表進行偵錯](../xml-tools/debugging-xslt.md)。 使用偵錯工具，您可在 XSLT 樣式表中設定中斷點，從程式碼逐步執行 XSLT 樣式表等。

> [!NOTE]
> 只有 Enterprise 版的 Visual Studio 中使用 XSLT 偵錯工具。

## <a name="see-also"></a>另請參閱

- <xref:System.Xml?displayProperty=fullName>
- [XSLT 轉換](/dotnet/standard/data/xml/xslt-transformations)
- [使用 XPath 資料模型處理 XML 資料](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [XML 文件物件模型 (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [XML 結構描述物件模型 (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)