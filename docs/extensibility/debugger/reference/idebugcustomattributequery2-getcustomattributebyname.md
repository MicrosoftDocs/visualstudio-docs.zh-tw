---
title: IDebug自定義屬性查詢2::獲取按名稱獲取自定義屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47471f2743e705b06fb9a1bda6752b24a7836d1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732557"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
獲取給定自定義屬性名稱的自定義屬性位元組。

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
[在]包含要尋找的自訂屬性的名稱的字串。

`ppBlob`\
[進出]使用自定義屬性位元組填充的陣列。

`pdwLen`\
[進出]指定要在`ppBlob`陣列中傳回的最大位元,並返回實際寫入陣列的位元組數。

## <a name="return-value"></a>傳回值
 如果成功,則返回S_OK或返回S_FALSE自定義屬性不存在。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 將`ppBlob`參數設定為空值以返回可用屬性位元數。 然後分配一個陣列,並將該陣列傳遞給該`ppBlob`參數。

 屬性位元表示自定義屬性的原始數據。

 如果`ppBlob``pdwLen`和 參數設定為 null 值,則此方法可用於確定自訂屬性是否僅存在。 但是,一個更簡單的替代方法是調用[IsCustom屬性定義](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
