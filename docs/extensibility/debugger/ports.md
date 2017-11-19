---
title: "連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 926f5e9a80a91da57d843c11175865f78775e38c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ports"></a>連接埠
偵錯工具就架構而言，**連接埠**:  
  
-   在伺服器上執行的一組處理序的容器。 例如，連接埠可能代表 Windows ce 裝置的序列纜線或網路的非 DCOM 機器的連線。 一個特殊的連接埠，稱為本機連接埠，包含本機電腦上執行的所有處理程序。  
  
-   可以依名稱或識別碼識別本身。  
  
-   可用列舉所有的連接埠上執行的處理程序並啟動和結束這些處理序。  
  
-   由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面，它由傳遞[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)引數[下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供處理所有 windows 處理程序，原生和 managed 的預設連接埠。 自訂連接埠必須與不是以 Windows 為基礎的外部裝置連線的實作。 若要提供這類自訂連接埠，自訂連接埠供應商也必須實作。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [處理程序](../../extensibility/debugger/processes.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)