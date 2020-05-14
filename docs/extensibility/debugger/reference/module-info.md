---
title: MODULE_INFO |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59ab4d0bb2a7aaa4b08f616ea0a99be85b521bb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714306"
---
# <a name="module_info"></a>MODULE_INFO
描述特定模組(DLL、EXE 或程式集)。

## <a name="syntax"></a>語法

```cpp
typedef struct tagMODULE_INFO { 
   MODULE_INFO_FIELDS dwValidFields;
   BSTR               m_bstrName;
   BSTR               m_bstrUrl;
   BSTR               m_bstrVersion;
   BSTR               m_bstrDebugMessage;
   UINT64             m_addrLoadAddress;
   UINT64             m_addrPreferredLoadAddress;
   DWORD              m_dwSize;
   DWORD              m_dwLoadOrder;
   FILETIME           m_TimeStamp;
   BSTR               m_bstrUrlSymbolLocation;
   MODULE_FLAGS       m_dwModuleFlags;
} MODULE_INFO;
```

```csharp
public struct MODULE_INFO { 
   public uint     dwValidFields;
   public string   m_bstrName;
   public string   m_bstrUrl;
   public string   m_bstrVersion;
   public string   m_bstrDebugMessage;
   public ulong    m_addrLoadAddress;
   public ulong    m_addrPreferredLoadAddress;
   public uint     m_dwSize;
   public uint     m_dwLoadOrder;
   public FILETIME m_TimeStamp;
   public string   m_bstrUrlSymbolLocation;
   public uint     m_dwModuleFlags;
};
```

## <a name="members"></a>成員
 `dwValidFields`\
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)枚舉中的標誌的組合,用於指定填寫哪些欄位。

 `m_bstrName`\
 模組名稱。

 `m_bstrUrl`\
 模組 URL。

 `m_bstrVersion`\
 模組版本。

 `m_bstrDebugMessage`\
 有關模組的可選消息,例如,"無法載入符號"。

 `m_addrLoadAddress`\
 模組載入位址。

 `m_addrPreferredLoadAddress`\
 模組的首選負載位址。

 `m_dwSize`\
 模組大小。

 `m_dwLoadOrder`\
 模組載入順序。

 `m_TimeStamp`\
 上次修改符號文件的時間。

 `m_bstrUrlSymbolLocation`\
 符號檔的位置(例如,".")\\在模組中指定。 用作查找模組符號的起始位置。

 `m_dwModuleFlags`\
 描述模組[MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)枚舉的標誌的組合。

## <a name="remarks"></a>備註
 此結構傳遞給填寫它的[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)方法。

 此結構對應於 **「模組」** 視窗中列出的每個模組。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
