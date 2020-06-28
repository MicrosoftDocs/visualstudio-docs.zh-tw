---
title: IDiaSymbol：： get_intro |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: b48f91dcb68f44f070e596d674461367dcf22966
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463516"
---
# <a name="idiasymbolget_intro"></a>IDiaSymbol::get_intro
抓取指定函數是否為簡介虛擬函式的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
`pRetVal`

脫銷`TRUE`如果函數是簡介虛擬，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="example"></a>範例

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

`A::f1`和 `B::f1` 都是虛擬函式，但 `A::f1` 是簡介虛擬。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
