---
title: 如何：建立活動程式庫 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dec73d392dc6af74e5daef99bd6d306f7d58409
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662749"
---
# <a name="how-to-create-an-activity-library"></a>HOW TO：建立活動程式庫
自訂活動是用來將工作流程中特定的商務程序模型化。 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 中提供了活動程式庫範本，可讓您透過 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 來以視覺方式建立這類自訂活動。

### <a name="to-create-a-workflow-activity-library"></a>若要建立工作流程活動程式庫

1. 啟動 [!INCLUDE[vs2010](../includes/vs2010-md.md)]。

2. **在 [檔案**] 功能表上，指向 [**新增**]，然後選取 [**專案**]。

     [ **新增專案** ] 對話方塊隨即開啟。

3. 在 [**專案類型**] 窗格中，根據您的語言喜好設定，從 [**視覺效果C#** 專案] 或 [ **Visual Basic** ] 群組選取 [**工作流程**]。

4. 在 [**範本**] 窗格中，選取 [**活動程式庫**]。

5. 在 [**名稱**] 方塊中，輸入專案的描述性名稱，使其易於識別。

6. 在 [**位置**] 方塊中，輸入您要儲存專案的目錄，或按一下 **[流覽]** 以流覽至它。

7. 在 [**方案**] 方塊中，輸入解決方案的描述性名稱，然後按一下 **[確定]** 。

    > [!NOTE]
    > 如果您想要將工作流程主控台應用程式加入至現有的方案，請在 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 中開啟該方案，在**方案總管**中以滑鼠右鍵按一下方案，然後依**序選取 [新增] 和 [** **新增專案**]。 以開啟 [**新增專案**] 對話方塊。 依照本程序上面的說明繼續進行。

8. 專案範本會以 XAML 格式建立活動定義。 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 會開啟並顯示自訂活動的畫布。

9. 將活動從 [**工具箱**] 拖曳至設計介面，以將它包含在您的自訂活動中。

    > [!CAUTION]
    > 自訂活動的主體中僅可有一個子活動，但是該子活動可以是複合活動，例如 <xref:System.Activities.Statements.Sequence> 活動或 <xref:System.Activities.Statements.Flowchart> 活動。

## <a name="see-also"></a>請參閱
 [如何：建立](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)建立[工作流程專案](../workflow-designer/creating-a-workflow-project.md)的活動