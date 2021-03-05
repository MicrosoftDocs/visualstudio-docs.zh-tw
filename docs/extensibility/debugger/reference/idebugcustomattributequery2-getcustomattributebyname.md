---
description: 取得自訂屬性的名稱的自訂屬性（property）。
title: IDebugCustomAttributeQuery2：： GetCustomAttributeByName |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c65abff050af7b7c34161cbca2594431cb119b5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150077"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
取得自訂屬性的名稱的自訂屬性（property）。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>參數
`pszCustomAttributeName`\
在字串，包含要尋找之自訂屬性的名稱。

`ppBlob`\
[in，out]以自訂屬性位元組填入的陣列。

`pdwLen`\
[in，out]指定要在陣列中傳回的最大位元組數目 `ppBlob` ，並傳回實際寫入陣列的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，或如果自訂屬性不存在，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 將 `ppBlob` 參數設定為 null 值，以傳回可用的屬性位元組數目。 然後配置陣列，並針對參數傳遞該陣列 `ppBlob` 。

 屬性位元組代表自訂屬性的原始資料。

 如果 `ppBlob` 和 `pdwLen` 參數設定為 null 值，則可以使用這個方法來判斷自訂屬性是否只存在。 不過，較簡單的替代方法是呼叫 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
