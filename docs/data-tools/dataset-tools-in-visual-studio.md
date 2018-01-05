---
title: "Visual Studio 中的資料集工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a8c8660fbc489dd8c4926bb09b8b42006da0897a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio 中的資料集工具
> [!NOTE]
>  資料集和相關的類別會讓應用程式處理記憶體中資料的應用程式的連接會中斷資料庫早期 2000s年從舊版.NET 技術。 它們是特別適用於應用程式可讓使用者修改資料，並保存回資料庫的變更。 雖然資料集證明為十分成功的技術，我們建議新的.NET 應用程式使用 Entity Framework。 Entity Framework 提供更自然的方式來使用物件模型，為表格式資料，並且有更簡單的程式設計介面。  
  
 資料集物件是記憶體中物件，基本上是小型的資料庫。 它包含資料表、 DataColumn 和 DataRow 物件可以儲存並修改一或多個資料庫中的資料，而不需要維護的開啟連接。 資料集維護其資料，以變更的相關資訊，以便將追蹤更新，並重新連接您的應用程式時，傳送回資料庫。  
  
 .NET Framework 類別庫中的 System.Data 命名空間中定義資料集和相關的類別。 您可以建立和修改資料集，以動態方式在程式碼中。 如需如何執行這些作業的詳細資訊，請參閱 ADO.NET。 本節中的文件將示範如何使用 Visual Studio 設計工具來處理資料集。 若要知道一件事： 透過設計工具所做的資料集使用 TableAdapter 物件來與資料庫互動而以程式設計的方式的資料集使用資料配接器物件。 以程式設計方式建立資料集的相關資訊，請參閱[Dataadapter 和 Datareader](/dotnet/framework/data/adonet/dataadapters-and-datareaders)。  
  
 如果您的應用程式必須只從資料庫讀取資料，並不會執行更新、 新增，或刪除，通常就可以更佳的效能使用 DataReader 物件取得資料的泛型清單的物件或另一個集合物件。 如果您要顯示的資料，您可以資料繫結的使用者介面的集合。  
  
## <a name="dataset-workflow"></a>資料集的工作流程  
 Visual Studio 提供許多工具，可簡化使用資料集。 基本的端對端工作流程是︰  
  
-   使用**資料來源**視窗從一或多個資料來源建立新的資料集。 使用**Dataset 設計工具**設定資料集，並設定其屬性。 例如，您需要指定哪一個資料表包含，資料來源，以及每個資料表中的資料行。 請小心選擇，以節省資料集所需的記憶體數量。 如需詳細資訊，請參閱[建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
-   指定在資料表之間的關聯性，以便正確地處理外部索引鍵。 如需詳細資訊，請參閱[填滿資料集，使用 Tableadapter](../data-tools/fill-datasets-by-using-tableadapters.md)。  
  
-   使用**TableAdapter 組態精靈**至指定的查詢或預存程序將會填入資料集，以及要實作哪些資料庫作業 （更新、 刪除等等）。 如需詳細資訊，請參閱下列主題：  
  
    -   [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [編輯資料集中的資料](../data-tools/edit-data-in-datasets.md)  
  
    -   [驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)  
  
    -   [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)  
  
-   查詢，並在資料集中搜尋的資料。 如需詳細資訊，請參閱[查詢資料集](../data-tools/query-datasets.md)。 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)]可讓[LINQ (Language-Integrated Query ()](/dotnet/csharp/linq/)中的資料<xref:System.Data.DataSet>物件。 如需詳細資訊，請參閱 [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset)。  
  
-   使用**資料來源**視窗使用者介面控制項繫結至資料集或其個別的資料行，並指定使用者可編輯的哪些資料行。 如需詳細資訊，請參閱[控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
## <a name="datasets-and-n-tier-architecture"></a>資料集和多層式架構的架構  
 多層式架構應用程式中的資料集的相關資訊，請參閱[處理在多層式架構應用程式中的資料集](../data-tools/work-with-datasets-in-n-tier-applications.md)。  
  
## <a name="datasets-and-xml"></a>資料集和 XML  
 有關轉換資料集與 XML 的詳細資訊，請參閱[讀取 XML 資料至資料集](../data-tools/read-xml-data-into-a-dataset.md)和[將資料集儲存為 XML](../data-tools/save-a-dataset-as-xml.md)。  
  
## <a name="see-also"></a>請參閱  
 [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)