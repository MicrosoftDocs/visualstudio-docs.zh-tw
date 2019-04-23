---
title: 將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: dbd65c5247a82f2a58a57e50402ecde5d330cc9b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111684"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集
您可以藉由建立資料集的部分類別檔案，並新增程式碼來擴充資料集的功能 (而不是將程式碼加入*DatasetName*。Dataset.Designer 檔案）。 部分類別可讓多個實體檔案分割為特定類別的程式碼。 如需詳細資訊，請參閱 <<c0> [ 部分](/dotnet/visual-basic/language-reference/modifiers/partial)或是[部分類別和方法](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)。

定義資料集的程式碼會產生每次變更 （在具類型的資料集） 的資料集定義。 當您進行任何修改的資料集組態的精靈執行期間的變更，也會產生此程式碼。 若要避免您的程式碼正在刪除在資料集的重新產生期間，加入資料集的部分類別檔案中的程式碼。

根據預設，您可將資料集和 TableAdapter 程式碼之後, 的結果會是離散的類別檔案中的每個專案。 原始的專案具有名為的檔案*DatasetName.Designer.vb* (或*DatasetName.Designer.cs*) 包含 TableAdapter 的程式碼。 專案中指定**資料集 Project**屬性有檔案，稱為*DatasetName.DataSet.Designer.vb* (或*DatasetName.DataSet.Designer.cs*).此檔案包含的資料集程式碼。

> [!NOTE]
>  當您分隔資料集和 Tableadapter (藉由設定**資料集 Project**屬性)，將不會自動移動專案中的現有部份資料集類別。 現有的資料集部分的類別必須手動將移至資料集專案。

> [!NOTE]
>  具類型資料集時的驗證程式碼必須加入，提供功能來產生<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>事件處理常式。 如需詳細資訊，請參閱 <<c0> [ 將驗證新增至多層式架構資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>若要將程式碼加入 n-tier 應用程式中的資料集

1. 找出包含專案 *.xsd*檔案。

2. 選取  **.xsd**開啟資料集的檔案。

3. 以滑鼠右鍵按一下您想以加入程式碼 （標題列中的資料表名稱），然後選取的資料表**檢視程式碼**。

     部分類別會建立，並會在程式碼編輯器中開啟。

4. 加入部分類別宣告內的程式碼。

     下列範例示範如何將程式碼新增至 NorthwindDataSet 中 CustomersDataTable:

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

- [多層式架構 (N-Tier) 資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)
- [將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [建立和設定 TableAdapter](create-and-configure-tableadapters.md)
- [階層式更新概觀](hierarchical-update.md)
- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)