---
title: IDebugReference2::SetValueAsString |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca994aaf03103e6d668d78a7d3a683ddbc988eb7
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210089"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
設定參考，以從字串的值。 保留供未來使用。

## <a name="syntax"></a>語法

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   DWORD     dwRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   dwRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>參數
`pszValue`\
[in]做為字串值。

`dwRadix`\
[in]要用於格式化數字的任何資訊基數。

`dwTimeout`\
[in]最大時間 （毫秒），這個方法返回之前等候。 使用`INFINITE`無限期等候。

## <a name="return-value"></a>傳回值
 一律傳回 `E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)