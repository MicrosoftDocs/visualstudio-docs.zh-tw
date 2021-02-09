---
title: 將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter
description: 將程式碼新增至多層式應用程式中的資料表介面卡。 建立 TableAdapter 的部分類別檔案，並在其中加入程式碼 (，而不是 DatasetName 設計工具) 。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: da4db396d718fcd8b88b476278a2470663b58a8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859472"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter
您可以藉由建立 TableAdapter 的部分類別檔案並在其中加入程式碼，來擴充 TableAdapter 的功能 (而不是將程式碼加入至 *DatasetName 設計* 工具檔案) 。 部分類別可讓特定類別的程式碼分散到多個實體檔案中。 如需詳細資訊，請參閱 [部分](/dotnet/visual-basic/language-reference/modifiers/partial) 或 [部分 (類型) ](/dotnet/csharp/language-reference/keywords/partial-type)。

每次對資料集中的 TableAdapter 進行變更時，就會產生定義 TableAdapter 的程式碼。 當修改 TableAdapter 設定的任何 wizard 執行期間發生變更時，也會產生此程式碼。 為了避免在重新產生 TableAdapter 期間刪除您的程式碼，請將程式碼加入至 TableAdapter 的部分類別檔案。

根據預設，在您分隔資料集和 TableAdapter 程式碼之後，結果會是每個專案中的個別類別檔案。 原始專案有一個名為 *DatasetName* 的檔案， (或包含 TableAdapter 程式碼的 *DatasetName.Designer.cs*) 。 在 [ **資料集專案** ] 屬性中指定的專案具有名為 *DatasetName* 的檔案， (或包含資料集程式碼的 *DatasetName.DataSet.Designer.cs*) 。

> [!NOTE]
> 當您分隔資料集與 TableAdapter 時 (設定 [資料集專案] 屬性)，將不會自動移動專案中的現有部份資料集類別。 您必須手動將現有的部分資料集類別移至資料集專案。

> [!NOTE]
> 資料集提供 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 在需要驗證時產生事件處理常式和事件處理常式的功能。 如需詳細資訊，請參閱 [將驗證加入至多層式資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>將使用者程式碼新增至多層式應用程式中的 TableAdapter

1. 找出包含 *.xsd* 檔的專案。

2. 按兩下 *.xsd* 檔案以開啟 **DataSet 設計工具**。

3. 以滑鼠右鍵按一下您要新增程式碼的 TableAdapter，然後選取 [ **視圖程式碼**]。

     部分類別會在程式碼編輯器中建立並開啟。

4. 在部分類別宣告中加入程式碼。

5. 下列範例顯示在中將程式碼加入至的位置 `CustomersTableAdapter` `NorthwindDataSet` ：

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

- [多層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)
- [將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [建立和設定 TableAdapter](create-and-configure-tableadapters.md)
- [階層式更新概觀](hierarchical-update.md)
