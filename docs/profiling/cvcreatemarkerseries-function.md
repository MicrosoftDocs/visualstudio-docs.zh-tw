---
title: CvCreateMarkerSeries 函式 | Microsoft Docs
description: 請參閱並行視覺化檢視 SDK 函式 CvCreateMarkerSeries (C 程式庫) 的參考資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8915724c39a656917d6565c60ddc7dfbb0737564
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941030"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries 函式
建立指定提供者的標記系列。

## <a name="syntax"></a>語法

```C
_Check_return_ HRESULT CvCreateMarkerSeriesW(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCWSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);

_Check_return_ HRESULT CvCreateMarkerSeriesA(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);
```

#### <a name="parameters"></a>參數
 `pProvider` CvInitProvider 先前初始化的提供者物件。 不能是 NULL。

 `pSeriesName` 標記系列名稱。 不可以是 NULL，但允許空字串。

 `ppMarkerSeries` 將儲存標記系列內容的輸出變數位址。 不能是 NULL。

## <a name="return-value"></a>傳回值
 成功建立標記系列時傳回 S_OK，發生任何錯誤時則傳回錯誤碼。 您可以使用 SUCCEEDED/FAILED 巨集檢查是否有錯誤狀況。

## <a name="requirements"></a>規格需求
 **標頭︰** *cvmarkers.h*

 **Unicode：** CvCreateMarkerSeriesW

 **ANSI：** CvCreateMarkerSeriesA

## <a name="see-also"></a>另請參閱
- [C + + 程式庫參考](../profiling/cpp-library-reference.md)