---
title: XML 編輯器
description: 瞭解 Visual Studio 中以文字編輯器為基礎的 XML 編輯器，並包含 XML 語言的其他支援。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de79063eeef5056bd850d8fa1fe76d6698c7e082
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874842"
---
# <a name="xml-editor"></a>XML 編輯器

Visual Studio 中的 XML 編輯器是以文字編輯器為基礎，並包含 XML 語言的其他支援。 當您在 Visual Studio 中開啟 XML 檔案時，它會在 [XML 編輯器] 中開啟。

XML 編輯器包含下列功能：

- XML 1.0 語法檢查。

- 輸入時的結構描述驗證。

- XML 片段支援，包括結構描述產生的片段。

- 文件類型定義 (DTD) 支援。

- XML 結構描述定義語言 (XSD) 結構描述支援。

- 從 XML 執行個體文件建立 XML 結構描述。

- 將 DTD 或 XML 資料精簡 (XDR) 結構描述轉換成 XML 結構描述。

- XSLT 語法檢查。

- 文件大綱，以便展開及摺疊項目。

- 與 [XML 架構瀏覽器](../xml-tools/xml-schema-explorer.md)整合。 這會提供 XML 架構的階層視圖。

XML 編輯器是針對已知的副檔名（例如 *.xml*、 *.xsd*、 *.xsl* 和 *.config*）叫用。如果檔案似乎包含 XML，也會在任何未知的副檔名上叫用它。

## <a name="xslt-intellisense"></a>XSLT IntelliSense

[XSLT IntelliSense](../xml-tools/xml-editor-intellisense-features.md) 可讓您針對指定的模式或指定的命名範本，自動完成屬性集名稱、範本模式和名稱，以及參數名稱。

## <a name="xslt-profiler"></a>XSLT 分析工具

[Xslt](../xml-tools/xslt-profiler.md)分析工具會建立詳細的 xslt 效能報告，協助您測量、評估及鎖定 XSLT 程式碼中與效能相關的問題。 XSLT 分析工具也包含 XSL 和 XSLT 樣式表最佳化的實用提示。

## <a name="xslt-hierarchy"></a>XSLT 階層

[XSLT 階層工具](../xml-tools/walkthrough-using-xslt-hierarchy.md)可讓您在包含的樣式表單及/或內建範本規則中加入中斷點。

## <a name="see-also"></a>另請參閱

- [XML 編輯器選項-格式設定](../ide/reference/options-text-editor-xml-formatting.md)
- [XML 編輯器選項-其他](../ide/reference/options-text-editor-xml-miscellaneous.md)
- [程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md)
- [XML 標準參考](/previous-versions/dotnet/netframework-4.0/ms256177(v=vs.100))
- [Visual Studio 中的 XML 工具](../xml-tools/xml-tools-in-visual-studio.md)