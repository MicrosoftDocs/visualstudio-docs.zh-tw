---
title: CONNECTION_PROTOCOL |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d70aa31e7574e9fcdb0ed4e8d89847e832f3739b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832759"
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
表示用來偵錯伺服器和偵錯封裝 (DE) 之間進行通訊的通訊協定。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```csharp  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
};  
```  
  
#### <a name="parameters"></a>參數  
 CONNECTION_NONE  
 沒有已連接到伺服器。  
  
 CONNECTION_UNKNOWN  
 已建立的連接，但它是未知的類型。  
  
 CONNECTION_LOCAL  
 連接是在本機伺服器。  
  
 CONNECTION_PIPE  
 連線是透過具名管道。  
  
 CONNECTION_TCPIP  
 連線使用 TCP/IP。  
  
 CONNECTION_HTTP  
 連線使用 HTTP （透過 Web 伺服器）。  
  
 CONNECTION_OTHER  
 已建立其他類型的連接 （這個值目前未使用）。  
  
## <a name="remarks"></a>備註  
 會傳回這些值從[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)