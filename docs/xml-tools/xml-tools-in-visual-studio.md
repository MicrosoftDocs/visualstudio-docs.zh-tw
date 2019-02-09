---
title: XML 工具
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
ms.openlocfilehash: 9d07e7d2a1a8d96b19354ea8d1261b2e82a84d3a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55946885"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio 中的 XML 工具

*可延伸標記語言 (XML)* 是一種標記語言，提供用來描述資料格式。 這種語言可以協助在多個平台之間更精確地宣告內容，以及提供更有意義的搜尋結果。 此外，XML 可將資料的呈現方式與資料本身分開。 例如在 HTML 中，您可以使用標記來指示瀏覽器以粗體或斜體顯示資料，但在 XML 中，您只能使用標記來描述資料，例如城市名稱、溫度和氣壓。 在 XML 中，您使用的樣式表等 Extensible Stylesheet Language (XSL) 和階層式樣式表 (CSS) 來呈現瀏覽器中的資料。 XML 可將資料的呈現方式和處理分開。 這讓您可以套用不同的樣式表和應用程式，以您想要的方式來顯示及處理資料。

XML 是 SGML 的子集，已針對在網路上傳送進行最佳化。 它是由全球資訊網協會 (W3C) 所定義。 此項標準可確保結構化的資料是統一且獨立的應用程式或廠商。

XML 是 Visual Studio 和.NET Framework 的許多功能的核心。 下列清單中，發行項名稱的工具和 XML 與相關的功能在 Visual Studio 和.NET Framework 所提供。

如需詳細資訊，請參閱<xref:System.Xml?displayProperty=fullName>文件。

## <a name="reference"></a>參考資料

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)公開[XML 編輯器](http://go.microsoft.com/fwlink/?LinkId=228249)剖析樹狀結構，透過[System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250)任何 XML 文件。

[XML 標準參考](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401)提供 XML 技術，包括 XML、 文件類型定義 (DTD)、 XML 結構描述定義語言 (XSD) 和 XSLT 的相關資訊。

<xref:System.Xml?displayProperty=fullName> 描述類別和其他項目構成<xref:System.Xml>命名空間，並提供更多詳細資訊的連結，每個項目。

<xref:System.Xml.Serialization?displayProperty=fullName> 描述類別和其他項目構成<xref:System.Xml.Serialization>命名空間，並提供每個項目相關的更多詳細資訊的連結。

## <a name="related-sections"></a>相關章節

[XML 文件物件模型 (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)描述如何<xref:System.Xml.XmlDocument>和其相關聯的類別符合 W3C 文件物件模型 （核心） 層級 1 和層級 2 命名空間支援規格。

[處理 XML 資料與 XmlReader 和 XmlWriter](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc189001\(v\=vs.95\))

[XSLT 轉換](/dotnet/standard/data/xml/xslt-transformations)描述如何<xref:System.Xml.Xsl.XslCompiledTransform>類別實作 XSLT 1.0 建議事項。

[處理 XML 資料使用 XPath 資料模型](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)描述如何<xref:System.Xml.XPath.XPathNavigator>類別可以處理 XML 資料儲存在<xref:System.Xml.XPath.XPathDocument>或<xref:System.Xml.XmlDocument>物件。 <xref:System.Xml.XPath.XPathNavigator> 類別以 XQuery 1.0 和 XPath 2.0 資料模型為基礎，可用以巡覽和編輯 XML 資料。

[XML 結構描述物件模型 (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)描述用來建立及操作 XML 結構描述，藉由提供的類別<xref:System.Xml.Schema.XmlSchema>類別來載入及編輯結構描述。