---
title: "BDC 模型設計工具的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eaf6871f7ad9316ba2dbdaa8fa29b4810b1d6a3d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="bdc-model-design-tools-overview"></a>BDC 模型設計工具概觀
  您可以使用 BDC 設計工具來設計商務資料連線 (BDC) 模型**BDC 方法詳細資料**視窗中，而**BDC 總管**。  
  
 **BDC 總管**可讓您瀏覽模型、 搜尋模型，以及定義類型描述元。  
  
## <a name="bdc-designer"></a>BDC 設計工具  
 BDC 設計工具可讓您在模型中定義的實體，以及以視覺化方式彼此排列它們的關聯性。 您可以使用 BDC 設計工具來完成下列工作：  
  
-   將實體加入至模型。  
  
-   從模型移除實體。  
  
-   定義實體之間的關聯性。  
  
 若要開啟 BDC 設計工具，按兩下您的專案中的模型檔案或開啟模型檔案的捷徑功能表，然後選擇**開啟**。 將實體加入至模型中，拖曳或複製**實體**從**工具箱**拖曳至設計工具。 若要建立兩個實體之間的關聯，請選擇**關聯**控制**工具箱**，選擇第一個實體，，然後選擇 第二個實體。  
  
## <a name="bdc-method-details-window"></a>BDC 方法詳細資料視窗  
 使用**BDC 方法詳細資料**視窗定義參數，執行個體，和篩選方法的描述元。  
  
 您可以快速產生中的搜尋、 特定搜尋工具、 建立者、 Updater 和刪除者方法**BDC 方法詳細資料**視窗。 當您產生這些方法時，Visual Studio 會加入至方法的中繼資料，例如參數、 執行個體和型別描述元。 您可以修改此中繼資料，以滿足您的特定案例。  
  
 若要開啟**BDC 方法詳細資料**視窗，請在功能表列上的選擇**檢視**，**其他視窗**， **BDC 方法詳細資料**。  
  
 若要檢視中的方法**BDC 方法詳細資料**視窗中，選擇 BDC 設計工具中的實體。 選取實體的方法會出現在**BDC 方法詳細資料**視窗。 如果您沒有在 BDC 設計工具中，選擇實體**BDC 方法詳細資料**視窗會顯示任何資訊。  
  
 展開或摺疊中的節點**BDC 方法詳細資料**視窗定義參數、 執行個體，並篩選描述元。 使用**BDC 總管**定義類型描述元。  
  
## <a name="bdc-explorer"></a>BDC 總管  
 **BDC 總管**顯示構成模型的項目。 若要開啟**BDC 總管**，在功能表列上選擇 **檢視**，**其他視窗**， **BDC 總管**。 若要瀏覽此模型中，展開節點中的**BDC 總管**。 每個節點表示模型檔的 XML 中的項目。  
  
 隨著您選擇在節點**BDC 總管**，您選擇每個節點的屬性會出現在**屬性**視窗。 許多這些屬性對應到模型檔案中的屬性。 您可以使用 [搜尋] 方塊上方的搜尋模型**BDC 總管**。  
  
> [!NOTE]  
>  **BDC 總管**不會顯示識別項、 自訂屬性、 當地語系化的字串，關聯群組、 動作、 篩選描述元、 動作控制清單，以及預設參數值。  
  
### <a name="defining-type-descriptors"></a>定義類型描述元  
 使用**BDC 總管**定義類型描述元。 BDC 總管可讓您將類型描述元定義一次，然後重複使用該模型中其他位置的類型描述元。 若要完成這項作業，複製類型描述元和貼上任何其他參數或型別描述項。  
  
> [!NOTE]  
>  原始的型別描述項的變更不會影響該類型描述元的複本。  
  
 如需詳細資訊，請參閱[如何： 定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何： 將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何： 加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何： 加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何： 加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何： 加入 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)   
 [逐步解說： 使用商務資料在 SharePoint 中建立外部清單](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  