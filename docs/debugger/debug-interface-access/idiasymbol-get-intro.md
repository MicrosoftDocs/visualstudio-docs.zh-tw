---
title: 'Idiasymbol:: Get_intro |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 153daa1f43ba4945a5eb32aea82c5d58ff57c5f6
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "62836796"
---
# <a name="idiasymbolgetintro"></a>IDiaSymbol::get_intro
擷取指定函數是否為簡介的虛擬函式的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
`pRetVal`

[out]會傳回`TRUE`函式是簡介虛擬; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="example"></a>範例

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

兩者`A::f1`並`B::f1`是虛擬的函式，但`A::f1`是虛擬的簡介。

## <a name="requirements"></a>需求

|需求|說明|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
