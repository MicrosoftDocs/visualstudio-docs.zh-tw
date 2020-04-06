---
title: IDebug程式提供程式2::獲取提供程式處理數據 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e958900307f5f7915f58679709c88f80c2abfc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721835"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
從指定程序檢索正在運行的程式的清單。

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

## <a name="parameters"></a>參數
`Flags`\
[在][PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)枚舉中的標誌的組合。 以下標誌是此呼叫的典型標誌:

|旗標|描述|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|呼叫者在遠端電腦上運行。|
|`PFLAG_DEBUGGEE`|當前正在調試調用方(將為每個節點返回有關編組的其他資訊)。|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|調用方已附加到調試器,但未啟動。|
|`PFLAG_GET_PROGRAM_NODES`|呼叫方要求返回程式節點的清單。|

`pPort`\
[在]調用進程正在運行的埠。

`processId`\
[在]包含包含相關程式的進程 ID 的[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。

`EngineFilter`\
[在]分配給除錯此過程的除錯引擎的 GUID 陣列(這些程式將用於篩選根據提供的引擎支援的內容實際返回的程式;如果未指定引擎,則將返回所有程式)。

`pProcess`\
[出]使用請求的資訊填充[PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)結構。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此過程通常調用此方法以獲取該進程中運行的程式的清單。 返回的資訊是[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件的清單。

## <a name="see-also"></a>另請參閱
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
