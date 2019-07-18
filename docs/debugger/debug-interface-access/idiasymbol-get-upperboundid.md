---
title: 'Idiasymbol:: Get_upperboundid |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_upperBoundId method
ms.assetid: ddfa1617-bd0f-4187-ba77-a225bab93a95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7711073319a5381a205672ae8023699a725b8936
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64803482"
---
# <a name="idiasymbolgetupperboundid"></a>IDiaSymbol::get_upperBoundId
擷取的符號識別項的 FORTRAN 陣列維度的上限。

## <a name="syntax"></a>語法

```C++
HRESULT get_upperBoundId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`
- [out]傳回代表 FORTRAN 陣列維度的上限的符號 ID。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="remarks"></a>備註
 識別碼是由 DIA SDK，將標示為唯一的所有符號的唯一值。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)