---
title: 資料集工具
ms.date: 11/21/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b131e1339c1eab5cac84f55f08779e41c50eedd5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949138"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio 中的資料集工具

> [!NOTE]
> 資料集和相關的類別是舊版的.NET 技術，從早期 2000s 可讓應用程式的應用程式會與資料庫中斷連接時，使用記憶體中的資料。 它們是特別適用於應用程式，讓使用者能夠修改資料，並保存資料庫的變更。 雖然資料集已證明是非常成功的技術，我們建議新的.NET 應用程式使用 Entity Framework。 Entity Framework 提供更自然的方式，為物件模型的表格式資料搭配使用，而且有一個簡單的程式設計介面。

A`DataSet`物件是基本上是小型資料庫的記憶體物件。 它包含`DataTable`， `DataColumn`，和`DataRow`物件中，您可以儲存和修改一或多個資料庫中的資料，而不需要維護的開啟連接。 資料集會維護其資料，變更的相關資訊，因此更新可以追蹤與您的應用程式變得重新連線時，傳送回資料庫。

資料集和相關的類別會定義在<xref:System.Data?displayProperty=fullName>.NET Framework 類別庫中的命名空間。 您可以建立及修改資料集，以動態方式使用 ADO.NET 程式碼。 在本節中的文件會示範如何使用 Visual Studio 設計工具使用資料集。 會透過設計工具使用的資料集**TableAdapter**與資料庫互動的物件。 以程式設計方式建立的資料集使用**DataAdapter**物件。 如需以程式設計方式建立資料集的資訊，請參閱[Dataadapter 和 Datareader](/dotnet/framework/data/adonet/dataadapters-and-datareaders)。

如果您的應用程式必須只從資料庫讀取資料，並不會執行更新、 新增，或刪除，您可以使用，通常取得較佳的效能`DataReader`物件擷取資料到泛型`List`物件或另一個集合物件。 如果您要顯示的資料，您可以資料繫結的使用者介面的集合。

## <a name="dataset-workflow"></a>資料集的工作流程

Visual Studio 提供工具，以簡化使用資料集。 基本的端對端工作流程是：

- 使用[資料來源 視窗](add-new-data-sources.md#data-sources-window)從一或多個資料來源建立新的資料集。 使用**Dataset 設計工具**設定資料集，並設定其屬性。 例如，您需要指定哪一個資料表包含，資料來源，以及每個資料表資料行。 請小心選擇，以保留的資料集需要的記憶體數量。 如需詳細資訊，請參閱[建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。

- 指定在資料表之間的關聯性，以便能夠正確處理外部索引鍵。 如需詳細資訊，請參閱 <<c0> [ 使用 Tableadapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)。

- 使用**TableAdapter 組態精靈**指定的查詢或預存程序可填入資料集，以及要實作哪些資料庫作業 （update、 delete 等等）。 如需詳細資訊，請參閱下列主題：

    - [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)

    - [編輯資料集中的資料](../data-tools/edit-data-in-datasets.md)

    - [驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)

    - [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)

- 查詢，並在資料集中搜尋的資料。 如需詳細資訊，請參閱 <<c0> [ 查詢資料集](../data-tools/query-datasets.md)。 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] 可讓[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)中的資料<xref:System.Data.DataSet>物件。 如需詳細資訊，請參閱 [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset)。

- 使用**Zdroje dat**使用者介面控制項繫結至資料集或其個別的資料行，並指定哪些資料行是使用者可編輯 視窗。 如需詳細資訊，請參閱 <<c0> [ 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

## <a name="datasets-and-n-tier-architecture"></a>資料集和多層式架構的架構

如需在多層式架構應用程式中的資料集的資訊，請參閱[使用多層式架構應用程式中的資料集](../data-tools/work-with-datasets-in-n-tier-applications.md)。

## <a name="datasets-and-xml"></a>資料集和 XML

如需轉換資料集，與 XML 的資訊，請參閱[讀取 XML 資料至資料集](../data-tools/read-xml-data-into-a-dataset.md)並[將資料集儲存為 XML](../data-tools/save-a-dataset-as-xml.md)。

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)