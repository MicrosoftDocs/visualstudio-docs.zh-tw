---
title: CONNECTION_PROTOCOL |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ac287462149a20f52a1affdeab7fa6b8333711
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737644"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
表示用來在 debug server 與 debug 封裝之間進行通訊的通訊協定 (DE) 。

## <a name="syntax"></a>語法

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>欄位
`CONNECTION_NONE`\
尚未對伺服器進行連接。

`CONNECTION_UNKNOWN`\
已進行連接，但其類型為未知。

`CONNECTION_LOCAL`\
連接到本機伺服器。

`CONNECTION_PIPE`\
連接是透過具名管道。

`CONNECTION_TCPIP`\
連接使用 TCP/IP。

`CONNECTION_HTTP`\
連接會透過 Web 服務器) 來使用 HTTP (。

`CONNECTION_OTHER`\
已建立其他類型的連接 (此值目前未用) 。

## <a name="remarks"></a>備註
這些值是從 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) 方法傳回。

## <a name="requirements"></a>需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
