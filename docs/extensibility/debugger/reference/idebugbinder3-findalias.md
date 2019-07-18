---
title: IDebugBinder3::FindAlias |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8387a3302395d6e25c2b00dd360286e533531168
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344428"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
這個方法會找出的指定名稱的別名。 在程式中，這將會搜尋所有的別名。

## <a name="syntax"></a>語法

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>參數
`pcstrName`\
[in]若要尋找別名名稱。

`ppAlias`\
[out]所表示的別名 （如果有的話） 找到[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`（如果找不到別名） 或錯誤碼。

## <a name="remarks"></a>備註
 這個方法會初始化為 null，然後再呼叫; 的目的地物件然後它會測試之後，來判斷已找到別名為 null 值。

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)