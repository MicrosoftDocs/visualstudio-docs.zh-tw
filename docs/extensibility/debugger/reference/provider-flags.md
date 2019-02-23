---
title: PROVIDER_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 803d9569c611e3c4cd70f2c82ecd525716d8ddb3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687493"
---
# <a name="providerflags"></a>PROVIDER_FLAGS
指定要從程式提供者取得所需的屬性。

## <a name="syntax"></a>語法

```cpp
enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
typedef DWORD PROVIDER_FLAGS;
```

```csharp
public enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
```

## <a name="members"></a>成員
 指定 PFLAG_NONE 沒有旗標。

 PFLAG_REMOTE_PORT 呼叫端想要在不同的電腦上的程式清單[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]。

 處理序目前正在偵錯的這個執行個體的 PFLAG_DEBUGGEE [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]。

 PFLAG_ATTACH_TODEBUGGEE[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]附加偵錯程式，但未啟動。

 PFLAG_REASON_WATCH[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]會監看事件。

 PFLAG_GET_PROGRAM_NODES 呼叫端想要`ProgramNodes`欄位[PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)結構。

 PFLAG_GET_IS_DEBUGGER_PRESENT 呼叫端想要`fIsTheDebuggerPresent`欄位`PROVIDER_PROCESS_DATA`結構。

## <a name="remarks"></a>備註
 這些旗標會傳遞下列方法：

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

  這些值可以合併的位元`OR`。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)