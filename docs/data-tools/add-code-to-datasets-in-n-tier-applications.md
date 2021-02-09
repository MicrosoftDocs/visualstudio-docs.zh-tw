---
title: 將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集
description: 在 Visual Studio 的多層式應用程式中，將程式碼新增至資料集。 建立資料集的部分類別檔案，並在其中加入程式碼 (，而不是 DatasetName 設計工具) 。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending DataSets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c1a6e424fe76b94321ca79ab08496cd160969890
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867525"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集

您可以藉由建立資料集的部分類別檔案，並在其中加入程式碼 (取代將程式碼新增至 *DatasetName*，來擴充資料集的功能。) 的資料集。 部分類別可讓特定類別的程式碼分散到多個實體檔案中。 如需詳細資訊，請參閱 [部分](/dotnet/visual-basic/language-reference/modifiers/partial) 或 [部分類別和方法](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)。

每次對具型別資料集的資料集定義 (進行變更時，就會產生定義資料集的程式碼) 。 當您在執行任何修改資料集設定的 wizard 期間進行變更時，也會產生此程式碼。 若要避免在重新產生資料集期間刪除您的程式碼，請將程式碼加入至資料集的部分類別檔案。

根據預設，在您分隔資料集和 TableAdapter 程式碼之後，結果會是每個專案中的個別類別檔案。 原始專案有一個名為 *DatasetName* 的檔案， (或包含 TableAdapter 程式碼的 *DatasetName.Designer.cs*) 。 在 [ **資料集專案** ] 屬性中指定的專案具有名為 *DatasetName* 的檔案， (或 *DatasetName.DataSet.Designer.cs*) 。此檔案包含資料集程式碼。

> [!NOTE]
> 當您藉由設定 [ **資料集專案** ] 屬性) 來分隔資料集和 tableadapter (時，不會自動移動專案中的現有部分資料集類別。 您必須手動將現有的資料集部分類別移至資料集專案。

> [!NOTE]
> 當需要加入驗證程式代碼時，具類型的資料集會提供用於 <xref:System.Data.DataTable.ColumnChanging> 產生 <xref:System.Data.DataTable.RowChanging> 事件處理常式和事件處理常式的功能。 如需詳細資訊，請參閱 [將驗證加入至多層式資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>若要將程式碼加入至多層式應用程式中的資料集

1. 找出包含 *.xsd* 檔的專案。

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
- [建立和設定 TableAdapter](create-and-configure-tableadapters.md)
- [階層式更新概觀](hierarchical-update.md)
- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
