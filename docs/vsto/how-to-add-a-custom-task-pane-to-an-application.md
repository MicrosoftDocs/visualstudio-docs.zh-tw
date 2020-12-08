---
title: 如何：將自訂工作窗格加入至應用程式
description: 瞭解如何使用 Visual Studio Tools for Office (VSTO) 增益集，將自訂工作窗格加入至應用程式。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1e8056eddef6329aeb10ed5545c4146f0af0f167
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845046"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>如何：將自訂工作窗格加入至應用程式
  您可以使用 VSTO 增益集，將自訂工作窗格加入上面所列的應用程式。 如需詳細資訊，請參閱 [自訂工作窗格](../vsto/custom-task-panes.md)。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="add-a-custom-task-pane-to-an-application"></a>將自訂工作窗格加入至應用程式

### <a name="to-add-a-custom-task-pane-to-an-application"></a>若要在應用程式中加入自訂工作窗格

1. 針對上面所列的其中一個應用程式，開啟或建立 VSTO 增益集專案。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

2. 在 [專案]  功能表上，按一下 [加入使用者控制項] 。

3. 在 [ **加入新專案** ] 對話方塊中，將新使用者控制項的名稱變更為 **MyUserControl**，然後按一下 [ **加入**]。

     使用者控制項隨即在設計工具中開啟。

4. 將一或多個 Windows Forms 控制項從 [ **工具箱** ] 加入至使用者控制項。

5. 開啟 **ThisAddIn.cs** 或 **ThisAddIn .vb** 程式碼檔案。

6. 將下列程式碼新增至 `ThisAddIn` 類別。 此程式碼會將 `MyUserControl` 和 <xref:Microsoft.Office.Tools.CustomTaskPane> 的執行個體宣告為 `ThisAddIn` 類別的成員。

     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]

7. 將下列程式碼加入至 `ThisAddIn_Startup` 事件處理常式。 此程式碼會建立新的 <xref:Microsoft.Office.Tools.CustomTaskPane> ，方法是將 `MyUserControl` 物件加入 `CustomTaskPanes` 集合。 程式碼也會顯示工作窗格。

     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

    > [!NOTE]
    > 這個程式碼會使您自訂的工作窗格與應用程式中的現用視窗相關聯。 對於某些應用程式，您可能想要修改這個程式碼以確保工作窗格會隨其他文件或項目一起在應用程式中顯示。 如需詳細資訊，請參閱 [自訂工作窗格](../vsto/custom-task-panes.md)。

## <a name="see-also"></a>另請參閱
- [Office UI 自訂](../vsto/office-ui-customization.md)
- [自訂工作窗格](../vsto/custom-task-panes.md)
- [逐步解說：從自訂工作窗格自動化應用程式](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
