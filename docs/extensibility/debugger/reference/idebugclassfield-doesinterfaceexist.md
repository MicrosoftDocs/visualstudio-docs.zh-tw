---
title: IDebugClassField::DoesInterfaceExist |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57bf8d0af54773b03fd23994b83fe6d2fac1306c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337235"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
決定是否特定介面會定義在類別中。

## <a name="syntax"></a>語法

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

## <a name="parameters"></a>參數
`pszInterfaceName`\
[in]字串，包含要尋找的介面名稱。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，則傳回 S_FALSE 如果介面不存在;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法實際上取得列舉型別之所有介面，並搜尋相符的介面清單。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)