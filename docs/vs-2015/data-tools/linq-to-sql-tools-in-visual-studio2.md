---
title: LINQ to SQL 工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 470cfabd54fa5f2b92001a635477c60d45fac538
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651508"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Visual Studio 中的 LINQ to SQL 工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL 是 Microsoft 所發行的第一個物件關聯式對應技術。 它在基本案例中運作良好，並繼續在 Visual Studio 中受到支援，但它已不再處於開發階段。 在維護已使用的繼承應用程式時，或在使用 SQL Server 且不需要多資料表對應的簡單應用程式中，請使用 LINQ to SQL。 一般而言，當需要物件關聯式對應程式層時，新的應用程式應該使用 Entity Framework。

 在 Visual Studio 中，您可以使用 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 來建立代表 SQL 資料表的 LINQ to SQL 類別。

 @No__t_0 在其設計介面上有兩個不同的區域：左側的 [實體] 窗格和右邊的 [方法] 窗格。 實體窗格是主設計介面，可以顯示實體類別、關聯和繼承階層。 方法窗格的設計介面，則可以顯示對應至預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。

 @No__t_0 （[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]）提供視覺化設計介面，可用來建立以資料庫中之物件為基礎的[LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)實體類別和關聯（關係）。 換句話說，[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]是用於建立應用程式中對應至資料庫內物件的物件模型。 它同時會產生可以在實體類別和資料庫之間傳送和接收資料的強型別 (Strongly Typed) 的 <xref:System.Data.Linq.DataContext>。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]也提供功能，將預存程序 (Stored Procedure) 和函式對應至 <xref:System.Data.Linq.DataContext> 方法，以傳回資料並填入 (Populate) 實體類別。 最後，[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]還可以設計實體類別之間的繼承 (Inheritance) 關聯性。

## <a name="opening-the-or-designer"></a>開啟 O/R 設計工具
 若要將 LINQ to SQL 實體模型加入至您的專案，請選擇 [  **&#124;專案] [加入新專案**]，然後從專案專案清單中選擇 [ **LINQ to SQL 類別**]：

 ![LINQ to SQL 類別](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL 類別")

 Visual Studio 會建立 .dbml 檔案，並將它新增至您的方案。 這是 XML 對應檔及其相關的程式碼檔案。

 ![方案總管中的 LINQ to SQL 類別](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "方案總管中的 raddata LINQ to SQL 類別")

 當您選取 .dbml 檔案時，Visual Studio 會顯示 O/R 設計工具介面，可讓您以視覺化方式建立模型。 下圖顯示 [Northwind Customers] 和 [Orders] 資料表從伺服器總管拖曳之後的設計工具。 請注意資料表之間的關聯性。

 ![LINQ to SQL 設計工具](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL 設計工具")

> [!IMPORTANT]
> @No__t_0 是簡單的物件關聯式對應程式，因為它只支援1:1 對應關聯性。 換句話說，實體類別與資料庫資料表或檢視之間只可以有一對一對應關聯性。 不支援複雜對應（例如，將實體類別對應至聯結資料表）。使用 Entity Framework 進行複雜的對應。 此外，這個設計工具是單向程式碼產生器。 這表示只有您對設計工具介面進行的變更才會反映在程式碼檔案中。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]中並不會反映程式碼檔的手動變更。 儲存設計工具並重新產生程式碼時，會覆寫您在程式碼檔中進行的所有手動變更。 如需如何加入使用者程式碼和擴充 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 所產生之類別的詳細資訊，請參閱[如何：擴充 O/R 設計工具所產生的程式碼](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)。

## <a name="creating-and-configuring-the-datacontext"></a>建立和設定 DataContext
 將 [ **LINQ to SQL 類別**] 專案加入至專案並開啟 [[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]] 之後，空的設計介面就代表準備好要設定的空 <xref:System.Data.Linq.DataContext>。 <xref:System.Data.Linq.DataContext> 是使用第一個拖曳至設計介面的專案所提供的連接資訊進行設定。 因此，<xref:System.Data.Linq.DataContext> 會使用第一個放入設計介面之項目的連接資訊來進行設定。 如需 <xref:System.Data.Linq.DataContext> 類別的詳細資訊，請參閱[DataCoNtext 方法（O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>建立對應至資料庫資料表和檢視的實體類別
 您可以將資料庫資料表和 views 從**伺服器總管**/**資料庫總管**拖曳到 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 上，藉以建立對應至資料表和視圖的實體類別。 如先前章節所示，第一個拖曳至設計介面之項目所提供的連接資訊會用於設定 <xref:System.Data.Linq.DataContext>。 如果後續又將使用不同連接的項目加入至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，您可以變更 <xref:System.Data.Linq.DataContext> 的連接。 如需詳細資訊，請參閱[如何：建立對應至資料表和視圖的 LINQ to SQL 類別（O/R 設計工具）](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)。

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>建立呼叫預存程序和函式的 DataContext 方法
 您可以將它們從**伺服器總管**/**資料庫總管**拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，以建立呼叫（對應至）預存程式和函式的 <xref:System.Data.Linq.DataContext> 方法。 預存程序和函式都會加入至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]做為 <xref:System.Data.Linq.DataContext> 的方法。

> [!NOTE]
> 當您將預存程式和函式從**伺服器總管**/**資料庫總管**拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 上時，所產生之 <xref:System.Data.Linq.DataContext> 方法的傳回型別會根據您放置專案的位置而有所不同。 如需詳細資訊，請參閱[DataCoNtext 方法（O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>設定 DataContext 使用預存程序在實體類別與資料庫之間儲存資料
 如前所述，您可以建立會呼叫預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。 此外，還可以指派預存程序來提供執行插入、更新和刪除作業時的預設 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 執行階段行為。 如需詳細資訊，請參閱[如何：指派預存程式來執行更新、插入和刪除（O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

## <a name="inheritance-and-the-or-designer"></a>繼承和 O/R 設計工具
 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 類別就像其他物件，可以使用繼承，也可以衍生自其他類別。 在資料庫中，有數種方式可以建立繼承關聯性。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]通常是在關聯式系統中實作，因此支援單一資料表繼承概念。 如需詳細資訊，請參閱[如何：使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)。

## <a name="linq-to-sql-queries"></a>LINQ to SQL 查詢
 @No__t_0 所建立的實體類別是專為搭配[LINQ （語言整合式查詢）](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)使用所設計。 如需詳細資訊，請參閱[如何：查詢資訊](https://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0)。

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>將產生的 DataContext 和實體類別程式碼分隔至不同的命名空間
 @No__t_0 會在 <xref:System.Data.Linq.DataContext> 上提供**內容命名空間**和**實體命名空間**屬性。 這些屬性會決定 <xref:System.Data.Linq.DataContext> 和實體類別程式碼產生時，會落在哪一個命名空間 (Namespace) 中。 根據預設，這些屬性是空的，而且 <xref:System.Data.Linq.DataContext> 和實體類別產生時，會落在應用程式的命名空間中。 產生程式碼時，如果希望使用其他的命名空間，而非應用程式的命名空間，請在 [內容命名空間] 和/或 [實體命名空間] 屬性中輸入值。

## <a name="in-this-section"></a>本節內容
 [DataCoNtext 方法（O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)說明 <xref:System.Data.Linq.DataContext> 方法是什麼，以及如何建立它們。

 [資料類別繼承（O/R 設計工具）](../data-tools/data-class-inheritance-o-r-designer.md)描述單一資料表繼承的概念，以及如何在 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 中執行它。

 [如何：建立對應至資料表和視圖的 LINQ to SQL 類別（O/R 設計工具）](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)描述如何建立對應至資料庫中之資料表和 views 的實體類別。

 [如何：在 LINQ to SQL 類別之間建立關聯（關聯性）（O/R 設計工具）](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)描述如何建立 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 實體類別之間的關聯性。

 [如何：建立對應至預存程式和函式的 DataCoNtext 方法（O/R 設計工具）](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)描述如何建立在呼叫預存程式或函式時執行的 <xref:System.Data.Linq.DataContext> 方法。

 [如何：指派用來執行更新、插入和刪除的預存程式（O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)描述如何設定 <xref:System.Data.Linq.DataContext>，以在將實體類別的資料儲存回資料庫時使用預存程式。

 [如何：變更 DataCoNtext 方法的傳回型別（O/R 設計工具）](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)描述如何將 <xref:System.Data.Linq.DataContext> 方法的傳回型別設定為實體類別的型別，或 O/R 設計工具所建立的自動產生型別。

 [如何：將驗證加入至實體類別](../data-tools/how-to-add-validation-to-entity-classes.md)描述如何產生部分方法，以便在屬性變更和實體類別更新期間加入程式碼。

 [如何：開啟和關閉複數表示（O/R 設計工具）](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)描述如何開啟和關閉新增至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 之類別的自動重新命名。

 [如何：使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)描述如何使用 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 的單一資料表繼承來設定實體類別。

 [如何：擴充 O/R 設計工具產生的程式碼](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)描述當 O/R 設計工具上的物件變更時，如何及何處新增不會覆寫的程式碼。

 [逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別（O/R 設計工具）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)提供逐步指示，說明如何使用 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 的單一資料表繼承來設定實體類別。

 [逐步解說：自訂實體類別的插入、更新和刪除行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)提供逐步指示，說明如何設定在將實體類別的資料儲存回資料庫時使用預存程式的 <xref:System.Data.Linq.DataContext>。

## <a name="reference-content"></a>參考內容
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>請參閱
 [Visual Studio data tools for .Net](../data-tools/visual-studio-data-tools-for-dotnet.md) [常見問題](https://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [存取中的資料 Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
