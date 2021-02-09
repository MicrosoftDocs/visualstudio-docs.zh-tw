---
title: XML 編輯器中的 XML 檔驗證
description: 瞭解 XML 編輯器中的 XML 檔驗證，以及它如何檢查 XML 1.0 語法，並在您輸入時執行資料驗證。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d7046a08ac61ac0c23e98a47fb5eda75e38846c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874999"
---
# <a name="xml-document-validation"></a>XML 文件驗證

XML 編輯器會檢查 XML 1.0 語法，同時也會在您輸入時執行資料驗證。 該編輯器可使用文件類型定義 (DTD) 或結構描述進行驗證。 紅色波浪底線可反白顯示任何 XML 1.0 格式正確錯誤。 藍色波浪底線可依據 DTD 或結構描述驗證，顯示語意錯誤。 每個錯誤在錯誤清單中都有相關聯的項目。 您亦可讓滑鼠暫停在波浪底線上，以檢視錯誤訊息。

藉由將已編譯結構描述的 `targetNamespace` 與該項目的 xmlns 宣告相比對，可找到驗證中所使用的結構描述。 已編譯的結構描述會從下列其中一個位置載入，並以優先順序列出：

- 從 [文檔 **屬性**] 視窗的 [**架構**] 欄位中指定的檔案名。

- 內嵌結構描述或 DTD。

- 外部 DTD 或 `xsd:schemaLocation` 及 `xsd:noNamespaceSchemaLocation` 屬性。

- 「x-結構描述」XDR 結構描述命名空間 URI。

當結構描述具有非空白的目標命名空間時，也可在下列其他位置找到結構描述：

- 包含結構描述的其他編輯器視窗。

- 目前解決方案中的結構描述。

- 結構描述快取目錄中的結構描述。

## <a name="xslt-files"></a>XSLT 檔
編輯 XSLT 檔案時，會使用位於架構快取中的 *xslt .xsd* 檔案進行驗證。 驗證錯誤以藍色波浪底線顯示。 XSLT 編譯器中的錯誤以紅色波浪底線顯示。

## <a name="xml-schema-xsd-files"></a>XML 架構 (XSD) 檔
編輯 XML 架構檔案時，會使用位於架構快取中的 *xsdschema .xsd* 檔案進行驗證。 驗證錯誤以藍色波浪底線顯示。 任何編譯錯誤也會以紅色波浪底線顯示。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)
