---
title: "Visual Studio 中的 XML 工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 38d933199c85bee3fa85a533f9c61c08bee898ea
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio 中的 XML 工具

*可延伸標記語言 (XML)*是一種標記語言，提供用來描述資料格式。 這種語言可以協助在多個平台之間更精確地宣告內容，以及提供更有意義的搜尋結果。 此外，XML 可將資料的呈現方式與資料本身分開。 例如在 HTML 中，您可以使用標記來指示瀏覽器以粗體或斜體顯示資料，但在 XML 中，您只能使用標記來描述資料，例如城市名稱、溫度和氣壓。 在 XML 中，您可以使用可延伸樣式表語言 (XSL) 和階層式樣式表 (CSS) 等樣式表，在瀏覽器中呈現資料。 XML 可將資料的呈現方式和處理分開。 這讓您可以套用不同的樣式表和應用程式，以您想要的方式來顯示及處理資料。

XML 是 SGML 的子集，已針對在網路上傳送進行最佳化。 它是由全球資訊網協會 (W3C) 所定義。 這項標準可確保結構化資料一致，並與應用程式或廠商無關。

XML 是許多功能的 Visual Studio 和.NET Framework 的核心。 下列主題列出命名的工具和在 Visual Studio 和.NET Framework 提供的 XML 與相關功能。

如需詳細資訊，請參閱<xref:System.Xml?displayProperty=fullName>文件。

## <a name="in-this-section"></a>本節內容

[使用 XML 資料](../xml-tools/working-with-xml-data.md)  
討論在 Visual Studio 中處理資料的方式中 XML 的角色。

[偵錯 XSLT](../xml-tools/debugging-xslt.md)  
提供使用 Visual Studio 偵錯工具來偵錯 XSLT 的主題連結。

## <a name="reference"></a>參考資料

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
公開[XML 編輯器](http://go.microsoft.com/fwlink/?LinkId=228249)剖析樹狀結構，透過[System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250)針對任何 XML 文件。

[XML 標準參考](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401)  
提供 XML 技術的資訊，包括 XML、文件類型定義 (DTD)、XML 結構描述定義語言 (XSD) 和 XSLT。

<xref:System.Xml?displayProperty=fullName>  
說明 <xref:System.Xml> 命名空間的組成類別和其他項目，並且提供每個項目的詳細資訊連結。

<xref:System.Xml.Serialization?displayProperty=fullName>  
說明 <xref:System.Xml.Serialization> 命名空間的組成類別和其他項目，並且提供每個項目的詳細資訊連結。

## <a name="related-sections"></a>相關章節

[XML 文件物件模型 (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)  
說明 <xref:System.Xml.XmlDocument> 及其相關類別如何符合 W3C 文件物件模型 (核心) 層級 1 和層級 2 命名空間支援規格。

[使用 XmlReader 和 XmlWriter 處理 XML 資料](https://msdn.microsoft.com/library/cc189001(v=vs.95).aspx)

[XSLT 轉換](/dotnet/standard/data/xml/xslt-transformations)  
說明 <xref:System.Xml.Xsl.XslCompiledTransform> 類別如何實作 XSLT 1.0 建議。

[使用 XPath 資料模型處理 XML 資料](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)  
說明 <xref:System.Xml.XPath.XPathNavigator> 類別如何處理儲存在 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的 XML 資料。 <xref:System.Xml.XPath.XPathNavigator> 類別以 XQuery 1.0 和 XPath 2.0 資料模型為基礎，可用以巡覽和編輯 XML 資料。

[XML 結構描述物件模型 (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)  
說明用於建立及操作 XML 結構描述的類別，方法是提供 <xref:System.Xml.Schema.XmlSchema> 類別來載入及編輯結構描述。