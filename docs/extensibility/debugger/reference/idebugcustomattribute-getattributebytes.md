---
description: 取得以位元組 blob 表示的屬性資訊。
title: IDebugCustomAttribute：： GetAttributeBytes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84d6e807e3be6d0fbdaa94834fbc8cad37f8e4d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088077"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
取得以位元組 blob 表示的屬性資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>參數
`ppBlob`\
[in，out]以屬性位元組填入的陣列。

`pdwLen`\
[in，out]指定要在陣列中傳回的最大位元組數目 `ppBlob` ，並傳回實際寫入陣列的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 將 `ppBlob` 參數設定為 null 值，以傳回可用的屬性位元組數目。 然後配置陣列，並針對參數傳遞該陣列 `ppBlob` 。

 屬性位元組代表自訂屬性的原始資料。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
