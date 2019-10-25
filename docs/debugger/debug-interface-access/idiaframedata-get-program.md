---
title: IDiaFrameData::get_program | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 135f2b0a042dd74b573a0746831a48fb27e7c2a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743524"
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

脫銷傳回程序字串。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果不支援此屬性，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 程式字串是為了建立序言而解讀的一系列宏。 例如，一般的堆疊框架可能會使用程式字串 `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`。 此格式為反向波蘭文標記法，其中運算子會遵循運算元。 `T0` 代表堆疊上的暫存變數。 這個範例會執行下列步驟：

1. 將 register `ebp` 的內容移至 `T0`。

2. 將 `4` 新增至 `T0` 中的值，以產生位址、從該位址取得值，並將值儲存在 register `eip` 中。

3. 從儲存在 `T0` 中的位址取得值，並將該值儲存在 register `ebp` 中。

4. 將 `8` 新增至 `T0` 中的值，並將該值儲存在 register `esp` 中。

   請注意，程式字串專屬於 CPU 和針對目前堆疊框架所表示的函式所設定的呼叫慣例。

## <a name="see-also"></a>請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)