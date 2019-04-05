---
title: HOW TO：建立活動設計工具程式庫 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 69d68fdc0a34ffa680ec2306a087cd29002eb185
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944943"
---
# <a name="how-to-create-an-activity-designer-library"></a>HOW TO：建立活動設計工具程式庫
自訂活動設計工具可讓您建立標準或自訂活動的使用者介面。 您可以控制使用者介面的複雜性，並且能為活動建立多個設計工具。 這個案例可讓您建立專為多個對象量身訂做的設計工具。  
  
### <a name="to-create-an-activity-designer-library"></a>若要建立活動設計工具程式庫  
  
1.  啟動 [!INCLUDE[vs2010](../includes/vs2010-md.md)]。  
  
2.  在 **檔案**功能表上，指向**新增**，然後選取 **專案...** 若要開啟 [**新的專案**] 對話方塊。  
  
3.  在 **專案類型**窗格中，選取**工作流程**從其中**Visual C#** 或**Visual Basic**取決於您慣用的群組語言。  
  
4.  在 **範本**窗格中，選取**活動設計工具程式庫**。  
  
5.  在 **名稱**方塊中，輸入您的專案，讓您輕鬆地識別的描述性名稱。  
  
6.  在 **位置**方塊中，輸入您要儲存您的專案，或按一下 的目錄**瀏覽**來巡覽找到它。  
  
7.  在 **解決方案**方塊中，輸入描述性的名稱，您的解決方案，然後按一下**確定**。  
  
    > [!NOTE]
    >  如果您想要新增至現有的方案工作流程主控台應用程式，開啟該方案中的[!INCLUDE[vs2010](../includes/vs2010-md.md)]，在方案上按一下滑鼠右鍵**方案總管 中**，然後選取**新增**，則**新增專案...** 若要開啟 [**新的專案**] 對話方塊。 依照本程序上面的說明繼續進行。  
  
8.  專案範本是以 XAML 建立活動設計工具定義，以及使用原始程式碼建立程式碼後置實作檔案。 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 會開啟並顯示活動設計工具的畫布。  
  
9. 拖曳[!INCLUDE[avalon1](../includes/avalon1-md.md)]控制項從**工具箱**至設計介面，以在您的自訂活動設計工具中使用它們。  如需如何實作自訂活動設計工具的範例，請參閱[How to:建立自訂活動設計工具](http://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31)。  
  
    > [!WARNING]
    >  自訂活動設計工具可以用於自訂活動，也可用於預設[!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]活動。  
  
## <a name="see-also"></a>另請參閱  
 [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)