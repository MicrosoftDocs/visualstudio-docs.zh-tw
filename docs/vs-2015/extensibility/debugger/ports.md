---
title: Ports | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939621"
---
# <a name="ports"></a>連接埠
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

偵錯工具就架構而言，**連接埠**:  
  
- 在伺服器上執行的一組處理序的容器。 例如，連接埠可能代表 Windows CE 架構裝置的序列纜線或網路上的非 DCOM 機器的連線。 一個特殊的連接埠，稱為本機連接埠，包含本機電腦上執行的所有處理程序。  
  
- 可以依名稱或識別碼識別本身。  
  
- 可以列舉所有連接埠上執行的處理序啟動和結束這些處理序。  
  
- 由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面，它由傳遞[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)引數[下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)。  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 提供處理所有以 Windows 為基礎的處理序原生和受管理的預設連接埠。 連線必須實作自訂連接埠不是以 Windows 為基礎的外部裝置。 若要提供這類自訂連接埠，自訂連接埠供應商也必須實作。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [處理程序](../../extensibility/debugger/processes.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
