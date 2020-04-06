---
title: IDebugProgram2::寫入轉儲 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722732"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
將轉儲寫入檔。

## <a name="syntax"></a>語法

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>參數
`DumpType`\
[在][DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md)枚舉中指定轉儲類型的值,例如,短轉儲或長轉儲類型。

`pszDumpUrl`\
[在]要將轉印寫入的 URL。 通常,這是以`file://c:\path\filename.ext`的形式 ,但可以是任何有效的 URL。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 程式轉儲通常包括當前堆疊幀、堆疊本身、程式中正在運行的線程的清單,以及程式擁有的任何記憶體。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
