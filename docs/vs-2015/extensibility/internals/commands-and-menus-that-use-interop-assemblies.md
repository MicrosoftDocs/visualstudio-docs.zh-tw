---
title: 使用 Interop 組件的命令和功能表 |Microsoft Docs
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
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d050f2e96eb78462f9e5e77504a365d17ed01d6d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484969"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>使用 Interop 組件的命令和功能表
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[命令和功能表，使用 Interop 組件](https://docs.microsoft.com/visualstudio/extensibility/internals/commands-and-menus-that-use-interop-assemblies)。  
  
使用 interop 組件中實作功能表和工具列命令的 VSPackage 必須：  
  
-   通知[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]有關其支援的命令和是否在目前啟用的整合式的開發環境 (IDE)。  
  
-   遵守的規則 （合約） 處理的命令。  
  
-   明確實作命令處理，使用其中一種<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面。  
  
 以下說明如何執行這些工作。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 Interop 組件判斷命令狀態](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 描述 VSPackage 如何通知 IDE 在它支援哪些命令的相關，而且是否在目前啟用。  
  
 [Interop 組件中的命令合約](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 提供所有的 Vspackage 實作使用 interop 組件的命令所使用的基本命令合約的定義  
  
 [實作](../../extensibility/internals/command-implementation.md)  
 提供 VSPackage 如何實作命令的概觀。  
  
 [註冊 Interop 組件命令處理常式](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 說明通知 IDE VSPackage 提供的命令處理常式所需的登錄項目。  
  
## <a name="related-sections"></a>相關章節  
 [可用性](../../extensibility/internals/command-availability.md)  
 描述 IDE 用來判斷哪些 VSPackage 的命令，以及哪些物件會處理它們的準則。  
  
 [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 提供有關如何建立會使用 UI 的詳細資料[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]命令支援。  
  
 [在 VSPackage 中路由傳送命令](../../extensibility/internals/command-routing-in-vspackages.md)  
 用來讓具有正確的命令要求的物件產生關聯的程序的概觀。

