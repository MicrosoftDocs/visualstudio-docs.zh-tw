---
title: 使用 XML 資料時的安全性考量
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f9d3c3e8ddffb72b04a9ca2fc0ec4df5eaac150
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966701"
---
# <a name="security-considerations-when-working-with-xml-data"></a>使用 XML 資料時的安全性考量

本主題討論您需要使用 XML 編輯器或 XSLT 偵錯工具時，了解的安全性問題。

## <a name="xml-editor"></a>XML 編輯器

 XML 編輯器是以基礎上 Visual Studio 文字編輯器。 它依賴 <xref:System.Xml> 及 <xref:System.Xml.Xsl> 類別來處理許多 XML 處理序。

- 會在新的應用程式定義域中執行 XSLT 轉換。 XSLT 轉換*沙箱*; 也就是您電腦的程式碼存取安全性原則用來判斷根據 XSLT 樣式表的位置限制的使用權限。 例如，來自網際網路位置的樣式表具有限制最嚴格的使用權限，但是複製到硬碟的樣式表則可以「完全信任」使用權限執行。

- <xref:System.Xml.Xsl.XslCompiledTransform> 類別用於將 XSLT 編譯為 Microsoft Intermediate Language，以在執行期間獲得更快的效能。

- XML 編輯器首次載入時，會自動下載類別目錄檔案的外部位置所指向的結構描述。 <xref:System.Xml.Schema.XmlSchemaSet> 類別用於編譯結構描述。 XML 編輯器隨附的類別目錄檔案並沒有任何外部結構描述的連結。 使用者必須明確加入外部結構描述的參考之前在 XML 編輯器結構描述會將檔案下載。 HTTP 下載可透過停用**其他工具選項**XML 編輯器的頁面。

- XML 編輯器使用<xref:System.Net>類別來下載結構描述

## <a name="xslt-debugger"></a>XSLT 偵錯工具

 XSLT 偵錯工具會使用 Visual Studio Managed 偵錯引擎、<xref:System.Xml> 的類別及 <xref:System.Xml.Xsl> 命名空間。

- XSLT 偵錯工具會在 sandboxed 應用程式定義域中執行每個 XSLT 轉換。 電腦的程式碼存取安全性原則會用於根據 XSLT 樣式表的位置，來決定限制的使用權限。 例如，來自網際網路位置的樣式表具有限制最嚴格的使用權限，但是複製到硬碟的樣式表則可以「完全信任」使用權限執行。

- 會使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來編譯 XSLT 樣式表。

- Managed 偵錯引擎會載入 XSLT 運算式評估工具。 Managed 偵錯引擎會假設所有的程式碼都是從使用者的本機電腦上執行。 相應地，<xref:System.Xml.Xsl.XslCompiledTransform> 類別會將 XSLT 檔案下載到使用者的本機電腦。 藉由使用限制的使用權限在新的應用程式定義域中執行所有的 XSLT 轉換，可降低執行權限提升的可能性。

## <a name="see-also"></a>另請參閱

- [應用程式定義域](/dotnet/framework/app-domains/application-domains)