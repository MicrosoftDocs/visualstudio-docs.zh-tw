---
description: 指定例外狀況狀態。
title: EXCEPTION_STATE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 297c5de3afd2b5f81444dd29278fc294cd71aa6a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059440"
---
# <a name="exception_state"></a>EXCEPTION_STATE
指定例外狀況狀態。

## <a name="syntax"></a>Syntax

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>欄位
`EXCEPTION_NONE`\
請勿在例外狀況時停止。

`EXCEPTION_STOP_FIRST_CHANCE`\
在第一次引發例外狀況時停止。 描述例外狀況事件時，此旗標表示例外狀況事件是第一個可能發生的例外狀況事件。

`EXCEPTION_STOP_SECOND_CHANCE`\
在第二次引發例外狀況時停止。 描述例外狀況事件時，表示例外狀況事件是第二個例外狀況事件。

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
在第一次引發使用者模式例外狀況時停止。 描述例外狀況事件時，表示例外狀況事件是第一個可能發生的使用者例外狀況事件。

`EXCEPTION_STOP_USER_UNCAUGHT`\
當未攔截到使用者模式例外狀況時停止。 描述例外狀況事件時，表示例外狀況事件是未攔截的使用者模式例外狀況事件。

`EXCEPTION_STOP_ALL`\
在任何例外狀況時停止。 描述例外狀況事件時未使用。

`EXCEPTION_CANNOT_BE_CONTINUED`\
描述例外狀況事件時，表示例外狀況無法繼續。

`EXCEPTION_CODE_SUPPORTED`\
指出例外狀況具有支援的程式碼。 用於顯示例外狀況

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
指出例外狀況程式碼應以十六進位顯示。 用來顯示例外狀況。

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
指出例外狀況程式碼支援 JustMyCode。 用來顯示例外狀況。

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
指出 managed 程式碼偵錯工具應該處理例外狀況。 如果未設定，則預設偵錯工具會處理例外狀況。 這會傳遞至 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) 方法，而不會用於 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 結構中。

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
已淘汰，請勿使用。

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
已淘汰，請勿使用。

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
已淘汰，請勿使用。

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
已淘汰，請勿使用。

## <a name="remarks"></a>備註
當做 `dwState` [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 結構的成員，用來表示例外狀況的狀態以及可以完成的工作。

這些值也會傳遞至 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) 方法，以設定所有例外狀況的狀態。

這些旗標可以結合位 OR。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
