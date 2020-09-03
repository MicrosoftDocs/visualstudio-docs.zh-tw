---
title: 搜尋運算式中的進階搜尋運算子 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5088fc04f4440260bdb9d3f040d99061c05d243
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620342"
---
# <a name="advanced-search-operators-in-search-expressions"></a>搜尋運算式中的進階搜尋運算子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

藉由使用 advanced search 運算子，您可以從較簡單的搜尋運算式建立更複雜的搜尋運算式來精簡搜尋內容。 如下表所示，這些運算子會限制查詢的執行內容。

> [!WARNING]
> 您必須輸入包含最終冒號且冒號前面沒有介入空格的進階搜尋運算子，搜尋引擎才能加以辨認。

|搜尋|用法|範例|結果|
|-------------------|---------|-------------|------------|
|主題標題中的詞彙|標題：|title:binaryreader|標題中包含 “binaryreader” 的主題。|
|程式碼範例中的詞彙|code:|code:readdouble|程式碼範例中包含 "readdouble" 的主題。|
|特定程式設計語言範例中的詞彙|code:vb:|code:vb:string|Visual Basic 範例中包含 “string” 的主題。|
|與特定索引關鍵字建立關聯的主題|keyword:|keyword:readbyte|與 “readbyte” 索引關鍵字建立關聯的主題。|

 您可以使用 code: 運算子尋找數種程式設計語言中任一種的內容，但它只會傳回特定程式設計語言所標上內容的結果。 下表列出此運算子所支援的程式設計語言：

|程式設計語言|用途|
|--------------------------|---------|
|Visual Basic|code:vb<br /><br /> 或<br /><br /> code:visualbasic|
|C#|code:c#<br /><br /> 或<br /><br /> code:csharp|
|C++|code:cpp<br /><br /> 或<br /><br /> code:c++<br /><br /> 或<br /><br /> code:cplusplus|
|F#|code:f#<br /><br /> 或<br /><br /> code:fsharp|
|JavaScript|code:javascript<br /><br /> 或<br /><br /> code:js|
|XAML|code:xaml|

## <a name="see-also"></a>另請參閱
 [搜尋運算式中的邏輯運算子](../ide/logical-operators-in-search-expressions.md)[全文檢索搜尋提示](../ide/full-text-search-tips.md)
