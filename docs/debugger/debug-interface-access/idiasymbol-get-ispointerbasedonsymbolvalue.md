---
title: IDiaSymbol::get_isPointerBasedOnSymbolValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 577c8011-9269-4373-8577-b4822a983724
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0d6e653bbafc09a9182cac743bdc97a23a6c58e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463292"
---
# <a name="idiasymbolget_ispointerbasedonsymbolvalue"></a>IDiaSymbol::get_isPointerBasedOnSymbolValue
指定指標是否 `this` 以符號值為基礎。

## <a name="syntax"></a>語法

```C++
HRESULT get_isPointerBasedOnSymbolValue(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展的指標 `BOOL` ，指定 `this` 指標是否以符號值為基礎。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)