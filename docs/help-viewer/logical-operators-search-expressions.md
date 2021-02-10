---
title: '搜尋運算式中的邏輯運算子 (說明檢視器) '
description: 瞭解如何使用邏輯運算子和 advanced search 運算子來精簡 Microsoft Help Viewer 中的搜尋運算式。
ms.custom: SEO-VS-2020
ms.date: 11/02/2017
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 37e2652d04df154a45ae5f87fd62c8f8dc2e0b3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944078"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>搜尋運算式中的邏輯與進階運算子

您可以使用邏輯運算子與進階的搜尋運算子，來精簡 [說明檢視器] 的說明內容搜尋範圍。

## <a name="logical-operators"></a>邏輯運算子

邏輯運算子會指定應該如何在搜尋查詢中合併多個搜尋詞彙。 下表會顯示邏輯運算子 AND、OR、NOT 和 NEAR。

|搜尋|用法|範例|結果|
|-------------------|---------|-------------|------------|
|相同文章中的兩個詞彙|AND|dib AND palette|包含 "dib" 和 "palette" 的主題。|
|文章中的任一個詞彙|OR|raster OR vector|包含 "raster" 或 "vector" 的主題。|
|相同文章中沒有第二個詞彙的第一個詞彙|NOT|"operating system" NOT DOS|包含 "operating system" 但沒有 "DOS" 的主題。|
|文章中接近的兩個詞彙|NEAR|user NEAR kernel|包含十分接近 "kernel" 之 "user" 的主題。|

> [!IMPORTANT]
> 您必須輸入全部大寫的邏輯運算子，搜尋引擎才能辨識它們。

## <a name="advanced-operators"></a>進階運算子

進階搜尋運算子可藉由在文章中指定要尋找搜尋詞彙的位置，來精簡內容的搜尋範圍。 下表描述四個可用的進階搜尋運算子。

|搜尋|用法|範例|結果|
|-------------------|---------|-------------|------------|
|文章標題中的詞彙|`title:`|`title:binaryreader`|標題中包含 "binaryreader" 的主題。|
|程式碼範例中的詞彙|`code:`|`code:readdouble`|程式碼範例中包含 "readdouble" 的主題。|
|特定程式設計語言範例中的詞彙|`code:vb:`|`code:vb:string`|在 Visual Basic 程式碼範例中包含 "string" 的主題。|
|與特定索引關鍵字建立關聯的文章|`keyword:`|`keyword:readbyte`|與 "readbyte" 索引關鍵字建立關聯的主題。|

> [!IMPORTANT]
> 您必須輸入包含最終冒號且冒號前面沒有介入空格的進階搜尋運算子，搜尋引擎才能加以辨認。

### <a name="programming-languages-for-code-examples"></a>程式碼範例的程式設計語言

您可以使用 `code:` 運算子，來尋找數種程式設計語言中任一語言的相關內容。 若要傳回特定程式設計語言的範例，請使用下列其中一個程式設計語言值：

|程式設計語言|搜尋運算子語法|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> `code:` 運算子只會尋找標示程式設計語言標籤的內容，而不是以一般方式標記為程式碼的內容。

## <a name="see-also"></a>另請參閱

- [如何：搜尋主題](../help-viewer/find-topics.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
