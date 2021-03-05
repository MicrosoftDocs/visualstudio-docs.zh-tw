---
description: 取得附加至此欄位之所有自訂屬性的列舉值。
title: IDebugCustomAttributeQuery2：： EnumCustomAttributes |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 348d5e753702e523f09bef8cbd5f374294c197e4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154440"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
取得附加至此欄位之所有自訂屬性的列舉值。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
擴展傳回代表自訂屬性清單的 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) 物件;否則，如果沒有任何自訂屬性，則會傳回 null 值。

## <a name="return-value"></a>傳回值
 如果成功，則會傳回 S_OK，或 S_FALSE 此欄位上沒有任何自訂屬性。 否則，會傳回錯誤碼;

## <a name="remarks"></a>備註
 欄位可以有多個自訂屬性。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
