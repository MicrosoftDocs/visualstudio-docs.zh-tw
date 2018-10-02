---
title: 搜尋運算式中的邏輯運算子 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cf55bbdc025b4aabd13f7ded72c2ea69386a61b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486521"
---
# <a name="logical-operators-in-search-expressions"></a>搜尋運算式中的邏輯運算子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[搜尋運算式中的邏輯運算子](https://docs.microsoft.com/visualstudio/ide/logical-operators-in-search-expressions)。  
  
使用邏輯運算子，即可從較簡單的搜尋運算式建立更複雜的搜尋運算式來精簡搜尋內容。 如下表所示，邏輯運算子指定應該如何在搜尋查詢中合併多個搜尋詞彙。  
  
> [!IMPORTANT]
>  您必須輸入全部大寫的邏輯運算子，搜尋引擎才能辨識它們。  
  
|搜尋|使用|範例|結果|  
|-------------------|---------|-------------|------------|  
|相同主題中的兩個詞彙|AND|dib AND palette|包含 "dib" 和 "palette" 的主題。|  
|主題中的任一個詞彙|OR|raster OR vector|包含 "raster" 或 "vector" 的主題。|  
|相同主題中沒有第二個詞彙的第一個詞彙|NOT|"operating system" NOT DOS|包含 "operating system" 但沒有 "DOS" 的主題。|  
|主題中接近的兩個詞彙|NEAR|user NEAR kernel|包含十分接近 "kernel" 之 "user" 的主題。|  
  
## <a name="see-also"></a>另請參閱  
 [全文檢索搜尋提示](../ide/full-text-search-tips.md)   
 [尋找資訊](../ide/locate-information.md)



