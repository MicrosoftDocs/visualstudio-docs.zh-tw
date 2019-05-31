---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d874a00c3c82108c224f18922f2b4853279beaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322207"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
取得指定欄位名稱的自訂屬性的自訂屬性位元組。

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
[in]字串，包含要尋找的自訂屬性的名稱。

`ppBlob`\
[in、 out]陣列，其中會填入自訂屬性的位元組。

`pdwLen`\
[in、 out]指定要傳回的位元組數目上限`ppBlob`陣列並傳回實際寫入至陣列的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，或如果沒有自訂屬性，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 設定`ppBlob`參數為 null 的值，傳回的數字屬性可用位元組。 配置的陣列，然後將陣列中的傳送`ppBlob`參數。

 屬性代表的原始資料的自訂屬性。

 如果`ppBlob`和`pdwLen`參數設定為 null 的值，這個方法可用來判斷是否只存在於自訂屬性。 簡單的替代方法，不過，是呼叫[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)