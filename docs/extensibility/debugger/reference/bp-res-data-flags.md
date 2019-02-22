---
title: BP_RES_DATA_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_RES_DATA_FLAGS
helpviewer_keywords:
- BP_RES_DATA_FLAGS enumeration
ms.assetid: d97611e2-def6-45a9-ad7d-eedf2ad4c82b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b111e98edb1d364a466157a6db4c0089617f18de
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413016"
---
# <a name="bpresdataflags"></a>BP_RES_DATA_FLAGS
指定是否要模擬資料中斷點或實作中的硬體。

## <a name="syntax"></a>語法

```cpp
enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
typedef DWORD BP_RES_DATA_FLAGS;
```

```csharp
public enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
```

## <a name="members"></a>成員
BP_RES_DATA_EMULATED  
指定模擬的資料中斷點。

## <a name="remarks"></a>備註
用於`dwFlags`隸屬[BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)結構。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
[列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
