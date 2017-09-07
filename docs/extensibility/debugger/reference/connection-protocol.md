---
title: "CONNECTION_PROTOCOL |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2be5678704e9a5899c4ce7f5caba8cec1d8a21e6
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# CONNECTION_PROTOCOL
指出用來偵錯伺服器和偵錯封裝 (DE) 之間進行通訊的通訊協定。  
  
## 語法  
  
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
  
#### 參數  
 CONNECTION_NONE  
 沒有已連接到伺服器。  
  
 CONNECTION_UNKNOWN  
 已建立連線，但它是未知的型別。  
  
 CONNECTION_LOCAL  
 連接是在本機伺服器。  
  
 CONNECTION_PIPE  
 連接是透過具名管道。  
  
 CONNECTION_TCPIP  
 連接會使用 TCP/IP。  
  
 CONNECTION_HTTP  
 連線使用 HTTP （透過 Web 伺服器）。  
  
 CONNECTION_OTHER  
 已建立其他類型的連線 （這個值目前未使用）。  
  
## 備註  
 這些值會傳回從[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)方法。  
  
## 需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
