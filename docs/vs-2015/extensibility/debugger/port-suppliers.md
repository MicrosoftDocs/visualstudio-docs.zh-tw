---
title: 埠供應商 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153712"
---
# <a name="port-suppliers"></a>連接埠提供者
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

就偵錯工具架構而言， **埠供應商**：  
  
- 包含在伺服器上，並提供對該伺服器之要求的埠。  
  
- 可以從包含的伺服器加入和移除埠。  
  
- 可以列舉所有提供給伺服器的埠。  
  
- 是以 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 介面表示，此介面透過登錄向 Visual Studio 註冊。 您可以藉由呼叫 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)來取得這個介面。  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 提供預設埠供應商和預設通訊埠。 如果需要執行自訂埠，也需要執行自訂埠供應商來提供這些自訂埠。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [港口](../../extensibility/debugger/ports.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
