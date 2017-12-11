---
redirect_url: /visualstudio/ide/logical-operators-in-search-expressions
ms.openlocfilehash: fe896af873197c95a4b226396e0b6333fdc40cfa
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
title: "搜尋運算式中的進階搜尋運算子 | Microsoft Docs" ms.custom: "" ms.date: "06/02/2017" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "Help Viewer, 搜尋關鍵字"
  - "Help Viewer, 搜尋程式碼"
  - "Help Viewer, 依程式設計語言搜尋程式碼"
  - "Help Viewer, 搜尋標題"
  - "搜尋程式碼 [Help Viewer]"
  - "搜尋標題 [Help Viewer]" ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e caps.latest.revision: 9 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="advanced-search-operators-in-search-expressions"></a>搜尋運算式中的進階搜尋運算子
您可以在 Help Viewer 中使用進階搜尋運算子，藉由在主題中指定要尋找搜尋字詞的位置，來縮小內容的搜尋範圍。 下表描述四個可用的進階搜尋運算子。

|搜尋|用法|範例|結果|  
|-------------------|---------|-------------|------------|  
|主題標題中的詞彙|title:|title:binaryreader|標題中包含 "binaryreader" 的主題。|  
|程式碼範例中的詞彙|code:|code:readdouble|程式碼範例中包含 "readdouble" 的主題。|  
|特定程式設計語言範例中的詞彙|code:vb:|code:vb:string|包含 Visual Basic 程式碼範例中 "string" 的主題。|  
|與特定索引關鍵字建立關聯的主題|keyword:|keyword:readbyte|與 "readbyte" 索引關鍵字建立關聯的主題。|  

> [!WARNING]
>  您必須輸入包含最終冒號且冒號前面沒有介入空格的進階搜尋運算子，搜尋引擎才能加以辨認。    

## <a name="programming-languages-for-code-examples"></a>程式碼範例的程式設計語言
您可以使用 code: 運算子尋找數種程式設計語言中任一種的內容，但它只會傳回標有程式設計語言標籤之內容的結果。 若要傳回特定程式設計語言的範例，請使用下列其中一個程式設計語言值：  

|程式設計語言|搜尋運算子語法|  
|--------------------|---------|  
|Visual Basic|code:vb<br/>code:visualbasic|  
|C#|code:c#<br/>code:csharp|  
|C++|code:cpp<br/>code:c++<br/>code:cplusplus|  
|F#|code:f#<br/>code:fsharp|  
|JavaScript|code:javascript<br/>code:js|  
|XAML|code:xaml|
