---
title: 實作連接埠供應商 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0743f307dc579f6197880b0b89acaf2db0dda08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-a-port-supplier"></a>實作連接埠供應商
連接埠供應商提供要求的工作階段的偵錯管理員 (SDM) 上的連接埠。 連接埠提供者必須實作非 DCOM 機器進行偵錯時，或當新裝置需要支援。 比方說，若要提供行動電話偵錯，您可能會實作一個提供連接埠，行動電話 （或許是藉由連線到 IR 或儲存格連線），並列舉的程序和程式的手機上執行的連接埠供應商。  
  
 （包括遠端偵錯） 的 windows 電腦上的偵錯程式，Visual Studio 可提供原生和 Common Language Runtime (CLR) 處理程序的連接埠供應商，所以不需要在這些情況下實作您自己的連接埠供應商。  
  
## <a name="in-this-section"></a>本節內容  
 [實作和註冊連接埠提供者](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 討論如何 SDM 互動與連接埠供應商和它的連接埠。  
  
 [必要的連接埠提供者介面](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 文件以取得連接埠提供者必須實作的介面。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯工具的擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)