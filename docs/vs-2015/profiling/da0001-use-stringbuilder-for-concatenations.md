---
title: DA0001：使用 StringBuilder 進行串連 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb8da704832031d69156eee8863b689e7956f025
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295961"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001：使用 StringBuilder 進行串連
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱[DA0001：使用 StringBuilder 進行](https://docs.microsoft.com/visualstudio/profiling/da0001-use-stringbuilder-for-concatenations)串連。  
  
|||  
|-|-|  
|規則識別碼|DA0001|  
|分類|.NET Framework 使用方式|  
|分析方法|取樣<br /><br /> 檢測設備|  
|訊息|請考慮使用 StringBuilder 來進行字串串連|  
|訊息類型|警告|  
  
## <a name="cause"></a>原因  
 對 System.String.Concat 的呼叫大部分是分析資料。 請考慮使用 <xref:System.Text.StringBuilder> 類別，從多個區段建構字串。  
  
## <a name="rule-description"></a>規則描述  
 <xref:System.String> 物件不可變。 因此，任何的字串修改都會建立新的字串物件，以及造成原始字串的記憶體回收。 無論您明確地呼叫 String.Concat，或是使用字串串連運算子 (例如 + 或 +=)，此行為都相同。 如果經常呼叫這些方法，例如在緊密迴圈中對字串加入字元，可能會降低程式效能。  
  
 StringBuilder 類別是可變動的物件，並不像 System.String，大部分 StringBuilder 上修改此類別之執行個體的方法會傳回該相同執行個體的參考。 您可以插入字元或將文字附加到 StringBuilder 執行個體，然後移除或取代執行個體中的字元，不需要配置新的執行個體並刪除原始執行個體。  
  
## <a name="how-to-investigate-a-warning"></a>如何調查警告  
 按兩下 [錯誤清單] 視窗中的訊息，瀏覽至取樣分析資料的[函式詳細資料檢視](../profiling/function-details-view.md)。 找出程式最常使用字串串連的區段。 對於複雜的字串操作 (包括常見的字串串連作業) 使用 StringBuilder 類別。  
  
 如需如何使用字串的詳細資訊，請參閱 Microsoft Patterns and Practices 文件庫中[第 5 章 - 改善 Managed 程式碼的效能 (英文)](https://go.microsoft.com/fwlink/?LinkId=177816)的[字串作業 (英文)](https://go.microsoft.com/fwlink/?LinkId=177817)一節。
