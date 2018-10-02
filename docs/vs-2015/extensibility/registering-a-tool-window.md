---
title: 註冊工具視窗 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2ec947455383fd1d2a22ec98f8627ee53fbbad5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496951"
---
# <a name="registering-a-tool-window"></a>註冊工具視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[註冊的工具視窗](https://docs.microsoft.com/visualstudio/extensibility/registering-a-tool-window)。  
  
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

