---
title: 實作連接埠提供者 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d6875baf72d94494a1abaea9260e344b236f83c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925581"
---
# <a name="implement-a-port-supplier"></a>實作連接埠提供者
連接埠提供者會提供工作階段的偵錯管理員 (SDM) 的要求上的連接埠。 對非 DCOM 機器或新的裝置時需要支援偵錯時，就必須實作連接埠提供者。 比方說，若要提供對手機偵錯，您可能會設定連接埠提供者，提供連接埠，連接到行動電話 （也許是透過 IR 或儲存格連接），並列舉的處理程序和手機上執行的程式。

 對於以 Windows 為基礎的電腦 （包括遠端偵錯） 上的偵錯程式，Visual Studio 會提供原生和 Common Language Runtime (CLR) 處理程序的連接埠提供者，因此不需要設定您自己的連接埠提供者，在這些情況下。

## <a name="in-this-section"></a>本節內容
 [實作並註冊連接埠提供者](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)討論 SDM 與連接埠提供者和它的連接埠的互動方式。

 [所需的連接埠供應商介面](../../extensibility/debugger/required-port-supplier-interfaces.md)文件以取得連接埠提供者，您必須實作的介面。

## <a name="related-sections"></a>相關章節
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)描述主要的偵錯架構概念。

## <a name="see-also"></a>另請參閱
 [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)