---
title: 將程式碼加入 n-tier 應用程式中的資料集 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74786c7fc32057881afd05b62dd2f48dfddbaffe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488223"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[程式碼加入 n-tier 應用程式中的資料集](https://docs.microsoft.com/visualstudio/data-tools/add-code-to-datasets-in-n-tier-applications)。  
  
  
您可以藉由建立資料集的部分類別檔案，並新增程式碼來擴充資料集的功能 (而不是將程式碼加入*DatasetName*。Dataset.Designer 檔案）。 部分類別可讓多個實體檔案分割為特定類別的程式碼。 如需詳細資訊，請參閱 <<c0> [ 部分](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)或是[部分類別和方法](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)。  
  
 定義資料集的程式碼會產生每次變更的資料集定義 (在[建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md))。 當您進行任何修改的資料集組態的精靈執行期間的變更，也會產生此程式碼。 若要避免您的程式碼正在刪除在資料集的重新產生期間，加入資料集的部分類別檔案中的程式碼。  
  
 根據預設之後您分隔資料集, 和`TableAdapter`程式碼，結果是離散的類別檔案中的每個專案。 原始的專案具有 filenamed *DatasetName*.Designer.vb (或*DatasetName*。其中包含 Designer.cs)`TableAdapter`程式碼。 專案中指定**資料集 Project**屬性有檔案，稱為*DatasetName*。DataSet.Designer.vb (或*DatasetName*。DataSet.Designer.cs)。此檔案包含的資料集程式碼。  
  
> [!NOTE]
>  當您分隔資料集和`TableAdapter`s (藉由設定**資料集 Project**屬性)，將不會自動移動專案中的現有部份資料集類別。 現有的資料集部分的類別必須手動將移至資料集專案。  
  
> [!NOTE]
>  要加入的驗證程式碼需要時[建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)提供的功能產生<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.RowChanging>事件處理常式。 如需詳細資訊，請參閱 <<c0> [ 將驗證新增至多層式架構資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。  
  
### <a name="to-add-code-to-datasets-in-n-tier-applications"></a>若要將程式碼加入 n-tier 應用程式中的資料集  
  
1.  找出包含.xsd 檔案的專案 ([建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md))。  
  
2.  選取  **.xsd**若要開啟的檔案[建立及編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)。  
  
3.  以滑鼠右鍵按一下的資料表，您要新增程式碼 （標題列中的資料表名稱） 和 thenselect**檢視程式碼**。  
  
     部分類別會建立，並會在程式碼編輯器中開啟。  
  
4.  加入部分類別宣告內的程式碼。  
  
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
 [多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)   
 [加入 Tableadapter 中的程式碼，在多層式架構應用程式](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [TableAdapterManager 概觀](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [階層式更新概觀](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [建立資料應用程式](../data-tools/creating-data-applications.md)   
 [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)

