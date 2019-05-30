---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f8333dd697f265480c46ed7edbfbea1a48970ae
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309334"
---
# <a name="processinfo"></a>PROCESS_INFO
包含處理序的相關資訊。

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
 從旗標的組合[PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)指定哪些欄位都已填寫的列舉型別。

 `bstrFileName`\
 程序的完整路徑名稱。 相當於呼叫[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)方法搭配參數`GN_FILENAME`。

 `bstrBaseName`\
 檔案名稱和副檔名的程序。 相當於呼叫`IDebugProcess2::Getname`方法使用參數`GN_BASENAME`。

 `bstrTitle`\
 標題的過程中，如果有的話。 相當於呼叫`IDebugProcess2::Getname`方法使用參數`GN_TITLE`。

 `ProcessId`\
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)識別處理序的結構。 相當於呼叫[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)方法。

 `dwSessionId`\
 偵錯工作階段中執行此程序的識別碼。

 `bstrAttachedSessionName`\
 附加的工作階段名稱。 相當於呼叫[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)方法。

 `CreationTime`\
 建立程序的時間。

 `Flags`\
 從旗標的組合[PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)列舉，指定處理序的屬性。

## <a name="remarks"></a>備註
 此結構會傳遞至[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)填滿其中的方法。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)