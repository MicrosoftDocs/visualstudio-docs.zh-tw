---
description: 描述 (DLL、EXE 或元件) 的特定模組。
title: MODULE_INFO |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d3fd390ca5491aa9dd3e97a0d820c8e02fd0147
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222350"
---
# <a name="module_info"></a>MODULE_INFO
描述 (DLL、EXE 或元件) 的特定模組。

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
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)列舉中的旗標組合，可指定要填寫的欄位。

 `m_bstrName`\
 模組名稱。

 `m_bstrUrl`\
 模組 URL。

 `m_bstrVersion`\
 模組版本。

 `m_bstrDebugMessage`\
 關於此模組的選擇性訊息，例如「無法載入符號」。

 `m_addrLoadAddress`\
 模組載入位址。

 `m_addrPreferredLoadAddress`\
 模組慣用的載入位址。

 `m_dwSize`\
 模組大小。

 `m_dwLoadOrder`\
 模組載入順序。

 `m_TimeStamp`\
 上次修改符號檔的時間。

 `m_bstrUrlSymbolLocation`\
 符號檔的位置 (例如 ". \\ "模組中指定的 ) 。 作為尋找模組符號的起始位置。

 `m_dwModuleFlags`\
 描述模組的 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) 列舉中的旗標組合。

## <a name="remarks"></a>備註
 此結構會傳遞至其填入的 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) 方法。

 此結構會對應至 [ **模組** ] 視窗中所列的每個模組。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
