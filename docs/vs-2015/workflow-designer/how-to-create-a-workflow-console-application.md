---
title: 如何：建立工作流程主控台應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1334655f2a8b8587922628664e43784b54ce971
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604924"
---
# <a name="how-to-create-a-workflow-console-application"></a>HOW TO：建立工作流程主控台應用程式
[!INCLUDE[wf](../includes/wf-md.md)] 可讓您建立工作流程來執行系統或人力流程。 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 會提供建立這些工作流程的設計介面。 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 可用來從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 建立工作流程，或者可以整合到重新裝載設計工具的其他應用程式中。

 本主題描述如何在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 中使用 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 建立主控台應用程式中的工作流程。

### <a name="to-create-a-workflow-console-application"></a>若要建立工作流程主控台應用程式

1. 啟動 [!INCLUDE[vs2010](../includes/vs2010-md.md)]。

2. **在 [檔案**] 功能表上，指向 [**新增**]，然後選取 [**專案**]。

     此時會開啟 [新增專案]**** 對話方塊。

3. 在 [**已安裝的範本**] 窗格中，根據您偏好的語言，從**Visual c #** 或**Visual Basic**群組中選取**工作流程**。

4. 在中間窗格中，選取 [ **工作流程主控台應用程式**]。

5. 在 [ **名稱** ] 方塊中，輸入專案的描述性名稱，以方便識別。

6. 在 [ **位置** ] 方塊中，輸入您要用來儲存專案的目錄，或按一下 **[流覽]** 流覽至該目錄。

7. 在 [ **方案** ] 方塊中，輸入新方案的名稱。 按一下 **[確定]** 以建立應用程式。

    > [!NOTE]
    > 如果您想要將工作流程主控台應用程式加入至現有的方案，請在中開啟該方案 [!INCLUDE[vs2010](../includes/vs2010-md.md)] ，以滑鼠右鍵按一下**方案總管**中的方案，然後依序選取 [新增] 和 [**新增專案** ** **]。 以開啟 [ **新增專案** ] 對話方塊。 依照本程序上面的說明繼續進行。

8. 專案範本會以 XAML 建立工作流程定義，而主控台應用程式定義會使用原始程式碼。 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 會開啟並顯示您所建立之工作流程的畫布。

9. 若要撰寫工作流程，請從 [ **工具箱** ] 將活動或其他工作流程專案拖曳到工作流程中的設計介面。

## <a name="see-also"></a>另請參閱
 [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)