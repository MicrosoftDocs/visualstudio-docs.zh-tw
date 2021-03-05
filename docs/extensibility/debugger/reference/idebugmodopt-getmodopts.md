---
description: 抓取選用修飾詞的清單。
title: IDebugModOpt：： GetModOpts |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 971d04662042afed1afe8e1861d0080b513ca74d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149934"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
抓取選用修飾詞的清單。

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
在要傳回的元素數目。

`rgelt`\
擴展傳回包含選項的陣列。

`pceltFetched`\
[in，out]陣列中傳回的元素數目 `rgelt` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
