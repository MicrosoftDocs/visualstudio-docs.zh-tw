---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 405d11b0c685017d59251ba83126a73fe1a96db2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708962"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
指定如何解譯中的處理序識別碼[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。

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

## <a name="members"></a>成員
系統識別項為 AD_PROCESS_ID_SYSTEM 處理序 ID。 使用`ProcessId.dwProcessId`欄位[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。

AD_PROCESS_ID_GUID 處理序識別碼是 GUID。 使用`ProcessId.guidProcessId`欄位`AD_PROCESS_ID`結構。

## <a name="remarks"></a>備註
用於`ProcessIdType`隸屬[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構，以識別包含在結構中的處理序識別碼的類型。 決定如何解譯`ProcessId`聯集結構中。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
