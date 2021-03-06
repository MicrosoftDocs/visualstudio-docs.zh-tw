---
description: 此結構提供在電腦上執行之處理常式的相關資訊。
title: PROVIDER_PROCESS_DATA |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f49ef1c2990fe578738356cbe5db19cbc1c159ab
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221974"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
此結構提供在電腦上執行之處理常式的相關資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>成員
 `Fields`\
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)列舉中的旗標組合，表示填入的欄位。

 `ProgramNodes`\
 包含程式節點陣列的 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) 結構。

 `fIsDebuggerPresent`\
 非零 (`TRUE`) 如果 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 偵錯工具正在執行，則零 (`FALSE`) 。

## <a name="remarks"></a>備註
 此結構會傳遞至其填入的 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) 方法。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
