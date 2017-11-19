---
title: "註冊工具視窗 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79a2d2f1e9dc130fc280ce61ec282f30e55024ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="registering-a-tool-window"></a>註冊工具視窗
您可以註冊您使用的工具視窗<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>和<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## <a name="example"></a>範例  
  
```csharp  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 在上述程式碼中<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>註冊使用 Visual Studio 工具視窗 PersistedWindowPane 和 DynamicWindowPane。 保存的工具視窗停駐，並使用索引標籤式**方案總管 中**，以及動態視窗指定的開始位置和大小的預設值。 [動態] 視窗是由暫時性的這表示，它不建立在啟動。 這會寫入 DontForceCreate 值 ToolWindows 索引鍵，在系統登錄中。 如需詳細資訊，請參閱[工具視窗顯示組態](../extensibility/tool-window-display-configuration.md)。