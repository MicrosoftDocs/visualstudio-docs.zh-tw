---
title: CONNECTION_PROTOCOL |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737644"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
指示用於在調試伺服器和調試包 (DE) 之間通信的協定。

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
尚未連接到伺服器。

`CONNECTION_UNKNOWN`\
已建立連接,但它的類型未知。

`CONNECTION_LOCAL`\
連接到本機伺服器。

`CONNECTION_PIPE`\
連接通過命名管道。

`CONNECTION_TCPIP`\
連接使用 TCP/IP。

`CONNECTION_HTTP`\
連接使用 HTTP(透過 Web 伺服器)。

`CONNECTION_OTHER`\
已建立某些其他類型的連接(目前未使用此值)。

## <a name="remarks"></a>備註
這些值從[GetConnection Protocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)方法返回。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
