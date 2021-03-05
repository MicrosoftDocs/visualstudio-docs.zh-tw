---
description: 用來判斷程式是否可以在到達執行的特定點之後停止執行。
title: CANSTOP_REASON |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: def5bdbb6433f6a154eb6f84a88fb39004bc41ae
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170994"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
用來判斷程式是否可以在到達執行的特定點之後停止執行。

## <a name="syntax"></a>Syntax

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>欄位
`CANSTOP_ENTRYPOINT`\
指定指定程式的進入點。

`CANSTOP_STEPIN`\
指定逐步執行至函式。

## <a name="remarks"></a>備註
以引數的形式傳遞至 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) 方法，以確認會話 Debug MANAGER (SDM) 是否可以在到達程式的進入點之後，或逐步執行至函式或方法之後停止運作。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
