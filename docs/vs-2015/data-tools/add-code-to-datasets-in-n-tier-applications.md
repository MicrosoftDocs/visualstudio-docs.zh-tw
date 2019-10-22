---
title: 將程式碼新增至多層式架構應用程式中的資料集 |Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673122"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以擴充資料集的功能，方法是建立資料集的部分類別檔案，並在其中加入程式碼（而不是將程式碼加入至*DatasetName*。Dataset. 設計工具檔案）。 部分類別可讓特定類別的程式碼劃分到多個實體檔案中。 如需詳細資訊，請參閱[部分](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)或[部分類別和方法](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)。

每次對資料集定義進行變更時，就會產生定義資料集的程式碼。 當您在執行任何修改資料集設定的任何 wizard 期間進行變更時，也會產生此程式碼。 若要避免在重新產生資料集期間刪除您的程式碼，請將程式碼加入至資料集的部分類別檔案。

根據預設，當您將資料集和 `TableAdapter` 程式碼分開之後，結果會是每個專案中的個別類別檔案。 原始專案具有 filenamed *DatasetName*。設計工具 .vb （或*DatasetName*。Designer.cs），其中包含 `TableAdapter` 的程式碼。 在**資料集專案**屬性中指定的專案具有名為*DatasetName*的檔案。資料集. Designer .vb （或*DatasetName*。DataSet.Designer.cs）。此檔案包含資料集程式碼。

> [!NOTE]
> 當您分隔資料集和 `TableAdapter`s （藉由設定 [**資料集專案**] 屬性）時，不會自動移動專案中的現有部分資料集類別。 現有的資料集部分類別必須手動移至 dataset 專案。

> [!NOTE]
> 當需要加入驗證碼時，DataSet 設計工具會提供產生 <xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.RowChanging> 事件處理常式的功能。 如需詳細資訊，請參閱[將驗證新增至多層式資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。

## <a name="add-code-to-datasets-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集

1. 找出包含 .xsd 檔案的專案（資料集）。

2. 選取 **.xsd**檔案以開啟資料集。

3. 以滑鼠右鍵按一下您想要加入程式碼的資料表（標題列中的資料表名稱），然後選取 [ **View code**]。

     部分類別會在程式碼編輯器中建立並開啟。

4. 在部分類別宣告內加入程式碼。

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

## <a name="see-also"></a>請參閱

- [多層式架構 (N-Tier) 資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)
- [將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Tableadapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [TableAdapterManager 總覽](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [階層式更新總覽](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)