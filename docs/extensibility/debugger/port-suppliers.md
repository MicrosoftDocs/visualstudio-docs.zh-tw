---
title: 連接埠供應商 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf81cfeea10a0687e84982db595a5c7a9aab6074
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998218"
---
# <a name="port-suppliers"></a>連接埠提供者
在偵錯工具架構中，*連接埠提供者*:  
  
- 包含由伺服器，並提供連接埠上對該伺服器的要求。  
  
- 新增和移除，其中包含伺服器的連接埠。  
  
- 可以列舉它已提供給伺服器的所有連接埠。  
  
- 由[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面，透過登錄向 Visual Studio。 這個介面，可由呼叫[GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)。  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供的預設連接埠提供者和預設連接埠。 如果需要實作自訂連接埠，自訂連接埠供應商也必須實作以提供這些自訂的連接埠。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [連接埠](../../extensibility/debugger/ports.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)