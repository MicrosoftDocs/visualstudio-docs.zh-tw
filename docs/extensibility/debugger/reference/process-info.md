---
title: PROCESS_INFO |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef73145fb0a2598dc5e4ee98e8652314e0bc1c89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713876"
---
# <a name="process_info"></a>PROCESS_INFO
包含有關進程的資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>成員
 `Fields`\
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)枚舉中的標誌的組合,用於指定填寫哪些欄位。

 `bstrFileName`\
 進程的完整路徑名稱。 等效於使用`GN_FILENAME`參數調用[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)方法。

 `bstrBaseName`\
 進程的檔名和副檔名。 等效於使用`IDebugProcess2::Getname``GN_BASENAME`參數調用 方法。

 `bstrTitle`\
 進程的標題(如果存在)。 等效於使用`IDebugProcess2::Getname``GN_TITLE`參數調用 方法。

 `ProcessId`\
 標識進程的[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。 等效於調用[Get物理進程 Id](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)方法。

 `dwSessionId`\
 此過程正在運行的調試會話的標識符。

 `bstrAttachedSessionName`\
 附加的會話名稱。 等效於調用[Get 附加會話名稱](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)方法。

 `CreationTime`\
 創建流程的時間。

 `Flags`\
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)枚舉中標記的組合,用於指定進程的屬性。

## <a name="remarks"></a>備註
 此結構傳遞給填寫它的[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)方法。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
