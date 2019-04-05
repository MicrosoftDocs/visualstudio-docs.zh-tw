---
title: 加入 Tableadapter 中的程式碼，在多層式架構應用程式 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 423975825e74b7dab29f19697e1e17fb00430f9c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940412"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
您可以擴充的功能`TableAdapter`所建立的部分類別檔案`TableAdapter`，然後將加入的程式碼 (而不是將程式碼加入*DatasetName*。DataSet.Designer 檔案）。 部分類別可讓多個實體檔案分割為特定類別的程式碼。 如需詳細資訊，請參閱 <<c0> [ 部分](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)或是[partial （類型）](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)。  
  
 定義的程式碼`TableAdapter`每次變更都會產生`TableAdapter`。 此程式碼也會產生任何修改的組態的精靈執行期間進行變更時`TableAdapter`。 若要防止您的程式碼重新產生期間刪除`TableAdapter`，將程式碼的部分類別檔案加入`TableAdapter`。  
  
 根據預設之後您分隔資料集, 和`TableAdapter`程式碼，結果是離散的類別檔案中的每個專案。 原始的專案具有名為的檔案*DatasetName*.Designer.vb (或*DatasetName*。其中包含 Designer.cs)`TableAdapter`程式碼。 專案中指定**資料集 Project**屬性具有名為的檔案*DatasetName*。DataSet.Designer.vb (或*DatasetName*。DataSet.Designer.cs) 包含資料集的程式碼。  
  
> [!NOTE]
> 當您分隔資料集和`TableAdapter`s (藉由設定**資料集 Project**屬性)，在專案中的現有部份資料集類別不會自動移動。 現有的資料集部分的類別必須手動將移至資料集專案。  
  
> [!NOTE]
> DataSet 設計工具提供功能來產生<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>時需要驗證的事件處理常式。 如需詳細資訊，請參閱 <<c0> [ 將驗證新增至多層式架構資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>若要將使用者程式碼新增至多層式架構應用程式中的 TableAdapter  
  
1.  找出包含.xsd 檔案 （資料集） 的專案。  
  
2.  按兩下 **.xsd**開啟資料集的檔案。  
  
3.  以滑鼠右鍵按一下`TableAdapter`想要加入程式碼，然後按**檢視程式碼**。  
  
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
 [多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)   
 [將程式碼加入 n-tier 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [TableAdapterManager 概觀](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [階層式更新概觀](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)