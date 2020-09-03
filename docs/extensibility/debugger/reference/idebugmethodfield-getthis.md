---
title: IDebugMethodField：： GetThis |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29252d1586d039084ec1d21f1fc4967aea68baf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727174"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
取得 `this` `Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 包含方法之物件) 指標中的 (。

## <a name="syntax"></a>語法

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>參數
`ppClass`\
擴展傳回代表 "this" 指標的 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 在物件導向的語言中，通常會有隱含指標指向類別的目前具現化。 這 `this` 在 c #/c + + 中也稱為，如同 `Me` 中一樣 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
