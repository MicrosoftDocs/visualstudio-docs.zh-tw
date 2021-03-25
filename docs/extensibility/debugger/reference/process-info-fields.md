---
description: 指定要為進程取出的資訊種類。
title: PROCESS_INFO_FIELDS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1f779352ce6b1217cd8af1e87988cb165b2dddc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079627"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
指定要為進程取出的資訊種類。

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>欄位
 `PIF_FILE_NAME`\
 初始化/使用 `bstrFileName` [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 結構的欄位。

 `PIF_BASE_NAME`\
 初始化/使用 `bstrBaseName` 結構的欄位 `PROCESS_INFO` 。

 `PIF_TITLE`\
 初始化/使用 `bstrTitle` 結構的欄位 `PROCESS_INFO` 。

 `PIF_PROCESS_ID`\
 初始化/使用 `ProcessId` 結構的欄位 `PROCESS_INFO` 。

 `PIF_SESSION_ID`\
 初始化/使用 `dwSessionId` 結構的欄位 `PROCESS_INFO` 。

 `PIF_ATTACHED_SESSION_NAME`\
 初始化/使用 `bstrAttachedSessionName` 結構的欄位 `PROCESS_INFO` 。

 `PIF_CREATION_TIME`\
 初始化/使用 `CreationTime` 結構的欄位 `PROCESS_INFO` 。

 `PIF_FLAGS`\
 初始化/使用 `Flags` 結構的欄位 `PROCESS_INFO` 。

 `PIF_ALL`\
 填滿所有欄位。

## <a name="remarks"></a>備註
 傳遞至 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) 方法，以指出要初始化 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 結構的哪些欄位。

 也可用於 `Fields` 結構的欄位 `PROCESS_INFO` ，以指出哪些欄位已使用且有效。

 這些旗標可以與位結合 `OR` 。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
