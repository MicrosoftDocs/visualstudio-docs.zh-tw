---
title: 連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f54ec931bc34f854d1c9f1a85961f5af65a56264
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936338"
---
# <a name="ports"></a>連接埠
在偵錯工具架構中，*連接埠*:  
  
- 在伺服器上執行的一組處理序的容器。 例如，連接埠可能代表 Windows CE 架構裝置的序列纜線或網路上的非 DCOM 機器的連線。 一個特殊的連接埠，稱為本機連接埠，包含本機電腦上執行的所有處理程序。  
  
- 可以依名稱或識別碼識別本身。  
  
- 可以列舉所有連接埠上執行的處理序啟動和結束這些處理序。  
  
- 由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面，它由傳遞[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)引數[下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)。  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供處理所有以 Windows 為基礎的處理序原生和受管理的預設連接埠。 自訂連接埠必須設定連線不是以 Windows 為基礎的外部裝置。 若要提供這類自訂連接埠，您必須也設定自訂連接埠供應商。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [處理程序](../../extensibility/debugger/processes.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)