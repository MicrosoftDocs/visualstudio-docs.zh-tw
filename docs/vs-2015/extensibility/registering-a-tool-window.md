---
title: 註冊工具視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8178938715278bf69fe8f4cc1b336bbd19cec04e
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "58945306"
---
# <a name="registering-a-tool-window"></a>註冊工具視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以註冊您使用的工具視窗<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>和  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## <a name="example"></a>範例  
  
```csharp  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 在上述程式碼中<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>向 Visual Studio 中的工具視窗 PersistedWindowPane 和 DynamicWindowPane。 保存的工具視窗停駐，並使用索引標籤式**方案總管 中**，且 動態 視窗會以預設的開始位置和大小。 [動態] 視窗是由暫時性的這表示，它不建立在啟動。 這會寫入 DontForceCreate 值 ToolWindows 機碼在系統登錄中。 如需詳細資訊，請參閱 <<c0> [ 工具視窗中顯示組態](../extensibility/tool-window-display-configuration.md)。
