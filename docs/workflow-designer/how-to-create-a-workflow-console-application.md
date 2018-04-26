---
title: 工作流程設計工具-如何： 建立工作流程主控台應用程式
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6461a644bdedd3d391059cd8a3a17f887e77c6b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-workflow-console-application"></a>HOW TO：建立工作流程主控台應用程式

Windows Workflow Foundation (WF) 可讓您建立執行系統或人工處理序的工作流程。 Windows 工作流程設計工具提供建立這些工作流程設計介面。 工作流程設計工具可以用來建立從 Visual Studio 內的工作流程或重新裝載設計工具的其他應用程式整合。

本主題描述如何使用 Visual Studio 2010 中的工作流程設計工具建立的工作流程主控台應用程式中。

## <a name="to-create-a-workflow-console-application"></a>若要建立工作流程主控台應用程式

1.  啟動 Visual Studio 2010。

2.  在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。

     [ **新增專案** ] 對話方塊隨即開啟。

3.  在**已安裝的範本**窗格中，選取**工作流程**從其中**Visual C#** 或**Visual Basic**分組，取決於您喜好設定的語言。

4.  在中間窗格中，選取**工作流程主控台應用程式**。

5.  在**名稱**方塊中，輸入您的專案讓您輕鬆識別的描述性名稱。

6.  在**位置**方塊中，輸入您要儲存您的專案，或按一下的目錄**瀏覽**來巡覽找到它。

7.  在**方案**方塊中，輸入新方案的名稱。 按一下**確定**建立應用程式。

    > [!NOTE]
    > 如果您想要新增至現有的方案工作流程主控台應用程式，在 Visual Studio 2010 中開啟該方案，以滑鼠右鍵按一下方案中的**方案總管 中**，然後選取**新增**，然後**新的專案**開啟**新專案** 對話方塊。 依照本程序上面的說明繼續進行。

8.  專案範本會以 XAML 建立工作流程定義，而主控台應用程式定義會使用原始程式碼。 工作流程設計工具開啟，並顯示您所建立之工作流程的畫布。

9. 若要撰寫工作流程，拖曳活動或其他工作流程項目從**工具箱**到在您的工作流程設計介面。

## <a name="see-also"></a>另請參閱

- [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)