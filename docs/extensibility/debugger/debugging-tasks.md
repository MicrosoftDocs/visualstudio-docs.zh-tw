---
title: 調試作業 |Microsoft Docs
description: 瞭解對程式進行偵錯工具所需的工作，例如將它附加至偵測引擎、產生啟動事件，以及叫用中斷點。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83d351e2b995922d1a8257f7ea9fc0cdad67ab3e
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915566"
---
# <a name="debug-tasks"></a>調試作業
若要對程式進行程式設計，必須將它啟動，而且必須將 debug engine (DE) 必須附加到該程式，否則 DE 必須附加至先前啟動的程式。 附加之後，DE 必須產生特定的啟動事件。 在回應中，debug 封裝會嘗試系結 IDE 中設定的中斷點。 當程式到達系結的中斷點時，它會中止，並等候使用者輸入。

## <a name="in-this-section"></a>本節內容
 [安全性問題](../../extensibility/debugger/security-issues.md) 討論偵錯工具所需的安全性步驟。

 [啟動程式](../../extensibility/debugger/launching-a-program.md) 提供逐步指示，說明如何指定 DE，以呼叫作業系統來啟動程式。

 [直接附加至程式](../../extensibility/debugger/attaching-directly-to-a-program.md) 描述在已執行的進程中用來對程式進行程式設計的進程。

 在[啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)列出將取消附加至程式之後所發生的事件，直到程式進入其主要進入點，並且準備好進行偵錯工具為止。

 [執行的控制](../../extensibility/debugger/control-of-execution.md) 說明刪除通常如何傳送進入點事件、載入完成事件或停止事件（視情況而定）。

 系結[中斷點](../../extensibility/debugger/binding-breakpoints.md)描述當使用者設定中斷點時，IDE 會會構成要求並提示 debug 會話建立中斷點。

 [評估運算式](../../extensibility/debugger/evaluating-expressions.md) 說明如何建立運算式，以及評估運算式時會發生什麼事。

 [視覺化和查看資料](../../extensibility/debugger/visualizing-and-viewing-data.md) 說明運算式評估工具 (EE) 如何支援型別視覺化程式和自訂檢視器。

## <a name="related-sections"></a>相關章節
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md) 描述主要的調試架構概念。

 [偵錯工具元件](../../extensibility/debugger/debugger-components.md) 概述 Visual Studio 的偵錯工具元件，其中包括 DE、EE 和 symbol 處理常式 (SH) 。

 [偵錯工具](../../extensibility/debugger/debugger-contexts.md) 內容說明如何在程式碼、檔和運算式評估內容中同時操作 DE。 描述每個內容的相關位置、位置或評估。

## <a name="see-also"></a>另請參閱
 [開始使用](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
