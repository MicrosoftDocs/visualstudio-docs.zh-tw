---
title: IDiaSymbol::get_baseDataSlot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: f9ed21b7-9397-4813-926e-ade11914b06b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ce2a1f2d6404f7bbb708478dff1e64b09b8246d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464223"
---
# <a name="idiasymbolget_basedataslot"></a>IDiaSymbol::get_baseDataSlot
抓取基底資料槽。

## <a name="syntax"></a>語法

```C++
HRESULT get_baseDataSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展 `DWORD` 保存基底資料位置之的指標。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)