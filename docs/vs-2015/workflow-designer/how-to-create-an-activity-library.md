---
title: 如何： 建立活動程式庫 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 341e87459cbaae204baba66108a5944eb1f7f97f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271819"
---
# <a name="how-to-create-an-activity-library"></a>HOW TO：建立活動程式庫
自訂活動是用來將工作流程中特定的商務程序模型化。 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 中提供了活動程式庫範本，可讓您透過 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 來以視覺方式建立這類自訂活動。  
  
### <a name="to-create-a-workflow-activity-library"></a>若要建立工作流程活動程式庫  
  
1.  啟動 [!INCLUDE[vs2010](../includes/vs2010-md.md)]。  
  
2.  在 **檔案**功能表上，指向**新增**，然後選取 **專案...**.  
  
     [ **新增專案** ] 對話方塊隨即開啟。  
  
3.  在 **專案類型**窗格中，選取**工作流程**從**Visual C#** 專案或**Visual Basic**群組取決於您語言喜好設定。  
  
4.  在 **範本**窗格中，選取**活動程式庫**。  
  
5.  在 [**名稱**] 方塊中，為您的專案的描述性名稱讓您輕鬆地識別的型別。  
  
6.  在**位置**方塊中，輸入您要儲存您的專案，或按一下 目錄**瀏覽**來巡覽找到它。  
  
7.  在 **解決方案**方塊中，輸入描述性的名稱，您的解決方案，然後按一下**確定**。  
  
    > [!NOTE]
    >  如果您想要新增至現有的方案工作流程主控台應用程式，開啟該方案中的[!INCLUDE[vs2010](../includes/vs2010-md.md)]，以滑鼠右鍵按一下方案中的**方案總管 中**，然後選取**新增**，然後**新增專案...** 若要開啟 [**新的專案**] 對話方塊。 依照本程序上面的說明繼續進行。  
  
8.  專案範本會以 XAML 格式建立活動定義。 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 會開啟並顯示自訂活動的畫布。  
  
9. 活動拖曳**工具箱**至設計介面，以將它包含在您的自訂活動。  
  
    > [!CAUTION]
    >  自訂活動的主體中僅可有一個子活動，但是該子活動可以是複合活動，例如 <xref:System.Activities.Statements.Sequence> 活動或 <xref:System.Activities.Statements.Flowchart> 活動。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 建立活動](http://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)