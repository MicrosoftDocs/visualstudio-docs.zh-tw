---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider 函式 | Microsoft Docs
description: 請參閱並行視覺化檢視 SDK 函式 CvCreateDefaultMarkerSeriesOfDefaultProvider (C 程式庫) 的參考資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32d7730d36f7e99a2557e764c2adb92862515e24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941043"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider 函式
建立預設提供者的預設標記系列。

## <a name="syntax"></a>語法

```C
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(
   _Out_ PCV_PROVIDER* ppProvider,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>參數
 `ppProvider` 提供者物件變數的位址。 位址不能是 NULL，變數可以是任何值。

 `ppMarkerSeries` 標記系列物件變數的位址。 位址不能是 NULL，變數可以是任何值。

## <a name="return-value"></a>傳回值
 成功建立提供者和標記系列兩者時傳回 S_OK，有任何錯誤時則傳回錯誤碼。 您可以使用 SUCCEEDED/FAILED 巨集檢查是否有錯誤狀況。

## <a name="requirements"></a>規格需求
 **標頭︰** *cvmarkers.h*

## <a name="see-also"></a>另請參閱
- [C + + 程式庫參考](../profiling/cpp-library-reference.md)