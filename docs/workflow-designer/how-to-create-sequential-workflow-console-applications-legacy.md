---
title: 工作流程設計工具-如何： 建立循序工作流程主控台應用程式 （舊版）
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb4e048fdf8eb8fee541f84656a29427b5a07a1d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973215"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>HOW TO：建立循序工作流程主控台應用程式 (舊版)

請遵循下列步驟來建立循序工作流程主控台應用程式專案中使用 Windows 工作流程設計工具提供的舊版的 Visual Studio 2010。 當您需要以.NET Framework 3.5 版或 WinFX 為目標時，請使用舊版工作流程設計工具。

## <a name="to-create-a-sequential-workflow-console-application"></a>若要建立循序工作流程主控台應用程式

1.  啟動 Visual Studio。

2.  在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。

     [ **新增專案** ] 對話方塊隨即開啟。

3.  選取 [ **.NET Framework 3.0**選項或 **.NET Framework 3.5**在清單頂端的下拉式選項**新專案**存取舊版設計工具] 視窗。

    > [!NOTE]
    > Visual Studio 2010 中的預設選項是 **.NET Framework 4**。 這個選項用來建立.NET Framework 4 為目標的 Windows Workflow Foundation (WF) 應用程式並不會使用舊版設計工具。

4.  在**專案類型**窗格中，選取 Visual C# 專案或 Visual Basic 專案 (下**其他語言**)，然後選取**工作流程**。

5.  在**範本**窗格中，選取**循序工作流程主控台應用程式**。

6.  在**名稱**方塊中，輸入您的專案讓您輕鬆識別的描述性名稱。

7.  在**位置**方塊中，輸入您要儲存您的專案，或按一下的目錄**瀏覽**來巡覽找到它。

     接著會開啟 Windows Form 設計工具，顯示您剛剛建立之專案的 Form1。

8.  按一下 [確定 **Deploying Office Solutions**]。

     工作流程設計工具會開啟並顯示您所建立的循序工作流程之設計介面。

9. 活動拖曳至**工具箱**至設計介面中**將活動置放在**指定區域。

## <a name="see-also"></a>另請參閱

- [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)
- [開發工作流程](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)