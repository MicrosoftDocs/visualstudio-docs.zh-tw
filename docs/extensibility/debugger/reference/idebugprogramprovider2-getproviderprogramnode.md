---
title: IDebug程式提供程式2::獲取提供程式程序節點 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd8ca7d5120ba20695caef2e9021ee25869df72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721801"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
檢索特定程式的程序節點。

## <a name="syntax"></a>語法

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
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

`pPort`\
[在]調用進程正在運行的埠。

`processId`\
[在]包含包含相關程式的進程 ID 的[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。

`guidEngine`\
[在]程式附加到的調試引擎的 GUID(如果有)。

`programId`\
[在]要為其獲取程式節點的程序的 ID。

`ppProgramNode`\
[出]表示請求的程式節點的[IDebug ProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
