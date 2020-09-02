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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
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

擴展 `TRUE` 如果函數為簡介虛擬，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="example"></a>範例

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

`A::f1`和 `B::f1` 都是虛擬函式，但 `A::f1` 是虛擬的簡介。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
