---
title: IDebugMethodfield:獲取此 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727174"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
獲取`this`包含`Me`方法[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]的物件 的指標。

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
[出]返回表示"此"指標的[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 在面向對象的語言中,通常存在指向類當前實例化的隱含指標。 這在 C#/C++`this``Me`[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]與 中稱為 。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
