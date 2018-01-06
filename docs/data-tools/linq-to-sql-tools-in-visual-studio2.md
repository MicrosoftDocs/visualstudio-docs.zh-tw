---
title: "Visual Studio O/R 設計工具概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a160cce25814cd2e110f8896ed6752a18b5dd0da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL 工具，Visual Studio 中
LINQ to SQL 是 Microsoft 所發行的第一個物件關聯式對應技術。 它適用於基本案例，並繼續在 Visual Studio 中，支援，但不再是真的開發。 使用 LINQ to SQL 時維護舊版的應用程式已使用它，或在使用 SQL Server，且不需要多重資料表對應的簡單應用程式。 一般情況下，新的應用程式需要的物件關聯對應程式層級時，應該使用 Entity Framework。  
  
在 Visual Studio 中，您可以建立 LINQ to SQL 類別使用物件關聯式設計工具 （O/R 設計工具） 來表示 SQL 資料表。  
  
[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]具有其設計介面上的兩個不同區域： 左邊的 [實體] 窗格和右邊的 [方法] 窗格。 實體窗格是主設計介面，可以顯示實體類別、關聯和繼承階層。 方法窗格是顯示在設計介面<xref:System.Data.Linq.DataContext>會對應至預存程序和函式的方法。  
  
[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]提供視覺化設計介面建立[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)實體類別和資料庫中的物件為基礎的關聯 （關聯性）。 換句話說，[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]是用於建立應用程式中對應至資料庫內物件的物件模型。 它同時會產生可以在實體類別和資料庫之間傳送和接收資料的強型別 (Strongly Typed) 的 <xref:System.Data.Linq.DataContext>。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]也提供功能，將預存程序 (Stored Procedure) 和函式對應至 <xref:System.Data.Linq.DataContext> 方法，以傳回資料並填入 (Populate) 實體類別。 最後，[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]還可以設計實體類別之間的繼承 (Inheritance) 關聯性。  
  
## <a name="opening-the-or-designer"></a>開啟 O/R 設計工具  
 若要加入 LINQ to SQL 實體模型，您的專案，選擇**專案**，**加入新項目**，然後選擇  **LINQ to SQL 類別**清單中的專案項目：  
  
 ![LINQ to SQL 類別](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL 類別")  
  
 Visual Studio 建立.dbml 檔，並將它加入至您的方案。 這是 XML 對應檔案和其相關的程式碼檔案。  
  
 ![在 [方案總管] 中的 LINQ to SQL 類別](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL 類別在 方案總管")  
  
 當您選取的.dbml 檔案時，Visual Studio 會顯示在 O/R 設計工具介面，可讓您以視覺化方式建立模型。 已從伺服器總管 拖曳 Northwind Customers 和 Orders 資料表之後下, 圖顯示在設計工具。 請注意資料表之間的關聯性。  
  
 ![LINQ 到 SQL 設計師](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL 設計工具")  
  
> [!IMPORTANT]
>  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]是簡單的物件關聯式對應工具 」，因為它支援僅 1:1 對應關係。 換句話說，實體類別與資料庫資料表或檢視之間只可以有一對一對應關聯性。 不支援複雜對應，例如將實體類別對應至聯結的資料表;針對複雜的對應都使用 Entity Framework。 此外，這個設計工具是單向程式碼產生器。 這表示只有您對設計工具介面進行的變更才會反映在程式碼檔案中。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中並不會反映程式碼檔的手動變更。 儲存設計工具並重新產生程式碼時，會覆寫您在程式碼檔中進行的所有手動變更。 如需有關如何加入使用者程式碼和擴充所產生的類別資訊[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，請參閱[如何： 擴充 O/R 設計工具所產生程式碼](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)。  
  
## <a name="creating-and-configuring-the-datacontext"></a>建立和設定 DataContext  
 您將加入之後**LINQ to SQL 類別**項目至專案並開啟[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，空的設計介面即代表空<xref:System.Data.Linq.DataContext>可供設定。 <xref:System.Data.Linq.DataContext>設定第一個拖曳到設計介面上的項目所提供的連接資訊... 因此，<xref:System.Data.Linq.DataContext>已使用從第一個項目拖曳至設計介面上卸除的連接資訊。 如需有關<xref:System.Data.Linq.DataContext>類別，請參閱[DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>建立對應至資料庫資料表和檢視的實體類別  
 您可以建立實體類別對應至資料表和檢視表，藉由拖曳資料庫資料表和檢視表從**伺服器總管**/**資料庫總管**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 如先前章節所示，第一個拖曳至設計介面之項目所提供的連接資訊會用於設定 <xref:System.Data.Linq.DataContext>。 如果後續又將使用不同連接的項目加入至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，您可以變更 <xref:System.Data.Linq.DataContext> 的連接。 如需詳細資訊，請參閱[How to： 建立 LINQ to SQL 類別對應至資料表和檢視 （O/R 設計工具）](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)。  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>建立呼叫預存程序和函式的 DataContext 方法  
 您可以建立<xref:System.Data.Linq.DataContext>呼叫的方法 （對應至） 預存程序和函數拖曳的方式從**伺服器總管**/**資料庫總管**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. 預存程序和函式都會加入至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]做為 <xref:System.Data.Linq.DataContext> 的方法。  
  
> [!NOTE]
>  當您拖曳預存程序和函式從**伺服器總管**/**資料庫總管**拖曳至[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，產生的傳回型別<xref:System.Data.Linq.DataContext>方法視您卸除項目。 如需詳細資訊，請參閱[DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>設定 DataContext 使用預存程序在實體類別與資料庫之間儲存資料  
 如前所述，您可以建立會呼叫預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。 此外，還可以指派預存程序來提供執行插入、更新和刪除作業時的預設 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 執行階段行為。 如需詳細資訊，請參閱[如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。  
  
## <a name="inheritance-and-the-or-designer"></a>繼承和 O/R 設計工具  
 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 類別就像其他物件，可以使用繼承，也可以衍生自其他類別。 在資料庫中，有數種方式可以建立繼承關聯性。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]通常是在關聯式系統中實作，因此支援單一資料表繼承概念。 如需詳細資訊，請參閱[How to： 使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)。  
  
## <a name="linq-to-sql-queries"></a>LINQ to SQL 查詢  
 所建立的實體類別[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]專為搭配[LINQ (Language-Integrated Query ()](/dotnet/csharp/linq/)。 如需詳細資訊，請參閱[如何： 查詢資訊](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information)。  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>將產生的 DataContext 和實體類別程式碼分隔至不同的命名空間  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]提供**內容命名空間**和**實體命名空間**屬性<xref:System.Data.Linq.DataContext>。 這些屬性會決定 <xref:System.Data.Linq.DataContext> 和實體類別程式碼產生時，會落在哪一個命名空間 (Namespace) 中。 根據預設，這些屬性是空的，而且 <xref:System.Data.Linq.DataContext> 和實體類別產生時，會落在應用程式的命名空間中。 若要產生的程式碼到應用程式的命名空間以外的命名空間，請輸入值**內容命名空間**及/或**實體命名空間**屬性。
  
## <a name="reference-content"></a>參考內容
<xref:System.Linq>  
<xref:System.Data.Linq>  
  
## <a name="see-also"></a>另請參閱
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)    
[常見問題集 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions) 