---
title: 使用互通程式集的命令和功能表 |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709493"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>使用互通程式集的指令和選單
使用網際網路應用程式集來選單和工具列指令的 VSPackage 必須:

- 告知[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 支援的指令以及目前是否啟用這些命令。

- 遵守處理命令的規則(協定)。

- 使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>或介面顯式實現命令處理。

  以下部分介紹如何執行這些任務。

## <a name="in-this-section"></a>本節內容
- [使用互通程式集決定命令狀態](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 描述 VSPackage 如何通知 IDE 它支援哪些命令以及當前是否啟用這些命令。

- [互通程式集中的命令協定](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 提供使用 Interop 程式集實現命令的所有 VS 包使用的基本命令協定的定義。

- [命令執行](../../extensibility/internals/command-implementation.md)

 概述 VSPackage 如何實現命令。

- [註冊內部作業程式集命令處理程式](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 描述通知 IDE VSPackage 提供命令處理程式所需的註冊表項。

## <a name="related-sections"></a>相關章節
- [命令可用性](../../extensibility/internals/command-availability.md)

 描述 IDE 用於確定哪些 VSPackage 命令可用以及哪個物件處理它們的條件。

- [VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 提供有關如何創建使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令支援的 UI 的詳細資訊。

- [VS 套件的指令路由](../../extensibility/internals/command-routing-in-vspackages.md)

 用於將物件與正確的命令請求相關聯的過程的概述。
