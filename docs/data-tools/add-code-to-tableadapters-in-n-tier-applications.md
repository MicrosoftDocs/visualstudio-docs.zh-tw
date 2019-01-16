---
title: 將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 17a56fcf0c89ef63033cdcd538e5b9cf9e3efe49
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928285"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter
您可以透過建立 TableAdapter 部分類別檔案，並加入程式碼擴充 TableAdapter 的功能 (而不是將程式碼加入*DatasetName.DataSet.Designer*檔案)。 部分類別可讓多個實體檔案分割為特定類別的程式碼。 如需詳細資訊，請參閱 <<c0> [ 部分](/dotnet/visual-basic/language-reference/modifiers/partial)或是[partial （類型）](/dotnet/csharp/language-reference/keywords/partial-type)。

定義 TableAdapter 的程式碼會產生每次變更資料集的 TableAdapter。 任何修改的 TableAdapter 組態精靈執行期間進行變更時，也會產生此程式碼。 若要避免您的程式碼在 TableAdapter 的重新產生期間遭到刪除，請在 TableAdapter 的部分類別檔案中加入程式碼。

根據預設，您可將資料集和 TableAdapter 程式碼之後, 的結果會是離散的類別檔案中的每個專案。 原始的專案具有名為的檔案*DatasetName.Designer.vb* (或*DatasetName.Designer.cs*) 包含 TableAdapter 的程式碼。 專案中指定**資料集 Project**屬性具有名為的檔案*DatasetName.DataSet.Designer.vb* (或*DatasetName.DataSet.Designer.cs*)，包含資料集程式碼。

> [!NOTE]
>  當您分隔資料集與 TableAdapter 時 (設定 [資料集專案] 屬性)，將不會自動移動專案中的現有部份資料集類別。 現有的部分資料集類別必須手動將移至資料集專案。

> [!NOTE]
> 資料集提供功能來產生<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>時需要驗證的事件處理常式。 如需詳細資訊，請參閱 <<c0> [ 將驗證新增至多層式架構資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>若要將使用者程式碼新增至多層式架構應用程式中的 TableAdapter

1.  找出包含專案 *.xsd*檔案。

2.  按兩下 *.xsd*若要開啟的檔案**Dataset 設計工具**。

3.  以滑鼠右鍵按一下您想要加入程式碼，然後選取 TableAdapter**檢視程式碼**。

     部分類別會建立，並會在程式碼編輯器中開啟。

4.  加入部分類別宣告內的程式碼。

5.  下列範例示範如何將程式碼加入`CustomersTableAdapter`在`NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>另請參閱

- [多層式架構 (N-Tier) 資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)
- [將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [建立和設定 TableAdapter](create-and-configure-tableadapters.md)
- [階層式更新概觀](hierarchical-update.md)
