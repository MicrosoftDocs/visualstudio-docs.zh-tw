---
title: 工作流程設計工具-如何： 建立循序工作流程程式庫 （舊版）
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ed341481ec3e82165a9f4cefd71eb362781d96c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970252"
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>HOW TO：建立循序工作流程程式庫 (舊版)

請遵循下列步驟來建立使用 Windows 工作流程設計工具提供的舊版的 Visual Studio 2010 的循序工作流程程式庫專案。 當您需要以.NET Framework 3.5 版或 WinFX 為目標時，請使用舊版工作流程設計工具。

## <a name="to-create-a-sequential-workflow-library-project"></a>若要建立循序工作流程程式庫專案

1.  啟動 Visual Studio。

2.  在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。

     [ **新增專案** ] 對話方塊隨即開啟。

3.  選取 [ **.NET Framework 3.0**選項或 **.NET Framework 3.5**在清單頂端的下拉式選項**新專案**存取舊版設計工具] 視窗。

    > [!NOTE]
    > Visual Studio 2010 中的預設選項是 **.NET Framework 4**。 這個選項用來建立.NET Framework 4 為目標的 Windows Workflow Foundation (WF) 應用程式並不會使用舊版設計工具。

4.  在**專案類型**窗格中，選取 Visual C# 或 Visual Basic (在**其他語言**)，然後選取**工作流程**。

5.  在**範本**窗格中，選取**循序工作流程程式庫**。

6.  在**名稱**方塊中，輸入您的專案讓您輕鬆識別的描述性名稱。

7.  在**位置**方塊中，輸入您要儲存您的專案，或按一下的目錄**瀏覽**來巡覽找到它。

     如果您想要建立專案的方案目錄，選取**為方案建立目錄**核取方塊，然後輸入中的名稱**方案名稱**方塊。

8.  按一下 [確定 **Deploying Office Solutions**]。

## <a name="see-also"></a>另請參閱

- [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)
- [工作流程的撰寫樣式](http://msdn.microsoft.com/en-us/aacf4ec6-da05-4974-958a-974769dda739)