---
title: "如何： 建立工作流程專案 （舊版） |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: dc38c6b323ee06ed9b312811eb892e7654134d05
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-workflow-projects-legacy"></a>HOW TO：建立工作流程專案 (舊版)
請依照這些步驟來建立以 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 為目標的 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 專案。 此程序會使用舊版所提供的 Windows 工作流程設計工具[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]。

### <a name="to-create-a-workflow-project"></a>若要建立工作流程專案

1.  啟動 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]。

2.  在**檔案**功能表上，指向**新增**，然後選取**專案**。

     [ **新增專案** ] 對話方塊隨即開啟。

3.  選取 [ **.NET Framework 3.0**選項或**.NET Framework 3.5**在清單頂端的下拉式選項**新專案**存取舊版設計工具] 視窗。

    > [!NOTE]
    > 中的預設選項[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]是**.NET Framework 4**。 這個選項是用來建立以 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 為目標的 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 應用程式，而不會使用舊版設計工具。

4.  在**專案類型** 窗格中，選取 Visual C# 專案或 Visual Basic 專案，然後選取**工作流程**。

5.  在**範本** 窗格中，選取其中一個已安裝的專案範本：

    -   循序工作流程主控台應用程式

    -   循序工作流程程式庫

    -   工作流程活動程式庫

    -   狀態機器工作流程主控台應用程式

    -   狀態機器工作流程程式庫

    -   空白工作流程專案

6.  在**名稱**方塊中，輸入您的專案讓您輕鬆識別的描述性名稱。

7.  在**位置**方塊中，輸入您要儲存您的專案，或按一下的目錄**瀏覽**瀏覽至目錄。

     如果您想要建立專案的方案目錄，選取**為方案建立目錄**核取方塊，然後輸入中的名稱**方案名稱**方塊。

8.  按一下 [確定 **Deploying Office Solutions**]。

## <a name="see-also"></a>另請參閱

- [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)