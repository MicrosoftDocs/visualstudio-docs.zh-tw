---
title: 資料集工具
description: 請參閱 Visual Studio 中提供的資料集工具。 深入瞭解資料集工作流程、資料集和多層式架構，以及資料集和 XML。
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4e711d60010117f3a5081470ab8e6e656a7e6e90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866992"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio 中的資料集工具

> [!NOTE]
> 資料集和相關類別是早期2000s 的舊版 .NET 技術，可讓應用程式在應用程式與資料庫中斷連線的情況下，使用記憶體中的資料。 它們特別適用于可讓使用者修改資料並將變更保存回資料庫的應用程式。 雖然資料集已證明是非常成功的技術，但我們建議新的 .NET 應用程式使用 Entity Framework。 Entity Framework 提供更自然的方式來處理表格式資料作為物件模型，而且具有更簡單的程式設計介面。

`DataSet`物件是記憶體中的物件，基本上是迷你資料庫。 它包含 `DataTable` 、 `DataColumn` 和 `DataRow` 物件，您可以在其中儲存和修改一或多個資料庫中的資料，而不需要維護開啟的連接。 資料集會維護其資料變更的相關資訊，以便在您的應用程式重新連線時，可以追蹤更新並將其傳送回資料庫。

資料集和相關類別是在 <xref:System.Data?displayProperty=fullName> .NET API 的命名空間中定義。 您可以使用 ADO.NET，在程式碼中以動態方式建立和修改資料集。 本節中的檔說明如何使用 Visual Studio 設計師來處理資料集。 透過設計工具建立的資料集會使用 **TableAdapter** 物件來與資料庫互動。 以程式設計方式建立的資料集會使用 **DataAdapter** 物件。 如需以程式設計方式建立資料集的詳細資訊，請參閱 [dataadapter 和 datareader](/dotnet/framework/data/adonet/dataadapters-and-datareaders)。

如果您的應用程式只需要從資料庫讀取資料，而不是執行更新、加入或刪除，您通常可以使用 `DataReader` 物件將資料取出到泛型 `List` 物件或另一個集合物件，以獲得更好的效能。 如果您要顯示資料，您可以將使用者介面資料系結至集合。

## <a name="dataset-workflow"></a>資料集工作流程

Visual Studio 提供可簡化資料集使用的工具。 基本的端對端工作流程為：

- 您可以使用 [ [資料來源] 視窗](add-new-data-sources.md#data-sources-window) ，從一或多個資料來源建立新的資料集。 使用 **DataSet 設計工具** 來設定資料集，並設定其屬性。 例如，您必須指定要包含的資料來源中的哪些資料表，以及每個資料表中的資料行。 請仔細選擇以節省資料集所需的記憶體數量。 如需詳細資訊，請參閱[建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。

- 指定資料表之間的關聯性，以便正確處理外鍵。 如需詳細資訊，請參閱 [使用 Tableadapter 填滿資料集](../data-tools/fill-datasets-by-using-tableadapters.md)。

- 您可以使用 [ **TableAdapter 設定向導]** 來指定填入資料集的查詢或預存程式，以及哪些資料庫作業 (更新、刪除等) 要執行的作業。 如需詳細資訊，請參閱下列主題：

  - [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [編輯資料集中的資料](../data-tools/edit-data-in-datasets.md)

  - [驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)

  - [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)

- 查詢並搜尋資料集中的資料。 如需詳細資訊，請參閱 [查詢資料集](../data-tools/query-datasets.md)。 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] 啟用 [LINQ (語言整合查詢) ](/dotnet/csharp/linq/) 物件中的資料 <xref:System.Data.DataSet> 。 如需詳細資訊，請參閱 [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset)。

- 您可以使用 [ **資料來源** ] 視窗，將使用者介面控制項系結至資料集或其個別資料行，並指定哪些資料行可供使用者編輯。 如需詳細資訊，請參閱 [將控制項系結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

## <a name="datasets-and-n-tier-architecture"></a>資料集和多層式架構

如需多層式應用程式中資料集的相關資訊，請參閱使用多 [層式應用程式中的資料集](../data-tools/work-with-datasets-in-n-tier-applications.md)。

## <a name="datasets-and-xml"></a>資料集和 XML

如需有關將資料集轉換成 XML 以及從 XML 轉換資料的詳細資訊，請參閱將 [xml 資料讀入資料集](../data-tools/read-xml-data-into-a-dataset.md) ，並 [將資料集儲存為 xml](../data-tools/save-a-dataset-as-xml.md)。

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
