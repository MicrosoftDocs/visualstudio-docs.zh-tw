---
title: AD_PROCESS_ID_TYPE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a88fbe97cede8d343f1a96bc1917a69b8905b02b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738196"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
指定如何在[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構中解釋進程 ID。

## <a name="syntax"></a>語法

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>欄位
`AD_PROCESS_ID_SYSTEM`\
進程識別碼是系統識別碼。 使用AD_PROCESS_ID`ProcessId.dwProcessId`結構的欄位[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)。

`AD_PROCESS_ID_GUID`\
進程識別碼是GUID。 `ProcessId.guidProcessId`使用結構欄位`AD_PROCESS_ID`。

## <a name="remarks"></a>備註
用於AD_PROCESS_ID結構`ProcessIdType`的成員,用於[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)標識結構中包含的進程 ID 的類型。 確定如何解釋結構中的`ProcessId`聯合。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
