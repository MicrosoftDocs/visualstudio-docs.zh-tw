---
title: 消息類型 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d0fd12495a59427500c16ef6f37d9f8b6e61f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714491"
---
# <a name="messagetype"></a>MESSAGETYPE
指定消息類型和原因。

## <a name="syntax"></a>語法

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>欄位
 `MT_OUTPUTSTRING`\
 指示應將消息發送到輸出視窗。 這是來自`MT_MESSAGEBOX`的相互排斥。

 `MT_MESSAGEBOX`\
 指示消息應顯示在消息框中。 這是來自`MT_OUTPUTSTRING`的相互排斥。

 `MT_TYPE_MASK`\
 用於隔離消息目標的掩碼值。

 `MT_REASON_EXCEPTION`\
 指示消息框由於異常而顯示。 這是來自`MT_REASON_TRACEPOINT`的相互排斥。

 `MT_REASON_TRACEPOINT`\
 指示由於命中跟蹤點而顯示消息框。 這是相互排斥的`MT_REASON_EXCEPTION`。

 `MT_REASON_MASK`\
 用於隔離顯示消息原因的掩碼值。

## <a name="remarks"></a>備註
 這些值從[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)和[GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)方法返回。

 其中一個原因值可以使用位值`OR`與輸出目標值之一組合。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
