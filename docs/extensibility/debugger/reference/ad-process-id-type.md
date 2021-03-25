---
description: 指定如何解讀 AD_PROCESS_ID 結構中的處理序識別碼。
title: AD_PROCESS_ID_TYPE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ae50fc827debd540faa99c33e10ddd217fc691f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094558"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
指定如何解讀 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 結構中的處理序識別碼。

## <a name="syntax"></a>Syntax

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

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
