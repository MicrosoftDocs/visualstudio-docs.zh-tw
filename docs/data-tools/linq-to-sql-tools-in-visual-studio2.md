---
title: O/R 設計工具概觀
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 0c4b3c752a2ca28c4cfb4b08b2f51f8b8fc6ac23
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894151"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Visual Studio 中的 LINQ to SQL 工具

LINQ to SQL 是 Microsoft 所發行的第一個物件關聯式對應技術。 其運作方式也在基本案例中，並會繼續支援在 Visual Studio 中，但不再進行開發。 使用 LINQ to SQL 時維護舊版的應用程式已使用它，或使用 SQL Server，而且不需要多重資料表對應的簡單應用程式中。 一般情況下，新的應用程式在需要物件關聯式對應程式層時，應該使用 Entity Framework。

在 Visual Studio 中，您必須建立 LINQ to SQL 類別，代表所使用的 SQL 資料表**物件關聯式設計工具**(**O/R Designer**)。

**O/R Designer**具有其設計介面上的兩個不同區域： 左邊的 [實體] 窗格和右邊的 [方法] 窗格。 實體窗格是主設計介面，可以顯示實體類別、關聯和繼承階層。 方法窗格的設計介面，則可以顯示對應至預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。

**O/R Designer**提供視覺化設計介面建立[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)實體類別和資料庫中的物件為基礎的關聯 （關聯性）。 亦即**O/R Designer**對應至資料庫中物件的應用程式中建立物件模型。 它也會產生強型別<xref:System.Data.Linq.DataContext>，傳送和接收實體類別與資料庫之間的資料。 **O/R Designer**也提供功能來對應預存程序和函式<xref:System.Data.Linq.DataContext>方法以傳回資料並填入實體類別。 最後， **O/R Designer**提供設計實體類別之間的繼承關聯性的能力。

## <a name="open-the-or-designer"></a>開啟 O/R 設計工具

若要加入 LINQ to SQL 實體模型至您的專案，選擇**專案** > **加入新項目**，然後選取**LINQ to SQL 類別**從清單中的專案項目：

![LINQ to SQL 類別](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio 會建立 *.dbml*檔案，並將它新增至您的解決方案。 這是 XML 對應檔案和其相關的程式碼檔案。

![LINQ to SQL 類別，在 方案總管](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

當您選取 *.dbml*檔案，Visual Studio 會顯示**O/R Designer**介面，可讓您以視覺化方式建立模型。 下圖顯示設計工具之後 Northwind`Customers`並`Orders`資料表已從拖曳**伺服器總管**。 請注意資料表之間的關聯性。

![LINQ to SQL 設計工具](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **O/R Designer**是簡單的物件關聯式對應程式，因為它支援僅為 1:1 對應關聯性。 換句話說，實體類別與資料庫資料表或檢視之間只可以有一對一對應關聯性。 不支援複雜的對應，例如實體類別對應至聯結的資料表;使用 Entity Framework 進行複雜的對應。 此外，這個設計工具是單向程式碼產生器。 這表示只有您對設計工具介面進行的變更才會反映在程式碼檔案中。 在程式碼檔案的手動變更不會反映在**O/R Designer**。 儲存設計工具並重新產生程式碼時，會覆寫您在程式碼檔中進行的所有手動變更。 如需如何加入使用者程式碼及擴充產生之類別的詳細資訊**O/R Designer**，請參閱[How to:擴充 O/R 設計工具產生的程式碼](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)。

## <a name="create-and-configure-the-datacontext"></a>建立和設定 DataContext

新增之後**LINQ to SQL 類別**項目至專案並開啟**O/R Designer**，空的設計介面表示空<xref:System.Data.Linq.DataContext>準備好進行設定。 <xref:System.Data.Linq.DataContext> 會使用第一個拖曳至設計介面之項目所提供的連接資訊來進行設定。 因此，<xref:System.Data.Linq.DataContext> 會使用第一個放入設計介面之項目的連接資訊來進行設定。 如需詳細資訊<xref:System.Data.Linq.DataContext>類別，請參閱 < [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>建立實體類別對應至資料庫資料表和檢視表

您可以建立實體類別對應到資料表和檢視表的資料庫資料表和檢視表從拖曳**伺服器總管**或**資料庫總管**拖曳至**O/R Designer**。 如先前章節所示，第一個拖曳至設計介面之項目所提供的連接資訊會用於設定 <xref:System.Data.Linq.DataContext>。 如果使用不同連接的後續項目會新增至**O/R Designer**，您可以變更連接<xref:System.Data.Linq.DataContext>。 如需詳細資訊，請參閱[＜How to：建立對應至資料表和檢視的 LINQ to SQL 類別 (O/R 設計工具)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)。

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>建立呼叫預存程序和函式的 DataContext 方法

您可以建立<xref:System.Data.Linq.DataContext>呼叫的方法 （對應至） 預存程序和函式從**伺服器總管**或是**資料庫總管**拖曳至**O/R 設計工具**. 預存程序和函式會加入至**O/R Designer**做為方法的<xref:System.Data.Linq.DataContext>。

> [!NOTE]
> 當您將預存程序和函式從**伺服器總管**或**資料庫總管**拖曳至**O/R 設計工具**，所產生的傳回類型<xref:System.Data.Linq.DataContext>方法會依據您卸除項目而有所不同。 如需詳細資訊，請參閱 < [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>設定 DataContext 使用預存程序，將實體類別與資料庫之間的資料儲存

如前所述，您可以建立會呼叫預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。 此外，您也可以指派用於的預設 LINQ to SQL 的執行階段行為，以執行插入、 更新和刪除的預存程序。 如需詳細資訊，請參閱[＜How to：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

## <a name="inheritance-and-the-or-designer"></a>繼承和 O/R 設計工具

其他物件，例如 LINQ to SQL 類別可以使用繼承，也可以衍生自其他類別。 在資料庫中，有數種方式可以建立繼承關聯性。 **O/R Designer**支援單一資料表繼承概念，通常是在關聯式系統中實作。 如需詳細資訊，請參閱[＜How to：使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)。

## <a name="linq-to-sql-queries"></a>LINQ to SQL 查詢

所建立的實體類別**O/R Designer**專為搭配[Language Integrated query (LINQ)](/dotnet/csharp/linq/)。 如需詳細資訊，請參閱[＜How to：如需資訊的查詢](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information)。

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>將產生的 DataContext 和實體類別程式碼分成不同的命名空間

**O/R Designer**提供**內容命名空間**並**實體命名空間**上的屬性<xref:System.Data.Linq.DataContext>。 這些屬性會決定 <xref:System.Data.Linq.DataContext> 和實體類別程式碼產生時，會落在哪一個命名空間 (Namespace) 中。 根據預設，這些屬性是空的，而且 <xref:System.Data.Linq.DataContext> 和實體類別產生時，會落在應用程式的命名空間中。 產生程式碼時，如果希望使用其他的命名空間，而非應用程式的命名空間，請在 [內容命名空間] 和/或 [實體命名空間] 屬性中輸入值。

## <a name="reference-content"></a>參考內容

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>另請參閱

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [常見問題的解答 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)