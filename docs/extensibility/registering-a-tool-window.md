---
title: 註冊工具視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34fddd6513aad612398c700b935c6d1d3ee72b59
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186271"
---
# <a name="register-a-tool-window"></a>註冊工具視窗
您可以使用 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 和 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>來註冊您的工具視窗。

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

 在上述程式碼中，<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 會向 Visual Studio 註冊 `PersistedWindowPane` 和 `DynamicWindowPane` 工具視窗。 保存的工具視窗會停駐並以**方案總管**的索引標籤，而動態視窗會提供預設的開始位置和大小。 動態視窗會成為暫時性，這表示它不會在啟動時建立。 這會在系統登錄的 `ToolWindows` 機碼中寫入 `DontForceCreate` 值。 如需詳細資訊，請參閱[工具視窗顯示設定](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015)。
