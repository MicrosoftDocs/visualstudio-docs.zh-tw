---
title: 將程式碼新增至多層式應用程式中的 Tableadapter |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 942850e776cdd493afaad56b782b417db2040625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673109"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉 `TableAdapter` 由建立的部分類別檔案 `TableAdapter` ，並在其中加入程式碼來擴充的功能 (而不是將程式碼新增至 *DatasetName*。) 的資料集。 部分類別可讓特定類別的程式碼分散到多個實體檔案中。 如需詳細資訊，請參閱 [部分](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) 或 [部分 (類型) ](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)。

 `TableAdapter`每次對進行變更時，就會產生定義的程式碼 `TableAdapter` 。 當在修改設定的任何 wizard 執行期間進行變更時，也會產生此程式碼 `TableAdapter` 。 為了避免在重新產生期間刪除您的程式碼 `TableAdapter` ，請將程式碼新增至的部分類別檔案 `TableAdapter` 。

 根據預設，在您分隔資料集和程式 `TableAdapter` 代碼之後，結果會是每個專案中的離散類別檔案。 原始專案具有名為 *DatasetName*的檔案。 (或 *DatasetName*。包含程式碼的 Designer.cs) `TableAdapter` 。 在 [ **資料集專案** ] 屬性中指定的專案具有名為 *DatasetName*的檔案。 (或 *DatasetName*的資料集。包含資料集程式碼的 DataSet.Designer.cs) 。

> [!NOTE]
> 當您藉 `TableAdapter` 由設定 [ **資料集專案** ] 屬性) 來分隔資料集和 (時，將不會自動移動專案中的現有部分資料集類別。 您必須手動將現有的資料集部分類別移至資料集專案。

> [!NOTE]
> DataSet 設計工具提供 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 在需要驗證時產生事件處理常式和事件處理常式的功能。 如需詳細資訊，請參閱 [將驗證加入至多層式資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>將使用者程式碼新增至多層式應用程式中的 TableAdapter

1. 找出包含 .xsd 檔 (資料集) 的專案。

2. 按兩下 **.xsd** 檔案以開啟資料集。

3. 以滑鼠右鍵按一下 `TableAdapter` 您要新增程式碼的，然後選取 [**視圖程式碼**]。

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
 多[層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)[將程式碼新增至多層式應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [Tableadapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) [TableAdapterManager 總覽](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)[階層式更新總覽](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)