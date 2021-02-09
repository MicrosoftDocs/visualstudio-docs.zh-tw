---
title: IDebugProgramProvider2：： GetProviderProcessData |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ce5bee4f2401e3895570f16a6de5567b5979d98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898290"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
從指定的進程抓取正在執行的程式清單。

## <a name="syntax"></a>語法

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
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
|`PFLAG_GET_PROGRAM_NODES`|呼叫端要求要傳回的程式節點清單。|

`pPort`\
在正在執行呼叫進程的埠。

`processId`\
在 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 結構，其中包含有問題之程式的進程識別碼。

`EngineFilter`\
在指派給 debug 此進程的 debug engine 的 Guid 陣列 (這些會用來根據提供的引擎所支援的專案篩選實際傳回的程式;如果未指定引擎，則會傳回) 的所有程式。

`pProcess`\
擴展填入所要求資訊的 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 結構。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法通常會由進程呼叫，以取得在該進程中執行的程式清單。 傳回的資訊是 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 物件的清單。

## <a name="see-also"></a>另請參閱
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
