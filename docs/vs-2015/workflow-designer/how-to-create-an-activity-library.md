---
title: How to：建立活動程式庫 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662749"
---
# <a name="how-to-create-an-activity-library"></a>HOW TO：建立活動程式庫
自訂活動是用來將工作流程中特定的商務程序模型化。 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 中提供了活動程式庫範本，可讓您透過 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 來以視覺方式建立這類自訂活動。

### <a name="to-create-a-workflow-activity-library"></a>若要建立工作流程活動程式庫

1. 啟動 [!INCLUDE[vs2010](../includes/vs2010-md.md)]。

2. **在 [檔案**] 功能表上，指向 [**新增**]，然後選取 [**專案**]。

     此時會開啟 [新增專案]**** 對話方塊。

3. 在 [**專案類型**] 窗格中，根據您的語言喜好設定，選取**Visual c #** 專案或**Visual Basic**群組中的**工作流程**。

4. 在 [ **範本** ] 窗格中，選取 [ **活動程式庫**]。

5. 在 [ **名稱** ] 方塊中，輸入專案的描述性名稱，以方便識別。

6. 在 [ **位置** ] 方塊中，輸入您要儲存專案的目錄，或按一下 **[流覽]** 流覽至該目錄。

7. 在 [ **方案** ] 方塊中，輸入解決方案的描述性名稱，然後按一下 **[確定]**。

    > [!NOTE]
    > 如果您想要將工作流程主控台應用程式加入至現有的方案，請在中開啟該方案 [!INCLUDE[vs2010](../includes/vs2010-md.md)] ，以滑鼠右鍵按一下**方案總管**中的方案，然後依序選取 [新增] 和 [**新增專案** ** **]。 以開啟 [ **新增專案** ] 對話方塊。 依照本程序上面的說明繼續進行。

8. 專案範本會以 XAML 格式建立活動定義。 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 會開啟並顯示自訂活動的畫布。

9. 將 [ **工具箱** ] 中的活動拖曳至設計介面，將它包含在您的自訂活動中。

    > [!CAUTION]
    > 自訂活動的主體中僅可有一個子活動，但是該子活動可以是複合活動，例如 <xref:System.Activities.Statements.Sequence> 活動或 <xref:System.Activities.Statements.Flowchart> 活動。

## <a name="see-also"></a>另請參閱
 [如何：建立活動](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)[建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)