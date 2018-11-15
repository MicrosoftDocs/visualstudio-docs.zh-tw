---
title: 建構資料表設計工具的篩選字串 |Microsoft Docs
description: 建構資料表設計工具的篩選字串
author: ghogen
manager: douge
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: ff8c3dd927e81b9e131242a9a6631a8297046a6e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001967"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>為資料表設計工具設計篩選字串架構
## <a name="overview"></a>總覽
在隨即出現在 Visual Studio 中的 Azure 資料表中篩選資料**資料表設計工具**，建構篩選字串，並在篩選欄位中輸入它。 篩選條件字串語法由 WCF Data Services 定義類似於 SQL WHERE 子句，而且會傳送至表格服務透過 HTTP 要求。 **資料表設計工具**處理適當的編碼，所以若要篩選所需的屬性值，您需要只輸入屬性名稱、 比較運算子、 準則值和 （選擇性） 布林值篩選 欄位中的運算子。 您不需要像建構 URL 來查詢透過資料表一樣包含 $filter 查詢選項[儲存體服務 REST API 參考](http://go.microsoft.com/fwlink/p/?LinkId=400447)。

WCF Data Services 為基礎[開放式資料通訊協定](http://go.microsoft.com/fwlink/p/?LinkId=214805)(OData)。 如需有關篩選系統查詢選項 (**$filter**)，請參閱[OData URI 轉換規格](http://go.microsoft.com/fwlink/p/?LinkId=214806)。

## <a name="comparison-operators"></a>比較運算子
所有屬性類型都支援下列的邏輯運算子：

| 邏輯運算子 | 描述 | 範例篩選字串 |
| --- | --- | --- |
| eq |等於 |City eq 'Redmond' |
| gt |大於 |價格 t 20 |
| ge |大於或等於 |價格 ge 10 |
| lt |小於 |價格 l 20 |
| le |小於或等於 |價格 le 100 |
| ne |不相等 |縣 （市) ne 'London' |
| 和 |及 |價格 le 200 和價格 t 3.5 |
| 或 |或 |價格 le 3.5 或價格 t 200 |
| not |not |不 isAvailable |

建構篩選字串時，下列規則很重要：

* 您可以使用邏輯運算子來比較屬性與值。 請注意，不可能比較屬性與動態值;運算式的一端必須是常數。
* 篩選條件字串的所有部分都都區分大小寫的。
* 常數的值必須是相同的資料類型中，篩選的屬性來傳回有效的結果。 如需支援的屬性類型的詳細資訊，請參閱[了解表格服務資料模型](http://go.microsoft.com/fwlink/p/?LinkId=400448)。

## <a name="filtering-on-string-properties"></a>篩選字串屬性
當您篩選字串屬性時，請用單引號括住字串常數。

下列範例會篩選**PartitionKey**並**RowKey**屬性; 其他的非索引鍵屬性也可以加入至篩選字串：

    PartitionKey eq 'Partition1' and RowKey eq '00001'

您可以每個篩選條件運算式括號括住，雖然這並非必要：

    (PartitionKey eq 'Partition1') and (RowKey eq '00001')

請注意，表格服務不支援萬用字元查詢中，它們不支援在資料表設計工具是。 不過，您可以執行比對的所需的前置詞上使用比較運算子的前置詞。 下列範例會傳回 LastName 屬性開頭為字母 'A' 有實體：

    LastName ge 'A' and LastName lt 'B'

## <a name="filtering-on-numeric-properties"></a>篩選數值屬性
若要篩選整數或浮點數，指定數值且不加引號。

這個範例會傳回與 Age 屬性，其值大於 30 的所有實體：

    Age gt 30

這個範例會傳回與 AmountDue 屬性的值小於或等於 100.25 的所有實體：

    AmountDue le 100.25

## <a name="filtering-on-boolean-properties"></a>篩選布林值屬性
若要篩選布林值，指定 **，則為 true**或是**false**且不加引號。

下列範例會傳回所有實體，IsActive 屬性設定為 **，則為 true**:

    IsActive eq true

您也可以撰寫這個篩選條件運算式，而不需要使用的邏輯運算子。 在下列範例中，表格服務也會傳回所有實體所在 IsActive **，則為 true**:

    IsActive

若要傳回 IsActive 為 false 的所有實體，您可以使用 not 運算子：

    not IsActive

## <a name="filtering-on-datetime-properties"></a>篩選 DateTime 屬性
若要篩選的日期時間值，指定**datetime**關鍵字，後面接著以單引號的日期/時間常數。 日期/時間常數必須是 UTC 組合格式，如中所述[格式化 DateTime 屬性值](http://go.microsoft.com/fwlink/p/?LinkId=400449)。

下列範例會傳回 CustomerSince 屬性等於 2008 年 7 月 10 日的實體：

    CustomerSince eq datetime'2008-07-10T00:00:00Z'
