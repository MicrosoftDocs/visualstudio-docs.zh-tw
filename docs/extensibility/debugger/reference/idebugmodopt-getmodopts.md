---
title: IDebugModOpt::獲取ModOpts |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ab870db3ae3517b60bebd4815e4530f6035b327
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727045"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
檢索可選修改器的清單。

## <a name="syntax"></a>語法

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>參數
`celt`\
[在]要返回的元素數。

`rgelt`\
[出]返回包含選項的陣列。

`pceltFetched`\
[進出]陣列中`rgelt`傳回的元素數。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
