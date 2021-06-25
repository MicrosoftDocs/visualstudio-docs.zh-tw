---
title: 註冊工具視窗 |Microsoft Docs
description: 瞭解如何使用 ProvideToolWindowAttribute 和 ProvideToolWindowVisibilityAttribute 向 Visual Studio 註冊您的工具視窗。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f4fb6330f913989a69c5d8d28374a40ea14d266d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899091"
---
# <a name="register-a-tool-window"></a>註冊工具視窗
您可以使用和註冊您的工具視窗 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> 。

## <a name="example"></a>範例

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 在上述程式碼中，會 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> `PersistedWindowPane` 使用 Visual Studio 註冊和 `DynamicWindowPane` 工具視窗。 保存的工具視窗會停駐，並以 **方案總管** 為索引標籤，而且動態視窗會獲得預設的開始位置和大小。 動態視窗會成為暫時性的，這表示它不會在啟動時建立。 這會將 `DontForceCreate` 值寫入系統登錄中的機 `ToolWindows` 碼。 如需詳細資訊，請參閱 [工具視窗顯示設定](/previous-versions/visualstudio/visual-studio-2015/extensibility/tool-window-display-configuration?preserve-view=true&view=vs-2015)。