---
title: 執行埠供應商 |Microsoft Docs
description: 瞭解如何執行埠供應商，這在對非 DCOM 電腦或新裝置需要支援時，是必要的。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98cc83ac9640241f0f97dc6e4adaacf8f90599b7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059908"
---
# <a name="implement-a-port-supplier"></a>執行埠供應商
埠供應商會在對會話 debug manager (SDM) 的要求上提供埠。 當您對非 DCOM 電腦或新裝置需要支援時，必須執行埠供應商。 例如，若要提供對行動電話的偵測，您可以設定埠供應商，以提供埠，連接到行動電話 (可能是透過 IR 或資料格連接) 並列舉電話上執行的處理常式和程式。

 若要在以 Windows 為基礎的電腦上進行偵錯工具 (包括遠端偵錯程式) ，Visual Studio 提供原生和 Common Language Runtime (CLR) 程式的埠供應商，因此在這些情況下，不需要設定您自己的通訊埠供應商。

## <a name="in-this-section"></a>本節內容
 [執行並註冊埠供應商](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) 討論 SDM 如何與埠供應商和其埠互動。

 [必要的埠提供者介面](../../extensibility/debugger/required-port-supplier-interfaces.md) 記載您必須實行才能取得埠供應商的介面。

## <a name="related-sections"></a>相關章節
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md) 描述主要的調試架構概念。

## <a name="see-also"></a>另請參閱
 [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
