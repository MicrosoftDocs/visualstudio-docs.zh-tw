---
title: "命令和功能表，使用 Interop 組件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8d89b698a97d1793b3c5255966d9eca35ec1b78f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>命令和使用 Interop 組件的功能表
使用 interop 組件中實作功能表和工具列命令的 VSPackage 必須：  
  
-   通知[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]它所支援的命令及是否在目前啟用的整合式的開發環境 (IDE)。  
  
-   遵守的規則 （合約） 處理的命令。  
  
-   明確實作使用的命令處理<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面。  
  
 以下描述如何執行這些工作。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 Interop 組件判斷命令狀態](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 描述 VSPackage 如何通知 IDE，它支援哪些命令的相關，以及是否在目前啟用。  
  
 [Interop 組件中的命令合約](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 提供所有的 Vspackage 實作使用 interop 組件的命令所使用的基本命令合約的定義  
  
 [實作](../../extensibility/internals/command-implementation.md)  
 提供 VSPackage 如何實作命令的概觀。  
  
 [註冊 Interop 組件命令處理常式](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 描述通知 IDE VSPackage 提供的命令處理常式所需的登錄項目。  
  
## <a name="related-sections"></a>相關章節  
 [可用性](../../extensibility/internals/command-availability.md)  
 描述 IDE 用來判斷可用的 VSPackage 的命令，以及哪些物件會處理它們的準則。  
  
 [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 提供有關如何建立使用的 UI 詳細資料[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令支援。  
  
 [在 VSPackage 中路由傳送命令](../../extensibility/internals/command-routing-in-vspackages.md)  
 用來與具有正確的命令要求的物件相關聯處理序的概觀。