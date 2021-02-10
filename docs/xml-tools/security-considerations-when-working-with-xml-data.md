---
title: 使用 XML 資料時的安全性考量
description: 瞭解在 XML 編輯器或 XSLT 偵錯工具中使用 XML 資料時的安全性考慮。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0bb4a293e4879838d53093b41cacf004b57de7e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968602"
---
# <a name="security-considerations-when-working-with-xml-data"></a>使用 XML 資料時的安全性考慮

本主題討論使用 XML 編輯器或 XSLT 偵錯工具時，您需要瞭解的安全性問題。

## <a name="xml-editor"></a>XML 編輯器

XML 編輯器是以 Visual Studio 文字編輯器為基礎。 它依賴 <xref:System.Xml> 及 <xref:System.Xml.Xsl> 類別來處理許多 XML 處理序。

- 會在新的應用程式定義域中執行 XSLT 轉換。 XSLT 轉換為 *沙箱* 化;也就是說，您電腦的代碼啟用安全性原則會用來根據 XSLT 樣式表單的位置來決定限制的許可權。 例如，來自網際網路位置的樣式表具有限制最嚴格的使用權限，但是複製到硬碟的樣式表則可以「完全信任」使用權限執行。

- <xref:System.Xml.Xsl.XslCompiledTransform> 類別用於將 XSLT 編譯為 Microsoft Intermediate Language，以在執行期間獲得更快的效能。

- 當 XML 編輯器首次載入時，會自動下載指向類別目錄檔案中外部位置的架構。 <xref:System.Xml.Schema.XmlSchemaSet> 類別用於編譯結構描述。 XML 編輯器隨附的類別目錄檔案沒有任何外部架構的連結。 使用者必須在 XML 編輯器下載架構檔案之前，明確地加入外部架構的參考。 您可以透過 XML 編輯器的 [ **其他工具選項** ] 頁面來停用 HTTP 下載。

- XML 編輯器會使用 <xref:System.Net> 類別來下載架構

## <a name="xslt-debugger"></a>XSLT 偵錯工具

XSLT 偵錯工具會使用 Visual Studio Managed 偵錯引擎、<xref:System.Xml> 的類別及 <xref:System.Xml.Xsl> 命名空間。

- XSLT 偵錯工具會在 sandboxed 應用程式定義域中執行每個 XSLT 轉換。 電腦的程式碼存取安全性原則會用於根據 XSLT 樣式表的位置，來決定限制的使用權限。 例如，來自網際網路位置的樣式表具有限制最嚴格的使用權限，但是複製到硬碟的樣式表則可以「完全信任」使用權限執行。

- 會使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來編譯 XSLT 樣式表。

- Managed 偵錯引擎會載入 XSLT 運算式評估工具。 Managed 偵錯引擎會假設所有的程式碼都是從使用者的本機電腦上執行。 相應地，<xref:System.Xml.Xsl.XslCompiledTransform> 類別會將 XSLT 檔案下載到使用者的本機電腦。 藉由使用限制的使用權限在新的應用程式定義域中執行所有的 XSLT 轉換，可降低執行權限提升的可能性。

## <a name="see-also"></a>另請參閱

- [應用程式域](/dotnet/framework/app-domains/application-domains)