---
title: IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 385ef2aaaadc8d1f66eaf245f06dbfd299638fa5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916714"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
擷取從指定的處理序中執行程式的清單。

## <a name="syntax"></a>語法

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
);
```

#### <a name="parameters"></a>參數
 `Flags`

 [in]從旗標的組合[PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)列舉型別。 此呼叫一般會在下列旗標：

|旗標|描述|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|呼叫端在遠端電腦上執行。|
|`PFLAG_DEBUGGEE`|呼叫端目前正在偵錯 （每個節點會傳回封送處理的其他資訊）。|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|已附加至呼叫端，但不是啟動偵錯工具。|
|`PFLAG_GET_PROGRAM_NODES`|呼叫端要求輸入程式節點的清單傳回。|

 `pPort`

 [in]呼叫處理序的連接埠上執行。

 `processId`

 [in][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構包含該程式處理序的識別碼有問題。

 `EngineFilter`

 [in]指派給此程序 （這些會用來篩選實際上還會傳回根據提供的引擎的支援; 如果未不指定任何引擎，則會傳回所有程式的程式） 進行偵錯的偵錯引擎 Guid 的陣列。

 `pProcess`

 [out]A [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)結構，其中會填入所要求的資訊。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 若要取得一份在該程序中執行程式處理程序正常呼叫這個方法。 傳回的資訊是一份[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件。

## <a name="see-also"></a>另請參閱
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)