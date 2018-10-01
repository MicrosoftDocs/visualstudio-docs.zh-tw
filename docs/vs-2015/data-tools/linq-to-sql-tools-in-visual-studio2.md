---
title: LINQ to SQL 工具，在 Visual 2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19d9bccad36a186c93aeb8aef8e93b63320a00d2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486263"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL 工具，在 Visual Studio 中
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[LINQ to SQL 工具，在 Visual 2](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。  
  
  
LINQ to SQL 是 Microsoft 所發行的第一個物件關聯式對應技術。 其運作方式也在基本案例中，並會繼續支援在 Visual Studio 中，但不再進行開發。 使用 LINQ to SQL 時維護舊版的應用程式已使用它，或使用 SQL Server，而且不需要多重資料表對應的簡單應用程式中。 一般情況下，新的應用程式在需要物件關聯式對應程式層時，應該使用 Entity Framework。  
  
 在 Visual Studio 中，您必須建立 LINQ to SQL 類別表示 SQL 資料表使用[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。  
  
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]具有其設計介面上的兩個不同區域： 左邊的 [實體] 窗格和右邊的 [方法] 窗格。 實體窗格是主設計介面，可以顯示實體類別、關聯和繼承階層。 方法窗格是顯示在設計介面<xref:System.Data.Linq.DataContext>會對應至預存程序和函式的方法。  
  
 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) 提供視覺化設計介面建立[LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)實體類別和資料庫中的物件為基礎的關聯 （關聯性）。 換句話說，[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]是用於建立應用程式中對應至資料庫內物件的物件模型。 它同時會產生可以在實體類別和資料庫之間傳送和接收資料的強型別 (Strongly Typed) 的 <xref:System.Data.Linq.DataContext>。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]也提供功能，將預存程序 (Stored Procedure) 和函式對應至 <xref:System.Data.Linq.DataContext> 方法，以傳回資料並填入 (Populate) 實體類別。 最後，[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]還可以設計實體類別之間的繼承 (Inheritance) 關聯性。  
  
## <a name="opening-the-or-designer"></a>開啟 O/R 設計工具  
 若要加入 LINQ to SQL 實體模型至您的專案，選擇**專案&#124;加入新項目**，然後選擇  **LINQ to SQL 類別**清單中的專案項目：  
  
 ![LINQ to SQL 類別](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL 類別")  
  
 Visual Studio 建立.dbml 檔，並將它新增至您的解決方案。 這是 XML 對應檔案和其相關的程式碼檔案。  
  
 ![在 [方案總管] 中的 LINQ to SQL 類別](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL 類別在 方案總管")  
  
 當您選取.dbml 檔案時，Visual Studio 會顯示在 O/R 設計工具介面，可讓您以視覺化方式建立模型。 已從伺服器總管 中拖曳的 Northwind Customers 和 Orders 資料表之後下, 圖顯示設計工具。 請注意資料表之間的關聯性。  
  
 ![LINQ to SQL 設計工具](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL 設計工具")  
  
> [!IMPORTANT]
>  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]是簡單的物件關聯式對應程式，因為它支援僅為 1:1 對應關聯性。 換句話說，實體類別與資料庫資料表或檢視之間只可以有一對一對應關聯性。 不支援複雜的對應，例如實體類別對應至聯結的資料表;使用 Entity Framework 進行複雜的對應。 此外，這個設計工具是單向程式碼產生器。 這表示只有您對設計工具介面進行的變更才會反映在程式碼檔案中。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]中並不會反映程式碼檔的手動變更。 儲存設計工具並重新產生程式碼時，會覆寫您在程式碼檔中進行的所有手動變更。 如需如何加入使用者程式碼及擴充產生之類別的詳細資訊[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，請參閱 <<c2> [ 如何： 擴充 O/R 設計工具程式碼產生](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)。  
  
## <a name="creating-and-configuring-the-datacontext"></a>建立和設定 DataContext  
 新增之後**LINQ to SQL 類別**項目至專案並開啟[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，空的設計介面表示空<xref:System.Data.Linq.DataContext>準備好進行設定。 <xref:System.Data.Linq.DataContext>設有拖曳到設計介面上的第一個項目所提供的連接資訊... 因此，<xref:System.Data.Linq.DataContext>已使用從第一個項目拖曳至設計介面的連接資訊。 如需詳細資訊<xref:System.Data.Linq.DataContext>類別，請參閱 < [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>建立對應至資料庫資料表和檢視的實體類別  
 您可以建立實體類別對應到資料表和檢視表的資料庫資料表和檢視表從拖曳**伺服器總管**/**資料庫總管**拖曳至[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。 如先前章節所示，第一個拖曳至設計介面之項目所提供的連接資訊會用於設定 <xref:System.Data.Linq.DataContext>。 如果後續又將使用不同連接的項目加入至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，您可以變更 <xref:System.Data.Linq.DataContext> 的連接。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立的 LINQ to SQL 類別對應至資料表和檢視 （O/R 設計工具）](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)。  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>建立呼叫預存程序和函式的 DataContext 方法  
 您可以建立<xref:System.Data.Linq.DataContext>呼叫的方法 （對應至） 預存程序和函式將它們從拖曳**伺服器總管**/**資料庫總管**到[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. 預存程序和函式都會加入至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]做為 <xref:System.Data.Linq.DataContext> 的方法。  
  
> [!NOTE]
>  當您將預存程序和函式從**伺服器總管**/**資料庫總管**拖曳至[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，所產生的傳回類型<xref:System.Data.Linq.DataContext>方法不同視您卸除項目。 如需詳細資訊，請參閱 < [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>設定 DataContext 使用預存程序在實體類別與資料庫之間儲存資料  
 如前所述，您可以建立會呼叫預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。 此外，還可以指派預存程序來提供執行插入、更新和刪除作業時的預設 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 執行階段行為。 如需詳細資訊，請參閱 <<c0> [ 如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。  
  
## <a name="inheritance-and-the-or-designer"></a>繼承和 O/R 設計工具  
 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 類別就像其他物件，可以使用繼承，也可以衍生自其他類別。 在資料庫中，有數種方式可以建立繼承關聯性。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]通常是在關聯式系統中實作，因此支援單一資料表繼承概念。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)。  
  
## <a name="linq-to-sql-queries"></a>LINQ to SQL 查詢  
 所建立的實體類別[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]專為搭配[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)。 如需詳細資訊，請參閱 <<c0> [ 如何： 查詢資訊](http://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0)。  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>將產生的 DataContext 和實體類別程式碼分隔至不同的命名空間  
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]提供**內容命名空間**並**實體命名空間**上的屬性<xref:System.Data.Linq.DataContext>。 這些屬性會決定 <xref:System.Data.Linq.DataContext> 和實體類別程式碼產生時，會落在哪一個命名空間 (Namespace) 中。 根據預設，這些屬性是空的，而且 <xref:System.Data.Linq.DataContext> 和實體類別產生時，會落在應用程式的命名空間中。 若要產生程式碼應用程式的命名空間以外的命名空間時，輸入 值**內容命名空間**及/或**實體命名空間**屬性。  
  
## <a name="in-this-section"></a>本節內容  
 [DataContext 方法 (O/R 設計工具)](../data-tools/datacontext-methods-o-r-designer.md)  
 說明何謂 <xref:System.Data.Linq.DataContext> 方法及其建立方式。  
  
 [資料類別繼承 (O/R 設計工具)](../data-tools/data-class-inheritance-o-r-designer.md)  
 說明單一資料表繼承的概念，以及它在 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]中的實作方式。  
  
 [如何：建立對應至資料表和檢視的 LINQ to SQL 類別 (O/R 設計工具)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)  
 說明如何建立實體類別，以對應至資料庫中的資料表和檢視。  
  
 [如何：建立 LINQ to SQL 類別之間的關聯 (關聯性) (O/R 設計工具)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)  
 說明如何建立 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 實體類別之間的關聯性。  
  
 [如何：建立對應至預存程序和函式的 DataContext 方法 (O/R 設計工具)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)  
 說明如何建立 <xref:System.Data.Linq.DataContext> 方法，以在呼叫時執行預存程序或函式。  
  
 [如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
 說明如何設定 <xref:System.Data.Linq.DataContext>，以在將實體類別的資料儲存回資料庫時使用預存程序。  
  
 [如何：變更 DataContext 方法的傳回型別 (O/R 設計工具)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)  
 說明如何將 <xref:System.Data.Linq.DataContext> 方法的傳回型別設定為實體類別的型別或 O/R 設計工具自動產生的型別。  
  
 [如何：將驗證新增至實體類別](../data-tools/how-to-add-validation-to-entity-classes.md)  
 說明如何產生部分方法，以加入在屬性變更及實體類別更新期間呼叫的程式碼。  
  
 [如何：開啟和關閉複數表示 (O/R 設計工具)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)  
 說明如何開啟和關閉已加入 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]中之類別自動重新命名的功能。  
  
 [如何：使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)  
 說明如何搭配 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，使用單一資料表繼承設定實體類別。  
  
 [如何：擴充 O/R 設計工具產生的程式碼](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)  
 說明程式碼加入的方法以及位置，才不致在 O/R 設計工具上的物件變更而程式碼重新產生時，覆寫程式碼。  
  
 [逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 (O/R 設計工具)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)  
 提供逐步指示，說明如何搭配 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，使用單一資料表繼承設定實體類別。  
  
 [逐步解說：自訂實體類別的插入、更新和刪除行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
 提供逐步指示，說明如何設定 <xref:System.Data.Linq.DataContext>，以在將實體類別的資料儲存回資料庫時使用預存程序。  
  
## <a name="reference-content"></a>參考內容  
 <xref:System.Linq>  
  
 <xref:System.Data.Linq>  
  
## <a name="see-also"></a>另請參閱  
 [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [常見問題集](http://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)

