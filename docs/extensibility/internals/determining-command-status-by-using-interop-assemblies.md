---
title: 使用 Interop 元件判斷命令狀態 |Microsoft Docs
description: 瞭解如何使用 IOleCommandTarget 介面來判斷 VSPackage 中所處理之命令的狀態，以及如何判斷。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5473fffa00723735b022412e7f37f184e043df4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963441"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>使用 interop 元件判斷命令狀態
VSPackage 必須追蹤它可以處理之命令的狀態。 環境無法判斷在 VSPackage 中處理的命令是啟用或停用的時機。 您的 VSPackage 會負責告知環境有關命令狀態的資訊，例如， **剪** 下、 **複製** 和 **貼** 上等一般命令的狀態。

## <a name="status-notification-sources"></a>狀態通知來源
 環境會透過 Vspackage 的方法接收命令的相關資訊 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ，這是 VSPackage 的介面實作為一部分 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。 環境會 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 在兩個條件下呼叫 VSPackage 的方法：

- 當使用者以滑鼠右鍵按一下) 來開啟主功能表或內容功能表 (時，環境會在 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 該功能表上的所有命令上執行方法，以判斷其狀態。

- 當 VSPackage 要求環境更新目前的使用者介面時 (UI) 。 這項更新會以使用者目前可見的命令來進行，例如標準工具列上的 **剪** 下、 **複製** 和 **貼** 上群組，會在回應內容和使用者動作時變成啟用和停用狀態。

  因為 shell 會裝載多個 Vspackage，所以如果需要輪詢每個 VSPackage 來判斷命令狀態，shell 的效能就會降低。 相反地，您的 VSPackage 應該會在變更時主動通知環境。 如需更新通知的詳細資訊，請參閱 [更新使用者介面](../../extensibility/updating-the-user-interface.md)。

## <a name="status-notification-failure"></a>狀態通知失敗
 當您的 VSPackage 無法通知環境的命令狀態變更時，可能會將 UI 置於不一致的狀態。 請記住，使用者可以在工具列上放置任何功能表或內容功能表命令。 因此，只有當功能表或內容功能表開啟時，才會更新 UI。

## <a name="see-also"></a>另請參閱
- [Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [實作](../../extensibility/internals/command-implementation.md)
