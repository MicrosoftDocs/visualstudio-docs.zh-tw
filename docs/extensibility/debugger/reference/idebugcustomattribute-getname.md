---
title: IDebugCustomAttribute::GetName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ed7abc9682d0a9f56c50fe7510ed3f276a6bf5a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315198"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
取得自訂屬性的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>參數
`bstrName`\
[out]傳回字串，包含自訂屬性的名稱。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所傳回的具名會對應至用來宣告屬性的類別名稱。 因為 C# 可讓 [屬性] 後置詞，是要卸除從自訂屬性名稱在宣告中使用時，這並非完全可能對應至自訂屬性類別本身的名稱。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)