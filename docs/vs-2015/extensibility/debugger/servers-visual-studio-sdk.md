---
title: 伺服器 (Visual Studio SDK) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ed2ce924b22827a82a67664e3e473f0930a87e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199403"
---
# <a name="servers-visual-studio-sdk"></a>伺服器 (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

就偵錯工具架構而言， **伺服器**：  
  
- 是埠和埠供應商的容器，可用來將埠和埠供應商傳達給會話 debug manager (SDM) 和偵錯工具引擎。  
  
- 可以依名稱識別其本身，並列舉其埠和埠供應商。  
  
- 是以 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) 介面表示，它只會由 Visual Studio 針對執行) 之 Visual Studio 的每個實例 (一個伺服器實例。  
  
## <a name="see-also"></a>另請參閱  
 [港口](../../extensibility/debugger/ports.md)   
 [埠供應商](../../extensibility/debugger/port-suppliers.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
