---
title: 資料集和 Tableadapter 分成不同的專案 |Microsoft Docs
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
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2f4b470bab1bc3a017edeb1c686a53baf2293495
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930645"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>將資料集和 TableAdapter 分成不同的專案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
具類型資料集已經過加強，以便[TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)和資料集類別產生為不同的專案。 這可讓您快速分隔應用程式層，並產生多層式架構資料應用程式。  
  
 下列程序說明使用 Dataset 設計工具來產生資料集的程式碼到專案包含所產生的專案不同的程序`TableAdapter`程式碼。  
  
## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets 和 Tableadapter  
 當您分隔資料集的程式碼從`TableAdapter`程式碼，包含資料集程式碼的專案必須位於目前的方案。 如果這個專案不位於目前的方案，其無法在**資料集 Project**清單中**屬性**視窗。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>將資料集分成不同的專案  
  
1. 開啟的方案，包含資料集 （.xsd 檔案）。  
  
   > [!NOTE]
   >  如果方案不包含您要區隔您的資料集程式碼的專案，建立專案，或將現有的專案加入方案。  
  
2. 按兩下具類型資料集檔案 （.xsd 檔案） 中**方案總管**以開啟中的資料集**Dataset 設計工具**。  
  
3. 選取的空白區域**Dataset 設計工具**。  
  
4. 在 [**屬性**] 視窗中，找出**資料集 Project**節點。  
  
5. 在 **資料集 Project**清單中，選取您要在其中產生資料集的程式碼專案的名稱。  
  
    選取您要產生資料集程式碼的專案之後**資料集檔案**屬性會填入預設的檔案名稱。 如有必要，您可以變更此名稱。 此外，如果您想要產生資料集的程式碼至特定的目錄，您可以設定**專案資料夾**的資料夾名稱的屬性。  
  
   > [!NOTE]
   >  當您分隔資料集和 Tableadapter (藉由設定**資料集 Project**屬性)，將不會自動移動專案中的現有部份資料集類別。 現有的資料集部分的類別必須手動將移至資料集專案。  
  
6. 儲存的資料集。  
  
    資料集程式碼會產生中選取的專案**資料集專案**屬性，而**TableAdapter**到目前的專案產生程式碼。  
  
   根據預設之後您分隔資料集, 和`TableAdapter`程式碼，結果是離散的類別檔案中的每個專案。 原始的專案具有名為的檔案，其中包含 DatasetName.Designer.vb （或 DatasetName.Designer.cs）`TableAdapter`程式碼。 中指定的專案**資料集 Project**屬性都有檔名為 DatasetName.DataSet.Designer.vb （或 DatasetName.DataSet.Designer.cs） 包含資料集的程式碼。  
  
> [!NOTE]
>  若要檢視產生的類別檔案中，選取 資料集或`TableAdapter`專案。 然後，在**方案總管**，選取**顯示所有檔案**。  
  
## <a name="see-also"></a>另請參閱  
 [多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)   
 [逐步解說：建立多層式架構資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [階層式更新](../data-tools/hierarchical-update.md)   
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)
