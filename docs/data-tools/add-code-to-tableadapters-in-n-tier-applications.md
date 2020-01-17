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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e5d240726030a3a08d184b3015f56f65d9168e9f
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113327"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter
您可以擴充 TableAdapter 的功能，方法是建立 TableAdapter 的部分類別檔案，並在其中加入程式碼（而不是將程式碼新增至*DatasetName 設計*工具檔案）。 部分類別可讓特定類別的程式碼劃分到多個實體檔案中。 如需詳細資訊，請參閱[partial](/dotnet/visual-basic/language-reference/modifiers/partial)或[partial （類型）](/dotnet/csharp/language-reference/keywords/partial-type)。

定義 TableAdapter 的程式碼會在每次對資料集中的 TableAdapter 進行變更時產生。 這段程式碼也會在執行任何修改 TableAdapter 設定的 wizard 期間進行變更時產生。 若要避免在重新產生 TableAdapter 期間刪除您的程式碼，請將程式碼新增至 TableAdapter 的部分類別檔案。

根據預設，當您分隔資料集和 TableAdapter 程式碼之後，結果會是每個專案中的個別類別檔案。 原始專案具有名為*DatasetName*的檔案，也就是包含 TableAdapter 程式碼的*DatasetName.Designer.cs*。 在**資料集專案**屬性中指定的專案具有名為*DatasetName*的檔案，其中包含資料集程式碼。

> [!NOTE]
> 當您分隔資料集與 TableAdapter 時 (設定 [資料集專案] 屬性)，將不會自動移動專案中的現有部份資料集類別。 現有的部分資料集類別必須手動移至 dataset 專案。

> [!NOTE]
> 資料集提供在需要驗證時產生 <xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.RowChanging> 事件處理常式的功能。 如需詳細資訊，請參閱[將驗證新增至多層式資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>在多層式應用程式中將使用者程式碼加入 TableAdapter

1. 找出包含 *.xsd*檔案的專案。

2. 按兩下 *.xsd*檔案以開啟 [ **DataSet 設計工具**]。

3. 以滑鼠右鍵按一下您想要加入程式碼的 TableAdapter，然後選取 [ **View code**]。

     部分類別會在程式碼編輯器中建立並開啟。

4. 在部分類別宣告內加入程式碼。

5. 下列範例顯示在 `NorthwindDataSet`中將程式碼加入至 `CustomersTableAdapter` 的位置：

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

## <a name="see-also"></a>請參閱

- [多層式架構 (N-Tier) 資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)
- [將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [建立和設定 TableAdapter](create-and-configure-tableadapters.md)
- [階層式更新概觀](hierarchical-update.md)
