---
title: LINQ to SQL O/R 設計工具總覽
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 55f6fa2ad9eda2d701563d1fa99c76f5cd5c7c1d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282003"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Visual Studio 中的 LINQ to SQL 工具

LINQ to SQL 是 Microsoft 所發行的第一個物件關聯式對應技術。 它在基本案例中運作良好，並繼續在 Visual Studio 中受到支援，但它已不再處於開發階段。 在維護已使用的繼承應用程式時，或在使用 SQL Server 且不需要多資料表對應的簡單應用程式中，請使用 LINQ to SQL。 一般而言，當需要物件關聯式對應程式層時，新的應用程式應該使用 Entity Framework。

## <a name="install-the-linq-to-sql-tools"></a>安裝 LINQ to SQL 工具

在 Visual Studio 中，您可以使用**物件關聯式設計工具**（**O/R 設計**工具），建立代表 SQL 資料表的 LINQ to SQL 類別。 O/R 設計工具是編輯 .dbml 檔案的 UI。 使用設計工具介面編輯 .dbml 檔案需要 LINQ to SQL 工具，預設不會安裝為 Visual Studio 任何工作負載的一部分。

若要安裝 LINQ to SQL 工具，請啟動 Visual Studio 安裝程式，選擇 [**修改**]，然後選取 [**個別元件**] 索引標籤，再選取 [程式**代碼工具**] 類別下的 [ **LINQ to SQL 工具**]。

## <a name="what-is-the-or-designer"></a>什麼是 O/R 設計工具

**O/R 設計**工具在其設計介面上有兩個不同的區域：左側的 [實體] 窗格和右邊的 [方法] 窗格。 實體窗格是主設計介面，可以顯示實體類別、關聯和繼承階層。 方法窗格的設計介面，則可以顯示對應至預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。

**O/R 設計**工具提供視覺化設計介面，可用來建立以資料庫中的物件為基礎的[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)實體類別和關聯（關係）。 換句話說， **O/R 設計**工具會在應用程式中建立對應至資料庫中物件的物件模型。 它也會產生強型別 <xref:System.Data.Linq.DataContext> ，以在實體類別與資料庫之間傳送和接收資料。 **O/R 設計**工具也提供將預存程式和函式對應至傳回 <xref:System.Data.Linq.DataContext> 資料和填入實體類別之方法的功能。 最後， **O/R 設計**工具可讓您設計實體類別之間的繼承關聯性。

## <a name="open-the-or-designer"></a>開啟 O/R 設計工具

若要將 LINQ to SQL 實體模型加入至您的專案，請選擇 [**專案**] [  >  **加入新專案**]，然後從專案專案清單中選取 [ **LINQ to SQL 類別**]：

![LINQ to SQL 類別](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio 會建立 *.dbml*檔案，並將它新增至您的方案。 這是 XML 對應檔及其相關的程式碼檔案。

![方案總管中的 LINQ to SQL 類別](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

當您選取 *.dbml*檔案時，Visual Studio 會顯示**O/R 設計**工具介面，可讓您以視覺化方式建立模型。 下圖顯示在 Northwind `Customers` 和 `Orders` 資料表從**伺服器總管**拖曳之後的設計工具。 請注意資料表之間的關聯性。

![LINQ to SQL 設計工具](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **O/R 設計**工具是一個簡單的物件關聯式對應程式，因為它只支援1:1 對應關聯性。 換句話說，實體類別與資料庫資料表或檢視之間只可以有一對一對應關聯性。 不支援複雜對應（例如，將實體類別對應至聯結資料表）。使用 Entity Framework 進行複雜的對應。 此外，這個設計工具是單向程式碼產生器。 這表示只有您對設計工具介面進行的變更才會反映在程式碼檔案中。 程式碼檔的手動變更不會反映在**O/R 設計**工具中。 儲存設計工具並重新產生程式碼時，會覆寫您在程式碼檔中進行的所有手動變更。 如需如何加入使用者程式碼及擴充產生之類別的詳細資訊**O/R Designer**，請參閱[How to:擴充 O/R 設計工具產生的程式碼](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)。

## <a name="create-and-configure-the-datacontext"></a>建立和設定 DataCoNtext

在您將 [ **LINQ to SQL 類別**] 專案加入至專案並開啟**O/R 設計**工具之後，空的設計介面 <xref:System.Data.Linq.DataContext> 就代表準備好要設定的空白。 <xref:System.Data.Linq.DataContext> 會使用第一個拖曳至設計介面之項目所提供的連接資訊來進行設定。 因此，<xref:System.Data.Linq.DataContext> 會使用第一個放入設計介面之項目的連接資訊來進行設定。 如需類別的詳細資訊 <xref:System.Data.Linq.DataContext> ，請參閱[DataCoNtext 方法（O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>建立對應至資料庫資料表和視圖的實體類別

您可以藉由將資料庫資料表和 views 從**伺服器總管**或**資料庫總管**拖曳至**O/R 設計**工具，來建立對應至資料表和視圖的實體類別。 如先前章節所示，第一個拖曳至設計介面之項目所提供的連接資訊會用於設定 <xref:System.Data.Linq.DataContext>。 如果在**O/R 設計**工具中加入了使用不同連接的後續專案，您可以變更的連接 <xref:System.Data.Linq.DataContext> 。 如需詳細資訊，請參閱[如何：建立對應至資料表和視圖的 LINQ to SQL 類別（O/R 設計工具）](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)。

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>建立可呼叫預存程式和函式的 DataCoNtext 方法

您可以藉 <xref:System.Data.Linq.DataContext> 由將預存程式和函式從**伺服器總管**或**資料庫總管**拖曳到**O/R 設計**工具上，來建立呼叫（對應至）的方法。 預存程式和函數會當做的方法加入至**O/R 設計**工具 <xref:System.Data.Linq.DataContext> 。

> [!NOTE]
> 當您將預存程式和函式從**伺服器總管**或**資料庫總管**拖曳至**O/R 設計**工具時，所產生方法的傳回型別會根據 <xref:System.Data.Linq.DataContext> 您放置專案的位置而有所不同。 如需詳細資訊，請參閱[DataCoNtext 方法（O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>設定 DataCoNtext 以使用預存程式來儲存實體類別和資料庫之間的資料

如前所述，您可以建立會呼叫預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。 此外，您也可以指派用於預設 LINQ to SQL 執行時間行為的預存程式，以執行插入、更新和刪除。 如需詳細資訊，請參閱[如何：指派預存程式來執行更新、插入和刪除（O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

## <a name="inheritance-and-the-or-designer"></a>繼承和 O/R 設計工具

就像其他物件一樣，LINQ to SQL 類別也可以使用繼承，並且衍生自其他類別。 在資料庫中，有數種方式可以建立繼承關聯性。 **O/R 設計**工具支援單一資料表繼承的概念，因為它通常是在關聯式系統中執行。 如需詳細資訊，請參閱[如何：使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)。

## <a name="linq-to-sql-queries"></a>LINQ to SQL 查詢

**O/R 設計**工具所建立的實體類別是設計用來與[語言整合式查詢（LINQ）](/dotnet/csharp/linq/)搭配使用。 如需詳細資訊，請參閱[如何：查詢資訊](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information)。

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>將產生的 DataCoNtext 和實體類別程式碼分隔為不同的命名空間

**O/R 設計**工具會在上提供**內容命名空間**和**實體命名空間**屬性 <xref:System.Data.Linq.DataContext> 。 這些屬性會決定 <xref:System.Data.Linq.DataContext> 和實體類別程式碼產生時，會落在哪一個命名空間 (Namespace) 中。 根據預設，這些屬性是空的，而且 <xref:System.Data.Linq.DataContext> 和實體類別產生時，會落在應用程式的命名空間中。 產生程式碼時，如果希望使用其他的命名空間，而非應用程式的命名空間，請在 [內容命名空間]**** 和/或 [實體命名空間]**** 屬性中輸入值。

## <a name="reference-content"></a>參考內容

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>另請參閱

- [LINQ to SQL （.NET Framework）](/dotnet/framework/data/adonet/sql/linq/index)
- [常見問題（.NET Framework）](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)
