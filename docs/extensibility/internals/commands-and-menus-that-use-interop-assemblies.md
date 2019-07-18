---
title: 使用 Interop 組件的命令和功能表 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14625d38a8eae594d1ba63aa1f628c2482be8f30
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342019"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>使用 Interop 組件的命令和功能表
使用 Interop 組件中實作功能表和工具列命令的 VSPackage 必須：

- 通知[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]有關其支援的命令和是否在目前啟用的整合式的開發環境 (IDE)。

- 遵守的規則 （合約） 處理的命令。

- 明確實作命令處理，使用其中一種<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面。

  下一節會說明如何執行這些工作。

## <a name="in-this-section"></a>本節內容
- [使用 Interop 組件判斷命令狀態](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 描述 VSPackage 如何通知 IDE 在它支援哪些命令的相關，而且是否在目前啟用。

- [Interop 組件中的命令合約](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 提供所有的 Vspackage 實作使用 Interop 組件的命令所使用的基本命令合約的定義。

- [命令實作](../../extensibility/internals/command-implementation.md)

 提供 VSPackage 如何實作命令的概觀。

- [註冊 Interop 組件命令處理常式](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 說明通知 IDE VSPackage 提供的命令處理常式所需的登錄項目。

## <a name="related-sections"></a>相關章節
- [命令可用性](../../extensibility/internals/command-availability.md)

 描述 IDE 用來判斷哪些 VSPackage 的命令，以及哪些物件會處理它們的準則。

- [Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 提供有關如何建立會使用 UI 的詳細資料[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令支援。

- [在 Vspackage 中路由傳送命令](../../extensibility/internals/command-routing-in-vspackages.md)

 用來讓具有正確的命令要求的物件產生關聯的程序的概觀。