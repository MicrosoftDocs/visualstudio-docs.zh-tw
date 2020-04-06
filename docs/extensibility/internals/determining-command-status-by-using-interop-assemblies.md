---
title: 使用互操作程式集確定命令狀態 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52bea32997b083cd13349a37201411e357f94a90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708705"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>使用互通程式集決定命令狀態
VSPackage 必須追蹤它可以處理的命令的狀態。 環境無法確定在 VSPackage 中處理的命令何時啟用或禁用。 VSPackage 負責通知環境命令狀態,例如,一般命令的狀態,如**剪切**、**複製**和**貼上**。

## <a name="status-notification-sources"></a>狀態通知來源
 環境通過 VSPackage<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法接收有關命令的資訊,這是 VSPackage 實現<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面的一部分。 環境在<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>以下兩種情況下調用 VSPackage 的方法:

- 當使用者打開主菜單或上下文菜單(通過右鍵單擊)時,環境將執行該功能表上所有命令<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>上的方法以確定其狀態。

- 當 VS 包請求環境更新當前使用者介面 (UI) 時。 此更新作為當前對用戶可見的命令(如標準工具列上的**剪切**、**複製**和**貼上**群組)而啟用和禁用,以回應上下文和使用者操作。

  由於 shell 承載多個 VSPackage,因此,如果需要輪詢每個 VSPackage 以確定命令狀態,則 shell 的性能將不可接受。 相反,當更改時,VSPackage 應主動通知環境。當其 UI 發生更改時。 有關更新通知的詳細資訊,請參閱[更新使用者介面](../../extensibility/updating-the-user-interface.md)。

## <a name="status-notification-failure"></a>狀態通知失敗
 VSPackage 未能通知環境命令狀態更改可能會使 UI 處於不一致狀態。 請記住,用戶可以將任何功能表或上下文功能單命令放在工具列上。 因此,僅在打開功能表或上下文菜單時更新 UI 是不夠的。

## <a name="see-also"></a>另請參閱
- [VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [實作](../../extensibility/internals/command-implementation.md)
