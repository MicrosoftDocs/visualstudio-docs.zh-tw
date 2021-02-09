---
title: IDiaFrameData::get_program | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1480b7e3273e3746f95c01ab8913eb5c934edc39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864940"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
抓取在呼叫目前的函式之前，用來計算暫存器集的程式字串。

## <a name="syntax"></a>語法

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回程序字串。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 程式字串是為了建立序言而解讀的一系列宏。 例如，一般的堆疊框架可能會使用程式字串 `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` 。 格式為反轉波蘭文標記法，其中運算子會在運算元後面。 `T0` 代表堆疊上的暫存變數。 此範例會執行下列步驟：

1. 將 [註冊] 的內容移 `ebp` 至 `T0` 。

2. 將加入 `4` 至中的值 `T0` ，以產生位址、從該位址取得值，並將值儲存在 register 中 `eip` 。

3. 從儲存在中的位址取得值 `T0` ，並將該值儲存在 register 中 `ebp` 。

4. 將加入 `8` 至中的值 `T0` ，並將該值儲存在 register 中 `esp` 。

   請注意，程式字串是針對 CPU 和針對目前堆疊框架所表示的函式所設定的呼叫慣例所特有的。

## <a name="see-also"></a>另請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)