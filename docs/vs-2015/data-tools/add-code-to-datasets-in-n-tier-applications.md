---
title: 將程式碼新增至多層式應用程式中的資料集 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aed37ee9cdd8c221fcfb114db426a6286ee8ad6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673122"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉由建立資料集的部分類別檔案，並在其中加入程式碼 (取代將程式碼新增至 *DatasetName*，來擴充資料集的功能。) 的資料集。 部分類別可讓特定類別的程式碼分散到多個實體檔案中。 如需詳細資訊，請參閱 [部分](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) 或 [部分類別和方法](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)。

每次對資料集定義進行變更時，就會產生定義資料集的程式碼。 當您在執行任何修改資料集設定的 wizard 期間進行變更時，也會產生此程式碼。 若要避免在重新產生資料集期間刪除您的程式碼，請將程式碼加入至資料集的部分類別檔案。

根據預設，在您分隔資料集和程式 `TableAdapter` 代碼之後，結果會是每個專案中的離散類別檔案。 原始專案具有 filenamed *DatasetName*。 (或 *DatasetName*。包含程式碼的 Designer.cs) `TableAdapter` 。 在 [ **資料集專案** ] 屬性中指定的專案具有名為 *DatasetName*的檔案。 (或 *DatasetName*的資料集。DataSet.Designer.cs) 。此檔案包含資料集程式碼。

> [!NOTE]
> 當您藉 `TableAdapter` 由設定 [ **資料集專案** ] 屬性) 來分隔資料集和 (時，不會自動移動專案中的現有部分資料集類別。 您必須手動將現有的資料集部分類別移至資料集專案。

> [!NOTE]
> 當需要加入驗證程式代碼時，資料集設計工具會提供用於 <xref:System.Data.DataTable.ColumnChanging> 產生 <xref:System.Data.DataTable.RowChanging> 事件處理常式和事件處理常式的功能。 如需詳細資訊，請參閱 [將驗證加入至多層式資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。

## <a name="add-code-to-datasets-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集

1. 找出包含 .xsd 檔 (資料集) 的專案。

2. 選取 **.xsd** 檔案以開啟資料集。

3. 以滑鼠右鍵按一下您要加入程式碼的資料表 (標題列中的資料表名稱) ，然後選取 [ **視圖程式碼**]。

     部分類別會在程式碼編輯器中建立並開啟。

4. 在部分類別宣告中加入程式碼。

     下列範例顯示在 NorthwindDataSet 中將程式碼新增至 CustomersDataTable 的位置：

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>另請參閱

- [多層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)
- [將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [TableAdapterManager 概觀](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [階層式更新總覽](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)