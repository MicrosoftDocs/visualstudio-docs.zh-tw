---
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d4013cabe43693e52498a3094aee10e4786da43a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460797"
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
此結構會提供在電腦上執行的處理序的相關資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>成員
 `Fields`\
 從旗標的組合[PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)列舉，指出哪些欄位會填入。

 `ProgramNodes`\
 A [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)結構，其中包含程式節點的陣列。

 `fIsDebuggerPresent`\
 非零值 (`TRUE`) 如果[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯工具正在執行，零 (`FALSE`) 如果不是。

## <a name="remarks"></a>備註
 此結構會傳遞至[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)填滿其中的方法。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)