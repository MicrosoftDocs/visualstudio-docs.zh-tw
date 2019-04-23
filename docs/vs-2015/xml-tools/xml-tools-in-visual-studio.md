---
title: XML 工具
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
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
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 07cb1a790640d01448b6331986519bf1bef619e9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651717"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio 中的 XML 工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

可延伸標記語言 (XML) * 是一種標記語言，提供用來描述資料格式。 這種語言可以協助在多個平台之間更精確地宣告內容，以及提供更有意義的搜尋結果。 此外，XML 可將資料的呈現方式與資料本身分開。 例如在 HTML 中，您可以使用標記來指示瀏覽器以粗體或斜體顯示資料，但在 XML 中，您只能使用標記來描述資料，例如城市名稱、溫度和氣壓。 在 XML 中，您可以使用可延伸樣式表語言 (XSL) 和階層式樣式表 (CSS) 等樣式表，在瀏覽器中呈現資料。 XML 可將資料的呈現方式和處理分開。 這讓您可以套用不同的樣式表和應用程式，以您想要的方式來顯示及處理資料。

 XML 是 SGML 的子集，已針對在網路上傳送進行最佳化。 它是由全球資訊網協會 (W3C) 所定義。 這項標準可確保結構化資料一致，並與應用程式或廠商無關。

 XML 是許多 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 和 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 功能的核心。 下列主題列出 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 和 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 所提供之與 XML 相關的工具和功能名稱。

 如需詳細資訊，請參閱 < [XML 開發人員中心](http://go.microsoft.com/fwlink/?LinkID=100176)，其為 XML 開發人員提供最新的文件、 技術資訊、 下載、 新聞群組和其他資源。

## <a name="in-this-section"></a>本節內容
 [使用 XML 資料](../xml-tools/working-with-xml-data.md)討論在處理 XML 資料的方式中的角色[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。

 [偵錯 XSLT](../xml-tools/debugging-xslt.md)提供有關使用 Visual Studio 偵錯工具來偵錯 XSLT 的主題連結。

## <a name="reference"></a>參考資料
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)公開[XML 編輯器](http://go.microsoft.com/fwlink/?LinkId=228249)剖析樹狀結構，透過[System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250)任何 XML 文件。

 [XML 標準參考](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401)提供 XML 技術，包括 XML、 文件類型定義 (DTD)、 XML 結構描述定義語言 (XSD) 和 XSLT 的相關資訊。

 <xref:System.Xml?displayProperty=fullName> 描述類別和其他項目構成<xref:System.Xml>命名空間，並提供更多詳細資訊的連結，每個項目。

 <xref:System.Xml.Serialization?displayProperty=fullName> 描述類別和其他項目構成<xref:System.Xml.Serialization>命名空間，並提供每個項目相關的更多詳細資訊的連結。

## <a name="related-sections"></a>相關章節
 [XML 文件物件模型 (DOM)](http://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54)描述如何<xref:System.Xml.XmlDocument>和其相關聯的類別符合 W3C 文件物件模型 （核心） 層級 1 和層級 2 命名空間支援規格。

 [使用 XmlReader 讀取 XML](http://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182)描述如何<xref:System.Xml.XmlReader>提供非快取、 順向、 唯讀存取 XML 資料的 XML 資料流。

 [撰寫 XML 使用 XmlWriter](http://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)描述如何<xref:System.Xml.XmlWriter>非快取、 順向的方式產生 XML 資料流，並協助您建置符合 W3C 標準的 XML 文件。

 [XSLT 轉換](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03)描述如何<xref:System.Xml.Xsl.XslCompiledTransform>類別實作 XSLT 1.0 建議事項。

 [處理 XML 資料使用 XPath 資料模型](http://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081)描述如何<xref:System.Xml.XPath.XPathNavigator>類別可以處理 XML 資料儲存在<xref:System.Xml.XPath.XPathDocument>或<xref:System.Xml.XmlDocument>物件。 <xref:System.Xml.XPath.XPathNavigator> 類別以 XQuery 1.0 和 XPath 2.0 資料模型為基礎，可用以巡覽和編輯 XML 資料。

 [XML 結構描述物件模型 (SOM)](http://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd)描述用來建立及操作 XML 結構描述，藉由提供的類別<xref:System.Xml.Schema.XmlSchema>類別來載入及編輯結構描述。
