---
title: HOW TO：建立工作流程主控台應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 33666c0e5d63d8d4d33d544fcfe18d8c185ce843
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044348"
---
# <a name="how-to-create-a-workflow-console-application"></a>HOW TO：建立工作流程主控台應用程式
[!INCLUDE[wf](../includes/wf-md.md)] 可讓您建立執行系統或人工處理序的工作流程。 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 會提供建立這些工作流程的設計介面。 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 可用來從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 建立工作流程，或者可以整合到重新裝載設計工具的其他應用程式中。  
  
 本主題描述如何在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 中使用 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 建立主控台應用程式中的工作流程。  
  
### <a name="to-create-a-workflow-console-application"></a>若要建立工作流程主控台應用程式  
  
1. 啟動 [!INCLUDE[vs2010](../includes/vs2010-md.md)]。  
  
2. 在 **檔案**功能表上，指向**新增**，然後選取 **專案...**.  
  
     [ **新增專案** ] 對話方塊隨即開啟。  
  
3. 在 **已安裝的範本**窗格中，選取**工作流程**從其中**Visual C#** 或**Visual Basic**分組，取決於您語言喜好設定。  
  
4. 在中間窗格中，選取**工作流程主控台應用程式**。  
  
5. 在 **名稱**方塊中，輸入您的專案，讓您輕鬆地識別的描述性名稱。  
  
6. 在 **位置**方塊中，輸入您要儲存您的專案，或按一下 的目錄**瀏覽**來巡覽找到它。  
  
7. 在 **解決方案**方塊中，輸入新方案的名稱。 按一下 **確定**建立應用程式。  
  
    > [!NOTE]
    >  如果您想要新增至現有的方案工作流程主控台應用程式，開啟該方案中的[!INCLUDE[vs2010](../includes/vs2010-md.md)]，以滑鼠右鍵按一下方案中的**方案總管 中**，然後選取**新增**，然後**新增專案...** 若要開啟 [**新的專案**] 對話方塊。 依照本程序上面的說明繼續進行。  
  
8. 專案範本會以 XAML 建立工作流程定義，而主控台應用程式定義會使用原始程式碼。 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 會開啟並顯示您所建立之工作流程的畫布。  
  
9. 若要撰寫工作流程，拖曳活動或從其他工作流程項目**工具箱**到在您的工作流程設計介面。  
  
## <a name="see-also"></a>另請參閱  
 [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)