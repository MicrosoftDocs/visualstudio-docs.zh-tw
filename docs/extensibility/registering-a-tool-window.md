---
title: 註冊工具視窗 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e7971de5ae5301d99147bbfc374dda6b039662a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701593"
---
# <a name="register-a-tool-window"></a>註冊工具視窗
您可以使用<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>和<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>註冊工具視窗。

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

 在上面的代碼中,<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>`PersistedWindowPane`將`DynamicWindowPane`和工具視窗與 Visual Studio 註冊。 持久化工具視窗與**解決方案資源管理器**停靠並選項卡化,並且動態視窗被賦予預設起始位置和大小。 動態視窗為瞬態視窗,表示它不是在啟動時創建的。 這將在系統`DontForceCreate`註冊表`ToolWindows`中的 密鑰中寫入值。 關於詳細資訊,請參考[工具視窗顯示設定](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015)。
