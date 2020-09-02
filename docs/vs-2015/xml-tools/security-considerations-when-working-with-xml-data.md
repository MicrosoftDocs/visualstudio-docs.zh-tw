---
title: 使用 XML 資料時的安全性考慮 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 491e8cf8f9441180e66259ed295e04e8a1a90493
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656130"
---
# <a name="security-considerations-when-working-with-xml-data"></a>使用 XML 資料時的安全性考量
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題討論使用 XML 編輯器或 XSLT 偵錯工具時，需要了解的安全性問題。

## <a name="xml-editor"></a>XML 編輯器
 XML 編輯器以 Visual Studio 文字編輯器為基礎。 它依賴 <xref:System.Xml> 及 <xref:System.Xml.Xsl> 類別來處理許多 XML 處理序。

- 會在新的應用程式定義域中執行 XSLT 轉換。 XSLT 轉換為 *沙箱*化;也就是說，您電腦的代碼啟用安全性原則會用來根據 XSLT 樣式表單的位置來決定限制的許可權。 例如，來自網際網路位置的樣式表具有限制最嚴格的使用權限，但是複製到硬碟的樣式表則可以「完全信任」使用權限執行。

- <xref:System.Xml.Xsl.XslCompiledTransform> 類別用於將 XSLT 編譯為 Microsoft Intermediate Language，以在執行期間獲得更快的效能。

- XML 編輯器首次載入時，會自動下載目錄檔案中指向外部位置的結構描述。 <xref:System.Xml.Schema.XmlSchemaSet> 類別用於編譯結構描述。 XML 編輯器隨附的目錄檔案不具有任何外部結構描述的連結。 使用者必須明確加入外部結構描述的參考，XML 編輯器才能下載結構描述檔案。 您可以透過 XML 編輯器的 [ **其他工具選項** ] 頁面來停用 HTTP 下載。

- XML 編輯器使用 <xref:System.Net> 類別來下載結構描述

## <a name="xslt-debugger"></a>XSLT 偵錯工具
 XSLT 偵錯工具會使用 Visual Studio Managed 偵錯引擎、<xref:System.Xml> 的類別及 <xref:System.Xml.Xsl> 命名空間。

- XSLT 偵錯工具會在 sandboxed 應用程式定義域中執行每個 XSLT 轉換。 電腦的程式碼存取安全性原則會用於根據 XSLT 樣式表的位置，來決定限制的使用權限。 例如，來自網際網路位置的樣式表具有限制最嚴格的使用權限，但是複製到硬碟的樣式表則可以「完全信任」使用權限執行。

- 會使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來編譯 XSLT 樣式表。

- Managed 偵錯引擎會載入 XSLT 運算式評估工具。 Managed 偵錯引擎會假設所有的程式碼都是從使用者的本機電腦上執行。 相應地，<xref:System.Xml.Xsl.XslCompiledTransform> 類別會將 XSLT 檔案下載到使用者的本機電腦。 藉由使用限制的使用權限在新的應用程式定義域中執行所有的 XSLT 轉換，可降低執行權限提升的可能性。

## <a name="see-also"></a>另請參閱
 [應用程式定義域](https://msdn.microsoft.com/39e57d07-a740-4cd4-ae82-e119ea3856c1)
