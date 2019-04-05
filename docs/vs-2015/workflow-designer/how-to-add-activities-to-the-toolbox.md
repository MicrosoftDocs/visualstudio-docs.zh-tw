---
title: HOW TO：將活動新增至工具箱 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 52f9fabec46fb04f2cc936c7bf76d67bd2dabcd3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945591"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>HOW TO：將活動新增至工具箱
活動可以加入至**工具箱**方案中有好幾種方式。 您可以從目前的專案內部加入活動、從不同的專案參考活動，或是從不同的組件參考活動。  
  
### <a name="to-add-an-activity-from-within-your-current-project"></a>若要從目前的專案內部加入活動  
  
1.  將新的自訂活動加入到目前的工作流程專案。 [!INCLUDE[crabout](../includes/crabout-md.md)] 將新的自訂活動新增至您的專案，請參閱[How to:將新的項目新增至工作流程專案](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md)。  
  
2.  加入自訂邏輯至活動。  
  
3.  建置專案。 如果建置成功，新的類別目錄中**工具箱**名為"\<*專案名稱*> 」 會顯示與該類別中包含這個自訂活動。  
  
    > [!NOTE]
    >  如果重設工具箱，自訂活動會移除，即使重新建置方案也一樣。 如果要在重設工具箱後重新填入自訂活動，請重新啟動 [!INCLUDE[vs2010](../includes/vs2010-md.md)]。  
  
    > [!NOTE]
    >  在工具箱中，針對一個活動名稱只能顯示一個活動。 如果有兩個活動來自不同的組件但類別名稱相同，就只能顯示其中一個。  
  
    > [!NOTE]
    >  應用程式定義域在編輯器執行個體間共用，如果使用靜態變數，則它們也會在編輯器執行個體間共用。 如果這不是想要的行為，應該使用服務來追蹤變數執行個體。 請參閱[使用 ModelItem 編輯內容](http://msdn.microsoft.com/library/7f9f1ea5-0147-4079-8eca-be94f00d3aa1)如需使用設計工具內的服務。  
  
### <a name="to-add-an-activity-from-within-a-different-project"></a>若要從不同的專案內部加入活動  
  
1.  開啟一個方案，該方案應包含至少一個工作流程專案，以及一個自訂活動程式庫專案，或另一個定義自訂活動的工作流程專案。  
  
2.  建置這兩個專案。 如果建置成功，新的類別目錄中**工具箱**名為"\<*專案名稱*> 」 會顯示與該類別中包含這個自訂活動。  
  
### <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>若要從組件將活動加入至工具箱  
  
1.  開啟一個工作流程方案。  
  
2.  從**工具**功能表上，選取**選擇工具箱項目...**.  
  
3.  在 **選擇工具箱項目**對話方塊中，選取**System.Activities 元件**索引標籤，然後按一下 **瀏覽...** 若要瀏覽至包含您想要新增的自訂活動的組件。  
  
4.  選取組件，然後按一下**確定**。 自訂活動元件會加到元件清單中，而且會自動選取。  
  
    1.  按一下 **確定**以關閉對話方塊。  
  
5.  若要顯示工具箱 中，選取**工具箱**從**檢視**功能表。  
  
6.  自訂活動會出現在**工具箱**之前的焦點項目已加入的類別下。 比方說，如果**一般**分類中選取**工具箱**之前新增工具箱項目，此活動出現在**一般**類別目錄。  
  
## <a name="see-also"></a>另請參閱  
 [使用工作流程設計工具](../workflow-designer/using-the-workflow-designer.md)