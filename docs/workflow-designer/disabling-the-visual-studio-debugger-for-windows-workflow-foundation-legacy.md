---
title: "停用 Visual Studio Debugger for Windows Workflow Foundation （舊版） |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d3ec3d87952f17feb8a59ae8acbda603451fbf4d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>停用 Visual Studio Debugger for Windows Workflow Foundation (舊版)

本主題描述如何停用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]偵錯工具 建置時使用的組態檔[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]舊版的 Windows 工作流程設計工具中的應用程式。 當您需要以 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。

 根據預設，將會針對主機處理序啟用 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]。 若要停用工作流程偵錯，您必須明確地關閉它將"DisableWorkflowDebugging"項目新增**\<參數 >**中的項目 **\<system.diagnostics >**主機組態檔區段。

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