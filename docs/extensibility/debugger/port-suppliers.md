---
title: "連接埠的供應商 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0cab184b0ecf4c4971b116cc9dfde26d8f80b45f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="port-suppliers"></a>連接埠供應商
偵錯工具就架構而言，**連接埠供應商**:  
  
-   包含由伺服器，並提供要求到該伺服器上的連接埠。  
  
-   新增和移除包含伺服器的連接埠。  
  
-   可以列舉它所提供的伺服器的連接埠。  
  
-   由[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面，透過登錄向 Visual Studio。 您可以取得此介面呼叫[GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供預設連接埠提供者和預設連接埠。 如果需要實作自訂連接埠，自訂連接埠供應商也必須實作以提供自訂連接埠。  
  
## <a name="see-also"></a>請參閱  
 [伺服器](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [連接埠](../../extensibility/debugger/ports.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)