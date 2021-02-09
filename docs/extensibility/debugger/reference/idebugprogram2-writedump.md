---
title: IDebugProgram2：： WriteDump |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 265c77acdb15069c1fcd7f33d93d4ff74a528eca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896145"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
將傾印寫入檔案。

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
在 [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) 列舉中的值，指定傾印的類型，例如簡短或 long。

`pszDumpUrl`\
在要將傾印寫入其中的 URL。 一般而言，這是的格式 `file://c:\path\filename.ext` ，但可能是任何有效的 URL。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 程式傾印通常會包含目前的堆疊框架、堆疊本身、在程式中執行的執行緒清單，以及程式所擁有的任何記憶體。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
