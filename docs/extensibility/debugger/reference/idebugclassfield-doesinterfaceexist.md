---
title: IDebugClassField::DoesInterfaceExist |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7884bff62321ed07c3a11a6db65855b1edea0adc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688403"
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

#### <a name="parameters"></a>參數
 `pszInterfaceName`

 [in]字串，包含要尋找的介面名稱。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，則傳回 S_FALSE 如果介面不存在;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法實際上取得列舉型別之所有介面，並搜尋相符的介面清單。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)