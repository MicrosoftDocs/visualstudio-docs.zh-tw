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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5a9f25c3913519b50131ec5860e127bef3ddc11
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467264"
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
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 程式字串是為了建立序言而解讀的一系列宏。 例如，一般的堆疊框架可能會使用程式字串 `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` 。 此格式為反向波蘭文標記法，其中運算子會遵循運算元。 `T0`表示堆疊上的暫存變數。 此範例會執行下列步驟：

1. 將註冊的內容移 `ebp` 至 `T0` 。

2. 將新增 `4` 至中的值， `T0` 以產生位址、從該位址取得值，並將值儲存在 register 中 `eip` 。

3. 從儲存在中的位址取得值 `T0` ，並將該值儲存在 register 中 `ebp` 。

4. 將新增 `8` 至中的值 `T0` ，並將該值儲存在 register 中 `esp` 。

   請注意，程式字串專屬於 CPU 和針對目前堆疊框架所表示的函式所設定的呼叫慣例。

## <a name="see-also"></a>另請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)