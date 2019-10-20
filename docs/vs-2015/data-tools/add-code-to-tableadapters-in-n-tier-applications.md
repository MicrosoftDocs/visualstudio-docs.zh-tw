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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673109"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉由建立 `TableAdapter` 的部分類別檔案並在其中新增程式碼，來擴充 `TableAdapter` 的功能（而不是將程式碼加入至*DatasetName*。DataSet. 設計工具檔案）。 部分類別可讓特定類別的程式碼劃分到多個實體檔案中。 如需詳細資訊，請參閱[partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)或[partial （類型）](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)。

 每次對 `TableAdapter` 進行變更時，都會產生定義 `TableAdapter` 的程式碼。 這段程式碼也會在執行任何修改 `TableAdapter` 設定的 wizard 期間進行變更時產生。 若要防止重新產生 `TableAdapter` 時刪除您的程式碼，請將程式碼新增至 `TableAdapter` 的部分類別檔案。

 根據預設，當您將資料集和 `TableAdapter` 程式碼分開之後，結果會是每個專案中的個別類別檔案。 原始專案具有名為*DatasetName*的檔案。設計工具 .vb （或*DatasetName*。Designer.cs），其中包含 `TableAdapter` 的程式碼。 在**資料集專案**屬性中指定的專案具有名為*DatasetName*的檔案。資料集. Designer .vb （或*DatasetName*。DataSet.Designer.cs），其中包含資料集程式碼。

> [!NOTE]
> 當您分隔資料集和 `TableAdapter`s （藉由設定 [**資料集專案**] 屬性）時，不會自動移動專案中的現有部分資料集類別。 現有的資料集部分類別必須手動移至 dataset 專案。

> [!NOTE]
> DataSet 設計工具會在需要驗證時，提供產生 <xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.RowChanging> 事件處理常式的功能。 如需詳細資訊，請參閱[將驗證新增至多層式資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>在多層式應用程式中將使用者程式碼加入 TableAdapter

1. 找出包含 .xsd 檔案的專案（資料集）。

2. 按兩下 **.xsd**檔案以開啟資料集。

3. 以滑鼠右鍵按一下您想要新增程式碼的 `TableAdapter`，然後選取 [**View code**]。

     部分類別會在程式碼編輯器中建立並開啟。

4. 在部分類別宣告內加入程式碼。

5. 下列範例顯示在 `NorthwindDataSet` 中將程式碼加入至 `CustomersTableAdapter` 的位置：

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
 多[層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)[將程式碼新增至多層式架構應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [Tableadapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) [TableAdapterManager 總覽](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)[階層更新總覽](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)