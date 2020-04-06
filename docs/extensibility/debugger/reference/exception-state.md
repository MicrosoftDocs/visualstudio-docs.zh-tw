---
title: EXCEPTION_STATE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd2e280cd03ae413e0853950d13fbfefb69bc15f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736951"
---
# <a name="exception_state"></a>EXCEPTION_STATE
指定異常狀態。

## <a name="syntax"></a>語法

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
不要停止在異常。

`EXCEPTION_STOP_FIRST_CHANCE`\
在首先觸發異常時停止。 描述異常事件時,此標誌指示異常事件是第一次異常事件。

`EXCEPTION_STOP_SECOND_CHANCE`\
在異常的第二次觸發時停止。 描述異常事件時,指示異常事件是第二個異常事件。

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
首先觸發使用者模式異常時停止。 描述異常事件時,指示異常事件是第一次用戶異常事件。

`EXCEPTION_STOP_USER_UNCAUGHT`\
未捕獲使用者模式異常時停止。 描述異常事件時,指示異常事件是未捕獲的使用者模式異常事件。

`EXCEPTION_STOP_ALL`\
停止任何異常。 描述異常事件時未使用。

`EXCEPTION_CANNOT_BE_CONTINUED`\
描述異常事件時,指示無法繼續從 中繼續異常。

`EXCEPTION_CODE_SUPPORTED`\
指示異常具有支援它的代碼。 顯示例外

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
指示異常代碼應顯示在十六進制中。 用於顯示異常。

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
指示異常代碼支援 JustMyCode。 用於顯示異常。

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
指示託管代碼調試器應處理異常。 如果未設置,則默認調試器處理異常。 這將傳遞給[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)方法,並且未在[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)結構中使用。

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
過時,請勿使用。

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
過時,請勿使用。

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
過時,請勿使用。

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
過時,請勿使用。

## <a name="remarks"></a>備註
用作EXCEPTION_INFO結構`dwState`的成員,[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)用於指示異常的狀態以及可以對此執行哪些措施。

這些值也會傳遞給[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)方法,以設置所有異常的狀態。

這些標誌可以與位或組合。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
