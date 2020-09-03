---
title: 使用 Interop 元件的命令和功能表 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad6b324953914df7103d0dec7371199e3cbbd937
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195045"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>使用 Interop 組件的命令和功能表
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用 interop 元件來實行功能表和工具列命令的 VSPackage 必須：  
  
- 告知 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 整合式開發環境 (IDE) 它所支援的命令，以及目前是否已啟用。  
  
- 遵循規則 (合約) 來處理命令。  
  
- 使用或介面明確地執行命令處理 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 。  
  
  以下說明如何執行這些工作。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 Interop 組件判斷命令狀態](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 描述 VSPackage 如何通知 IDE 它所支援的命令，以及它們目前是否已啟用。  
  
 [Interop 組件中的命令合約](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 提供使用 interop 元件的所有 Vspackage 執行命令所使用之基本命令合約的定義  
  
 [實作](../../extensibility/internals/command-implementation.md)  
 提供 VSPackage 如何實行命令的總覽。  
  
 [註冊 Interop 組件命令處理常式](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 描述通知 IDE VSPackage 提供命令處理常式所需的登錄專案。  
  
## <a name="related-sections"></a>相關章節  
 [可用性](../../extensibility/internals/command-availability.md)  
 描述 IDE 用來判斷哪些 VSPackage 命令可供使用的準則，以及物件處理它們的物件。  
  
 [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 提供有關如何建立使用命令支援之 UI 的詳細資料 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 [在 VSPackage 中路由傳送命令](../../extensibility/internals/command-routing-in-vspackages.md)  
 此程式概述用來建立物件與正確命令要求的關聯性。
