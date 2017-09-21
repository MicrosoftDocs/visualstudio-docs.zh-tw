---
title: "註冊工具視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "註冊管理工具視窗"
  - "註冊的工具視窗"
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 註冊工具視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以註冊工具視窗 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 和  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## 範例  
  
```c#  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 在上述程式碼中 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 向 Visual Studio 的 \[PersistedWindowPane 和 DynamicWindowPane 工具視窗。 持續性的工具視窗停駐，並使用索引標籤式 **方案總管\] 中**, ，以及 \[動態\] 視窗中指定的開始位置和大小的預設值。 \[動態\] 視窗是由暫時性的表示不建立在啟動。 這在 ToolWindows 機碼，在系統登錄中寫入 DontForceCreate 的值。 如需詳細資訊，請參閱[工具視窗中顯示設定](../extensibility/tool-window-display-configuration.md)。