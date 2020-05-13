---
title: SEEK_START |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca1c38027123ca5147a6a7ab1fa6a3f92966409a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713594"
---
# <a name="seek_start"></a>SEEK_START
指定在拆解流中開始查找的位置。

## <a name="syntax"></a>語法

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>欄位
 `SEEK_START_BEGIN`\
 在當前文件的開頭開始查找。

 `SEEK_START_END`\
 在當前文件的末尾開始查找。

 `SEEK_START_CURRENT`\
 開始在當前文件的當前位置查找。

 `SEEK_START_CODECONTEXT`\
 開始在當前文件的給定代碼上下文中尋找。

 `SEEK_START_CODELOCID`\
 開始在給定的代碼位置標識符處查找。 代碼位置識別碼是透過調用[GetCurrentlocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)獲得的。

## <a name="remarks"></a>備註
 作為參數傳遞給[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)方法。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
