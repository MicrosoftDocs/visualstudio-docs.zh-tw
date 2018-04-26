---
title: 工作流程設計工具的偵錯工作流程，從遠端電腦 （舊版）
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 391180cd76fe5e0cccca802ba1cbfb78277dabc1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>從遠端電腦偵錯工作流程 (舊版)

本主題描述如何偵錯遠端舊版 Windows Workflow Foundation (WF) 建置的應用程式會與舊版的 Windows 工作流程設計工具。 您的應用程式需要.NET Framework 3.5 版或 WinFX 為目標時，請使用舊版工作流程設計工具。

 當您安裝 Visual Studio 時，其中一個元件的安裝選項是安裝 Visual Studio 偵錯工具的 Windows Workflow Foundation (WF)。 這會安裝遠端偵錯元件。 這些遠端偵錯元件必須安裝在要進行遠端工作流程偵錯的目標電腦上。

 此外，包含您在遠端電腦上所偵錯之舊版工作流程之工作流程定義的組件，必須安裝在進行偵錯的來源本機電腦的全域組件快取 (GAC) 中。 例如，如果舊版工作流程是在遠端電腦 A 上執行，而您要從本機電腦 B 偵錯該工作流程，則工作流程定義必須位於電腦 B 的 GAC 中。如此可讓設計工具將執行於遠端電腦 A 之工作流程的工作流程標記，在電腦 B 上還原序列化並加以顯示。如需全域組件快取的詳細資訊，請參閱 MSDN Library。

 Windows Workflow Foundation 遠端偵錯的運作方式與其他 Visual Studio 元件的遠端偵錯功能相同。 如需詳細資訊，請參閱 Visual Studio 遠端偵錯 MSDN Library 中。

## <a name="see-also"></a>另請參閱

- [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)