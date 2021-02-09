---
title: 使用 Interop 元件的命令和功能表 |Microsoft Docs
description: 瞭解使用 Interop 元件在 VSPackage 中執行功能表和工具列命令時必須完成的工作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ea48c77212927c14b4ad49c91ce2f4d988e36f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928220"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>使用 Interop 元件的命令和功能表
使用 Interop 元件來實行功能表和工具列命令的 VSPackage 必須：

- 告知 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 它所支援的命令，以及目前是否已啟用。

- 遵循規則 (合約) 來處理命令。

- 使用或介面明確地執行命令處理 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 。

  下一節將說明如何執行這些工作。

## <a name="in-this-section"></a>本節內容
- [使用 Interop 元件判斷命令狀態](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 描述 VSPackage 如何通知 IDE 它所支援的命令，以及它們目前是否已啟用。

- [Interop 元件中的命令合約](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 提供使用 Interop 元件的所有 Vspackage 執行命令所使用之基本命令合約的定義。

- [命令執行](../../extensibility/internals/command-implementation.md)

 提供 VSPackage 如何實行命令的總覽。

- [註冊 Interop 元件命令處理常式](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 描述通知 IDE VSPackage 提供命令處理常式所需的登錄專案。

## <a name="related-sections"></a>相關章節
- [命令可用性](../../extensibility/internals/command-availability.md)

 描述 IDE 用來判斷哪些 VSPackage 命令可供使用的準則，以及物件處理它們的物件。

- [Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 提供有關如何建立使用命令支援之 UI 的詳細資料 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- [Vspackage 中的命令路由](../../extensibility/internals/command-routing-in-vspackages.md)

 此程式概述用來建立物件與正確命令要求的關聯性。
