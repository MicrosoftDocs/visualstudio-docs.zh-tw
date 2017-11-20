---
title: "在多層式架構應用程式中，加入至 Tableadapter 的程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 396e1132015c2eb37f06095f135dae878bfeb574
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>在多層式架構應用程式中，加入至 Tableadapter 的程式碼
您可以透過建立 tableadapter 的部分類別檔案，並加入程式碼擴充 TableAdapter 的功能 (而不是加入程式碼以*DatasetName*。DataSet.Designer 檔案）。 部分類別可讓分割為多個實體檔案的特定類別的程式碼。 如需詳細資訊，請參閱[部分](/dotnet/visual-basic/language-reference/modifiers/partial)或[partial （類型）](/dotnet/csharp/language-reference/keywords/partial-type)。  
  
每次變更資料集的 TableAdapter，都會產生定義 TableAdapter 的程式碼。 任何修改的 TableAdapter 組態精靈執行期間進行變更時，也會產生此程式碼。 若要防止在 TableAdapter 的重新產生期間正在刪除您的程式碼，將程式碼加入至 TableAdapter 的部分類別檔案。  
  
根據預設，您可將資料集和 TableAdapter 的程式碼之後, 的結果會是離散的類別檔案中的每個專案。 原始的專案具有名為*DatasetName*。.Designer.vb (或*DatasetName*。.Designer.cs) 包含 TableAdapter 的程式碼。 專案中指定的**資料集專案**屬性具有名為*DatasetName*。DataSet.Designer.vb (或*DatasetName*。DataSet.Designer.cs)，其中包含資料集程式碼。  
  
> [!NOTE]
>  當您分隔資料集與 Tableadapter 時 (藉由設定**資料集專案**屬性)，將不會自動移動專案中的現有部份資料集類別。 現有資料集部分類別必須手動移至資料集專案。  
  
> [!NOTE]
>  資料集提供的功能來產生<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>事件處理常式時需要驗證。 如需詳細資訊，請參閱[驗證加入 n-tier 資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>若要將使用者程式碼加入至 TableAdapter 的多層式架構應用程式中  
  
1.  找出包含.xsd 檔案的專案。
  
2.  按兩下  **.xsd**檔案以開啟**Dataset 設計工具**。  
  
3.  以滑鼠右鍵按一下您想要加入程式碼，然後選取 TableAdapter**檢視程式碼**。  
  
     建立部分類別，並會在程式碼編輯器中開啟。  
  
4.  加入部分類別宣告內的程式碼。  
  
5.  下列範例示範如何將程式碼加入`CustomersTableAdapter`中`NorthwindDataSet`:  
  
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
[多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)   
[將程式碼加入 n-tier 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
[建立及設定 TableAdapters](create-and-configure-tableadapters.md)   
[階層式更新概觀](hierarchical-update.md)   
