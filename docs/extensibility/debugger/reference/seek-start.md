---
title: SEEK_START | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 341b321b529bc1359ba576cc26ec20cc99e96cb3
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458402"
---
# <a name="seekstart"></a>SEEK_START
指定要啟動的反組譯碼資料流中搜尋的位置。

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
 搜尋目前文件的開頭開始。

 `SEEK_START_END`\
 啟動搜尋目前文件的結尾。

 `SEEK_START_CURRENT`\
 啟動搜尋目前文件目前的位置。

 `SEEK_START_CODECONTEXT`\
 開始搜尋在目前文件指定的程式碼內容。

 `SEEK_START_CODELOCID`\
 開始搜尋在指定的程式碼位置識別碼。 透過呼叫所取得的程式碼位置識別項[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)。

## <a name="remarks"></a>備註
 作為引數[搜尋](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)方法。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)