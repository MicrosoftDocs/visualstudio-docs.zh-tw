---
title: 'Idiasymbol:: Get_virtualbaseclass |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseClass method
ms.assetid: 474eddc6-bf16-4731-9145-6db2f2a0b4fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c97290f878a8b3b0835c7e3ac33aa2ebecfb019
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64799261"
---
# <a name="idiasymbolgetvirtualbaseclass"></a>IDiaSymbol::get_virtualBaseClass
擷取指定的使用者定義資料類型是否為虛擬基底類別的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_virtualBaseClass ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]會傳回`TRUE`使用者定義資料類型是虛擬的基底類別; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)