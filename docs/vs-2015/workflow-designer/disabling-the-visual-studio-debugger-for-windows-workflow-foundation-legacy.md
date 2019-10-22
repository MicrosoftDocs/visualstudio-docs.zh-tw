---
title: 停用 Windows Workflow Foundation 的偵錯工具（舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eddd72d648e7349f51096a21131f38c2e370a277
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656791"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>停用 Visual Studio Debugger for Windows Workflow Foundation (舊版)
本主題描述在舊版 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中建置 [!INCLUDE[wf](../includes/wf-md.md)] 應用程式時，如何透過組態檔停用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 偵錯工具。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。

 根據預設，將會針對主機處理序啟用 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for [!INCLUDE[wf](../includes/wf-md.md)]。 若要停用工作流程偵錯工具，您必須在主機設定檔的 **\<system 診斷 >** 區段中，新增 "DisableWorkflowDebugging" 專案 **\<switches >** 元素，明確地關閉它。

 下列範例顯示如何修改主機組態檔來停用工作流程偵錯。

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>請參閱
 叫用[適用于 Windows Workflow Foundation （舊版）的 Visual Studio 偵錯工具，以將](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)[舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)