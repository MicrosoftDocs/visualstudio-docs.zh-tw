---
description: 判斷自訂屬性是否以名稱存在。
title: IDebugCustomAttributeQuery2：： IsCustomAttributeDefined |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 646fe46f9d83a320423136b8601ee56b3f4ac583
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077586"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
判斷自訂屬性是否以名稱存在。

## <a name="syntax"></a>語法

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>參數
`pszCustomAttributeName`\
在字串，包含要尋找之自訂屬性的名稱。

## <a name="return-value"></a>傳回值
 如果自訂屬性是在此欄位上定義，則會傳回 S_OK，否則會傳回 S_FALSE。

## <a name="remarks"></a>備註
 若要取得與自訂屬性相關聯的屬性位元組，請呼叫 [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
