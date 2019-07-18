---
title: IDebugModOpt::GetModOpts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5ebced053b80af8dce81d41e6614e89e4ffbf3a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324014"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
擷取一份選擇性修飾詞。

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
[in]要傳回的項目數目。

`rgelt`\
[out]傳回陣列，其中包含的選項。

`pceltFetched`\
[in、 out]在傳回的項目數`rgelt`陣列。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)