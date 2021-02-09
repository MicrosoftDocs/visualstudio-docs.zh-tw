---
title: IDiaSymbol：： get_isSingleInheritance |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 46cde656-059b-4c20-9476-3ca68ccc9912
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 10bfeb77def9b6b1caa9a49b8dfd42c3b56d5774
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863113"
---
# <a name="idiasymbolget_issingleinheritance"></a>IDiaSymbol::get_isSingleInheritance
指定指標是否 `this` 指向具有單一繼承的資料成員。

## <a name="syntax"></a>語法

```C++
HRESULT get_isSingleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展的指標 `BOOL` ，指定 `this` 指標是否指向具有單一繼承的資料成員。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)