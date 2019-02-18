---
title: 資料類別繼承 (O-R 設計工具)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a8df3d39e44bf1d40f3abfd4d6218d2c9a72b690
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935676"
---
# <a name="data-class-inheritance-or-designer"></a>資料類別繼承 (O/R 設計工具)

其他物件，例如 LINQ to SQL 類別可以使用繼承，也可以衍生自其他類別。 在程式碼中，您可以宣告某個類別是繼承自其他類別，指定物件之間的繼承關聯性。 在資料庫中，有數種方式可以建立繼承關聯性。 **物件關聯式設計工具**(**O/R Designer**) 支援的單一資料表繼承概念，通常是在關聯式系統中實作。

在單一資料表繼承中，有一種單一資料庫資料表，它包含了基底和衍生類別的資料行。 使用關聯式資料時，鑑別子資料行所含的值會決定某筆記錄所屬的類別 (Class)。 例如，假設`Persons`包含某家公司雇用的所有人的資料表。 有些人是員工，而有些人是經理。 `Persons`資料表包含資料行名為`Type`經理和 2 的值具有值為 1 的員工。 `Type`資料行是鑑別子資料行。 在此案例中，您可以建立員工子類別，並填入具有的記錄類別`Type`值為 2。

當您使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 在實體類別中設定繼承時，請將包含繼承資料的單一資料表拖曳至設計工具兩次：繼承階層中的每個類別各一次。 將資料表新增至設計工具之後，請使用 [物件關聯式設計工具] 工具箱的 [繼承] 項目連接這些資料表，然後在 [屬性] 視窗中設定四個繼承屬性。

## <a name="inheritance-properties"></a>繼承屬性

下表列出繼承屬性及其描述：

|屬性|描述|
|--------------|-----------------|
|**鑑別子屬性**|這個屬性 (對應至資料行) 會判斷目前記錄所屬的類別。|
|**基底類別鑑別子值**|這個值 (在指定為**鑑別子屬性**的資料行中) 會判斷記錄是否為基底類別。|
|**衍生類別鑑別子值**|這個值 (在指定為**鑑別子屬性**的屬性中) 會判斷記錄是否為衍生類別。|
|**繼承預設值**|屬性中的值指定為時，會填入類別**鑑別子屬性**不符合**基底類別鑑別子值**或**衍生的類別鑑別子值**。|

建立使用繼承並對應至關聯式資料的物件模型在過程上較為複雜。 本主題提供設定繼承時，所需之基本概念和個別屬性的相關資訊。 下列主題提供更清楚的說明，如何設定的繼承**O/R Designer**。

|主題|描述|
|-----------|-----------------|
|[如何：使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|描述如何設定實體類別，透過使用單一資料表繼承**O/R Designer**。|
|[逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 (O/R 設計工具)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|提供逐步指示如何設定實體類別，透過使用單一資料表繼承**O/R Designer**。|

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說：建立 LINQ to SQL 類別 (O-R 設計工具)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 (O/R 設計工具)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [快速入門](/dotnet/framework/data/adonet/sql/linq/getting-started)