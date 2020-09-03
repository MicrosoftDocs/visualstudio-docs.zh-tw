---
title: AD_PROCESS_ID_TYPE |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738196"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
指定如何解讀 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 結構中的處理序識別碼。

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
處理序識別碼是系統識別碼。 使用 `ProcessId.dwProcessId` [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 結構的欄位。

`AD_PROCESS_ID_GUID`\
處理序識別碼是 GUID。 使用 `ProcessId.guidProcessId` 結構的欄位 `AD_PROCESS_ID` 。

## <a name="remarks"></a>備註
用於 `ProcessIdType` [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 結構的成員，以識別包含在結構中的處理序識別碼類型。 決定如何解讀 `ProcessId` 結構中的聯集。

## <a name="requirements"></a>需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
