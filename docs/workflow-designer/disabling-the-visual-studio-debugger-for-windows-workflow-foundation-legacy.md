---
title: 工作流程設計工具-停用 Visual Studio Debugger for Windows Workflow Foundation （舊版）
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 473ee507e35f5ec5df902df64ee34326dcf90a2b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>停用 Visual Studio Debugger for Windows Workflow Foundation (舊版)

本主題描述如何停用 Visual Studio 偵錯工具建置在舊版的 Windows 工作流程設計工具中的 Windows Workflow Foundation (WF) 應用程式時，使用組態檔。 當您需要以.NET Framework 3.5 版或 WinFX 為目標時，請使用舊版工作流程設計工具。

 根據預設，Visual Studio 偵錯工具的 Windows Workflow Foundation (WF) 會啟用主機處理程序。 若要停用工作流程偵錯，您必須明確地關閉它將"DisableWorkflowDebugging"項目新增**\<參數 >** 中的項目 **\<system.diagnostics >** 主機組態檔區段。

 下列範例顯示如何修改主機組態檔來停用工作流程偵錯。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [叫用 Visual Studio Debugger for Windows Workflow Foundation (舊版)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)