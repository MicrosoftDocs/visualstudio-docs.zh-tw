---
title: CvLeaveSpan 函式 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 776c24777403b9d88de31e11d0c28fe104666600
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974109"
---
# <a name="cvleavespan-function"></a>CvLeaveSpan 函式
標記範圍的結尾。

## <a name="syntax"></a>語法

```C
HRESULT CvLeaveSpan(
   _In_ PCV_SPAN pSpan
);
```

#### <a name="parameters"></a>參數
 `pSpan` 先前呼叫 CvEnterSpan* 所傳回的範圍物件。 不可以是 NULL。

## <a name="return-value"></a>傳回值
 當訊息成功寫入時傳回 S_OK。 發生任何錯誤時傳回錯誤碼。 您可以使用 SUCCEEDED/FAILED 巨集檢查是否有錯誤狀況。

## <a name="requirements"></a>需求
 **標頭︰** *cvmarkers.h*

## <a name="see-also"></a>另請參閱
- [C++ 程式庫參考](../profiling/cpp-library-reference.md)