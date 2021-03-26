---
description: 抓取特定程式的程式節點。
title: IDebugProgramProvider2：： GetProviderProgramNode |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07e7184c189d501b2fcb604590eeb121bae8ccdc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065277"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
抓取特定程式的程式節點。

## <a name="syntax"></a>語法

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>參數
`Flags`\
在 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) 列舉中的旗標組合。 以下是此呼叫的典型旗標：

|旗標|描述|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|呼叫端正在遠端電腦上執行。|
|`PFLAG_DEBUGGEE`|目前正在調試呼叫端 (針對每個節點) 會傳回封送處理的其他相關資訊。|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|呼叫端已附加至，但不是由偵錯工具啟動。|

`pPort`\
在正在執行呼叫進程的埠。

`processId`\
在 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 結構，其中包含有問題之程式的進程識別碼。

`guidEngine`\
在程式附加到 (（如果有任何) ）的 debug engine GUID。

`programId`\
在要取得程式節點的程式識別碼。

`ppProgramNode`\
擴展代表所要求之程式節點的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
