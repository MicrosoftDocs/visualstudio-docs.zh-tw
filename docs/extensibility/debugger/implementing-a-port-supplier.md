---
title: 實施埠供應商 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8218e372ad3aece922811bc20cfd7650f33296f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738550"
---
# <a name="implement-a-port-supplier"></a>實施埠供應商
埠供應商應要求向工作階段調試管理器 (SDM) 提供連接埠。 除錯到非 DCOM 電腦或新設備需要支援時,必須實現埠供應商。 例如,要向手機提供調試,可以設置一個埠供應商,該埠提供埠,這些埠連接到手機(可能通過 IR 或手機連接),並枚舉在電話上運行的進程和程式。

 對於基於 Windows 的電腦上的調試程式(包括遠端調試),Visual Studio 為本機和通用語言運行時 (CLR) 進程提供埠供應商,因此在這些情況下無需設置您自己的埠供應商。

## <a name="in-this-section"></a>本節內容
 [實施和註冊埠供應商](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)討論 SDM 如何與埠供應商及其埠進行互動。

 [所需的連接埠供應商介面](../../extensibility/debugger/required-port-supplier-interfaces.md)記錄獲取埠供應商時必須實現的介面。

## <a name="related-sections"></a>相關章節
 [除錯器概念](../../extensibility/debugger/debugger-concepts.md)描述主要的調試體系結構概念。

## <a name="see-also"></a>另請參閱
 [視覺化工作室除錯器可擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
