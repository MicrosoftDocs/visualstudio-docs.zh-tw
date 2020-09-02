---
title: 埠 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153692"
---
# <a name="ports"></a>連接埠
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

就偵錯工具架構而言， **埠**：  
  
- 是在伺服器上執行的一組進程的容器。 例如，埠可能代表透過序列纜線或網路非 DCOM 電腦的 Windows CE 型裝置連線。 一個特殊的埠（稱為本機埠）包含在本機電腦上執行的所有處理常式。  
  
- 可以依名稱或識別碼來識別其本身。  
  
- 可以列舉在埠上執行的所有處理常式，並啟動和終止這些進程。  
  
- 是由 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 介面表示，它是藉由將 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 引數傳遞至 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)所建立。  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 提供預設的埠，可處理所有以 Windows 為基礎的處理常式（原生和 managed）。 必須針對不是以 Windows 為基礎的外部裝置連線，執行自訂埠。 若要提供這類自訂埠，也需要執行自訂埠供應商。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [過程](../../extensibility/debugger/processes.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
