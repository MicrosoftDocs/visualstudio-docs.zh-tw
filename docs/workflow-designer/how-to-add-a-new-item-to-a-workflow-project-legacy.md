---
title: 工作流程設計工具-如何： 將新的項目加入至工作流程專案 （舊版）
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d6e9607f4924057568849fd7eabd4567130dc2f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>HOW TO：將新的項目加入至工作流程專案 (舊版)

建立使用 Windows 工作流程設計工具所提供 Visual Studio 2010 為目標的.NET Framework 3.5 版或 WinFX 舊版工作流程專案之後，您可以加入 Windows Workflow Foundation (WF) 項目和其他熟悉的 Visual Studio您的專案項目。

下表列出您可新增至工作流程專案的 Windows Workflow Foundation 項目。

|項目|描述|
|----------|-----------------|
|活動|活動定義置於設計工具程式碼檔案，且使用者程式碼置於不同程式碼檔案的活動。|
|活動 (程式碼分開置放)|活動定義表示成工作流程標記，且使用者程式碼置於不同的程式碼檔案。|
|循序工作流程 (程式碼)|工作流程定義置於設計工具程式碼檔案，且使用者程式碼置於不同程式碼檔案的循序工作流程。|
|循序工作流程 (程式碼分開置放)|工作流程定義表示成工作流程標記，且使用者程式碼置於不同程式碼檔案的循序工作流程。|
|狀態機器工作流程 (程式碼)|工作流程定義置於設計工具程式碼檔案，且使用者程式碼置於不同程式碼檔案的狀態機器工作流程。|
|狀態機器工作流程 (程式碼分開置放)|工作流程定義表示成工作流程標記，且使用者程式碼置於不同程式碼檔案的狀態機器工作流程。|

## <a name="to-add-a-new-item-to-a-workflow-project"></a>若要將新的項目加入至工作流程專案

1.  在**專案**功能表上，按一下 **加入新項目**。

     **加入新項目**對話方塊隨即開啟。

2.  選取項目。

     上表列出可用的 Windows Workflow Foundation 選擇。

3.  按一下**新增**將項目加入至工作流程專案。

## <a name="see-also"></a>另請參閱

- [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)