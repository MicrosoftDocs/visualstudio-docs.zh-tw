---
title: CvReleaseMarkerSeries 函式 | Microsoft Docs
description: 請參閱並行視覺化檢視 SDK 函式 CvReleaseMarkerSeries (C 程式庫) 的參考資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a69f60a991b9d88e6969992edbfe8eabdb7bd116
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686450"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries 函式
釋放標記系列。 不要在釋放之後使用標記系列物件，否則應用程式可能會當機。 釋放標記系列失敗會造成記憶體流失。

## <a name="syntax"></a>語法

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>參數
 `pMarkerSeries` 提供者物件變數的位址。 位址不能是 NULL，變數可以是任何值。

## <a name="return-value"></a>傳回值
 成功釋放標記系列時傳回 S_OK，發生任何錯誤時則傳回錯誤碼。 您可以使用 SUCCEEDED/FAILED 巨集檢查是否有錯誤狀況。

## <a name="requirements"></a>規格需求
 **標頭︰** *cvmarkers.h*

## <a name="see-also"></a>另請參閱
- [C + + 程式庫參考](../profiling/cpp-library-reference.md)