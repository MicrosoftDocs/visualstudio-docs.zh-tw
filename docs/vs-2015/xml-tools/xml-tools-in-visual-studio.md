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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9a46523c4c856367e77c345c7e44d0dbc87508f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845978"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio 中的 XML 工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

可延伸標記語言 (XML)  (XML) * 是標記語言，可提供描述資料的格式。 這種語言可以協助在多個平台之間更精確地宣告內容，以及提供更有意義的搜尋結果。 此外，XML 可將資料的呈現方式與資料本身分開。 例如在 HTML 中，您可以使用標記來指示瀏覽器以粗體或斜體顯示資料，但在 XML 中，您只能使用標記來描述資料，例如城市名稱、溫度和氣壓。 在 XML 中，您可以使用可延伸樣式表語言 (XSL) 和階層式樣式表 (CSS) 等樣式表，在瀏覽器中呈現資料。 XML 可將資料的呈現方式和處理分開。 這讓您可以套用不同的樣式表和應用程式，以您想要的方式來顯示及處理資料。

 XML 是 SGML 的子集，已針對在網路上傳送進行最佳化。 它是由全球資訊網協會 (W3C) 所定義。 這項標準可確保結構化資料一致，並與應用程式或廠商無關。

 XML 是許多 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 和 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 功能的核心。 下列主題列出 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 和 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 所提供之與 XML 相關的工具和功能名稱。

 如需詳細資訊，請參閱 [Xml 開發人員中心](https://msdn.microsoft.com/data/bb190600.aspx)，其中提供適用于 xml 開發人員的最新檔、技術資訊、下載、新聞群組和其他資源。

## <a name="in-this-section"></a>本節內容
 使用[XML 資料](../xml-tools/working-with-xml-data.md)討論在中處理資料的方式中的 XML 角色 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。

 [調試 XSLT](../xml-tools/debugging-xslt.md) 提供有關使用 Visual Studio 偵錯工具來將 XSLT 進行偵錯工具的主題連結。

## <a name="reference"></a>參考資料
 [Microsoft.VisualStudio.Xml編輯器](https://msdn.microsoft.com/library/microsoft.visualstudio.xmleditor.aspx) 透過System.Xml 公開 [XML 編輯器](https://msdn.microsoft.com/library/ms255810.aspx) 剖析樹狀目錄 [ 。](https://msdn.microsoft.com/library/system.xml.linq.aspx) 適用于任何 XML 檔的 Linq。

 [XML 標準參考](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) 提供 XML 技術的相關資訊，包括 XML、檔案類型定義 (DTD) 、XML 架構定義語言 (XSD) 和 XSLT。

 <xref:System.Xml?displayProperty=fullName> 描述組成命名空間的類別和其他元素 <xref:System.Xml> ，並提供每個專案的詳細資訊連結。

 <xref:System.Xml.Serialization?displayProperty=fullName> 描述組成命名空間的類別和其他元素 <xref:System.Xml.Serialization> ，並提供每個專案的詳細資訊連結。

## <a name="related-sections"></a>相關章節
 [XML 檔物件模型 (DOM) ](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) 描述 <xref:System.Xml.XmlDocument> 和其相關聯的類別如何符合 W3C 檔物件模型 (Core) 層級1和層級2命名空間支援規格。

 [使用 XmlReader 讀取 XML](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) 描述如何透過 <xref:System.Xml.XmlReader> xml 資料流程提供非快取、順向、唯讀存取 xml 資料。

 [使用 XmlWriter 撰寫 XML](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) 說明如何 <xref:System.Xml.XmlWriter> 提供非快建、順向、產生 xml 資料流程的方法，並協助您建立符合 W3C 標準的 xml 檔。

 [XSLT 轉換](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) 描述類別如何 <xref:System.Xml.Xsl.XslCompiledTransform> 實行 XSLT 1.0 建議。

 [使用 XPath 資料模型處理 XML 資料](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) 描述類別如何 <xref:System.Xml.XPath.XPathNavigator> 處理儲存在或物件中的 XML 資料 <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> 。 <xref:System.Xml.XPath.XPathNavigator> 類別以 XQuery 1.0 和 XPath 2.0 資料模型為基礎，可用以巡覽和編輯 XML 資料。

 [XML 架構物件模型 (SOM) ](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) 描述用來建立和操作 XML 架構的類別，方法是提供 <xref:System.Xml.Schema.XmlSchema> 載入和編輯架構的類別。
