---
title: DA0001-使用 StringBuilder 進行串連 |Microsoft 檔
description: 對 System.String.Concat 的呼叫大部分是分析資料。 請考慮使用 system.servicemodel 類別來建立多個區段中的字串。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 11ec65fc4131b4ad4d33fa25c616ecacc6a2fc79
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470023"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001：使用 StringBuilder 進行串連

|Item|值|
|-|-|
|規則 ID|DA0001|
|類別|.NET Framework 使用方式|
|分析方法|取樣<br /><br /> 測試設備|
|訊息|請考慮使用 StringBuilder 來進行字串串連|
|訊息類型|警告|

## <a name="cause"></a>原因
 對 System.String.Concat 的呼叫大部分是分析資料。 請考慮使用 <xref:System.Text.StringBuilder> 類別，從多個區段建構字串。

## <a name="rule-description"></a>規則描述
 <xref:System.String> 物件不可變。 因此，任何的字串修改都會建立新的字串物件，以及造成原始字串的記憶體回收。 無論您明確地呼叫 String.Concat，或是使用字串串連運算子 (例如 + 或 +=)，此行為都相同。 如果經常呼叫這些方法，例如在緊密迴圈中對字串加入字元，可能會降低程式效能。

 StringBuilder 類別是可變動的物件，並不像 System.String，大部分 StringBuilder 上修改此類別之執行個體的方法會傳回該相同執行個體的參考。 您可以插入字元或將文字附加到 StringBuilder 執行個體，然後移除或取代執行個體中的字元，不需要配置新的執行個體並刪除原始執行個體。

## <a name="how-to-investigate-a-warning"></a>如何調查警告
 按兩下 [ **錯誤清單** ] 視窗中的訊息，流覽至取樣設定檔資料的 [ [函數詳細](../profiling/function-details-view.md) 資料] 查看。 找出程式最常使用字串串連的區段。 對於複雜的字串操作 (包括常見的字串串連作業) 使用 StringBuilder 類別。

 如需如何使用字串的詳細資訊，請參閱 Microsoft Patterns and Practices 文件庫中[第 5 章 - 改善 Managed 程式碼的效能 (英文)](/previous-versions/msp-n-p/ff647790(v=pandp.10))的[字串作業 (英文)](/previous-versions/msp-n-p/ff647790(v=pandp.10)#string-operations)一節。
