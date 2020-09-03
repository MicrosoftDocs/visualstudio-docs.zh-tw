---
title: 如何：建立活動設計工具程式庫 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 63404d3d81c44ac4b8308d949cdb87df419f2e04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662864"
---
# <a name="how-to-create-an-activity-designer-library"></a>HOW TO：建立活動設計工具程式庫
自訂活動設計工具可讓您建立標準或自訂活動的使用者介面。 您可以控制使用者介面的複雜性，並且能為活動建立多個設計工具。 這個案例可讓您建立專為多個對象量身訂做的設計工具。

### <a name="to-create-an-activity-designer-library"></a>若要建立活動設計工具程式庫

1. 啟動 [!INCLUDE[vs2010](../includes/vs2010-md.md)]。

2. **在 [檔案**] 功能表上，指向 [**新增**]，然後選取 [**專案**]。 以開啟 [ **新增專案** ] 對話方塊。

3. 在 [**專案類型**] 窗格中，根據您慣用的語言，選取**Visual c #** 或**Visual Basic**分組的**工作流程**。

4. 在 [ **範本** ] 窗格中，選取 [ **活動設計**工具程式庫]。

5. 在 [ **名稱** ] 方塊中，輸入專案的描述性名稱，以方便識別。

6. 在 [ **位置** ] 方塊中，輸入您要用來儲存專案的目錄，或按一下 **[流覽]** 流覽至該目錄。

7. 在 [ **方案** ] 方塊中，輸入解決方案的描述性名稱，然後按一下 **[確定]**。

    > [!NOTE]
    > 如果您想要將工作流程主控台應用程式加入至現有的方案，請在中開啟該方案 [!INCLUDE[vs2010](../includes/vs2010-md.md)] ，以滑鼠右鍵按一下**方案總管**中**Add**的方案，然後依序選取 [新增] 和 [**新增專案**]。 以開啟 [ **新增專案** ] 對話方塊。 依照本程序上面的說明繼續進行。

8. 專案範本是以 XAML 建立活動設計工具定義，以及使用原始程式碼建立程式碼後置實作檔案。 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 會開啟並顯示活動設計工具的畫布。

9. 將 [!INCLUDE[avalon1](../includes/avalon1-md.md)] 控制項從 [ **工具箱** ] 拖曳至設計介面，以便在您的自訂活動設計工具中使用它們。  如需如何執行自訂活動設計工具的範例，請參閱 how [to：建立自訂活動設計](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31)工具。

    > [!WARNING]
    > 自訂活動設計工具可用於自訂活動以及預設 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 活動。

## <a name="see-also"></a>另請參閱
 [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)