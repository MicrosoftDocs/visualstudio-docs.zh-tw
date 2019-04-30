---
title: IDebugBinder3::FindAlias |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58675b5f9e963ec416a2c8586375a94f9c06ae69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877519"
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

#### <a name="parameters"></a>參數
 `pcstrName`

 [in]若要尋找別名名稱。

 `ppAlias`

 [out]所表示的別名 （如果有的話） 找到[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`（如果找不到別名） 或錯誤碼。

## <a name="remarks"></a>備註
 這個方法會初始化為 null，然後再呼叫; 的目的地物件然後它會測試之後，來判斷已找到別名為 null 值。

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)