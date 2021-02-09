---
title: 資料類別繼承 (O-R 設計工具)
description: 在物件關聯式設計工具的 (O/R 設計工具) （Visual Studio 中 LINQ to SQL 類別工具）中使用資料類別繼承。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4fed8d57359a6b4f7b6f64b283ed30c824ae32de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867057"
---
# <a name="data-class-inheritance-or-designer"></a>資料類別繼承 (O/R 設計工具)

LINQ to SQL 類別與其他物件一樣，可以使用繼承，也可以衍生自其他類別。 在程式碼中，您可以宣告某個類別是繼承自其他類別，指定物件之間的繼承關聯性。 在資料庫中，有數種方式可以建立繼承關聯性。 **物件關聯式設計工具** (**O/R 設計** 工具) 支援單一資料表繼承的概念，因為它通常是在關聯式系統中執行。

在單一資料表繼承中，有一種單一資料庫資料表，它包含了基底和衍生類別的資料行。 使用關聯式資料時，鑑別子資料行所含的值會決定某筆記錄所屬的類別 (Class)。 例如，假設有一個 `Persons` 資料表包含公司所採用的每個人。 有些人是員工，而有些人是經理。 `Persons`資料表包含名為的資料行 `Type` ，其管理員的值為1，而員工的值為2。 此資料 `Type` 行是鑒別子資料行。 在此案例中，您可以建立員工的子類別，並只將值為2的記錄填入類別 `Type` 。

當您使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 在實體類別中設定繼承時，請將包含繼承資料的單一資料表拖曳至設計工具兩次：繼承階層中的每個類別各一次。 將資料表新增至設計工具之後，請使用 [物件關聯式設計工具] 工具箱的 [繼承] 項目連接這些資料表，然後在 [屬性] 視窗中設定四個繼承屬性。

## <a name="inheritance-properties"></a>繼承屬性

下表列出繼承屬性及其描述：

|屬性|描述|
|--------------|-----------------|
|**鑑別子屬性**|這個屬性 (對應至資料行) 會判斷目前記錄所屬的類別。|
|**基底類別鑑別子值**|值 (在指定為 **鑒別子屬性** 的資料行中，) 判斷記錄是否為基類。|
|**衍生類別鑑別子值**|值 (在指定為 **鑒別子屬性** 的屬性中，) 判斷記錄是否為衍生類別。|
|**繼承預設值**|當指定為 **鑒別子屬性** 的屬性值不符合 **基類鑒別子值** 或 **衍生類別鑒別子值** 時，所填入的類別。|

建立使用繼承並對應至關聯式資料的物件模型在過程上較為複雜。 本主題提供設定繼承時，所需之基本概念和個別屬性的相關資訊。 下列主題提供如何使用 **O/R 設計** 工具設定繼承的更清楚說明。

|主題|描述|
|-----------|-----------------|
|[如何：使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|描述如何使用 **O/R 設計** 工具來設定使用單一資料表繼承的實體類別。|
|[逐步解說：使用單一資料表繼承來建立 LINQ to SQL 類別 (O/R 設計工具) ](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|提供逐步指示，說明如何使用 **O/R 設計** 工具來設定使用單一資料表繼承的實體類別。|

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說：建立 LINQ to SQL 類別 (O-R 設計工具)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [逐步解說：使用單一資料表繼承來建立 LINQ to SQL 類別 (O/R 設計工具) ](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [快速入門](/dotnet/framework/data/adonet/sql/linq/getting-started)
