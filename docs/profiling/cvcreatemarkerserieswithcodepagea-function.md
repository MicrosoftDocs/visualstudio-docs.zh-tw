---
title: CvCreateMarkerSeriesWithCodePageA 函式 | Microsoft Docs
description: 請參閱並行視覺化檢視 SDK 函式 CvCreateMarkerSeriesWithCodePageA (C 程式庫) 的參考資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69f4f19df03c4c2f6bb21a5e2262a4a1495adab8
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686151"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA 函式
為特定提供者與指定字碼頁建立標記系列。 此函式可以用來明確指定標記 API ANSI 函式所寫出文字的字碼頁。 如果要擷取追蹤並使用不同的地區設定/語言在不同電腦上進行分析，設定字碼頁會很有用。 預設會使用 GetACP() 函式所傳回的字碼頁。

## <a name="syntax"></a>語法

```C
HRESULT CvCreateMarkerSeriesWithCodePageA(
   _In_ PCV_PROVIDER pProvider,
   _In_ LPCSTR pSeriesName,
   _In_ UINT nTextCodePage,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>參數
 `pProvider` CvInitProvider 先前初始化的提供者物件。 不能是 NULL。

 `pSeriesName` 標記系列名稱。 不可以是 NULL，但允許空字串。

 `nTextCodePage` 有效的字碼頁。

 `ppMarkerSeries` 將儲存標記系列內容的輸出變數位址。 不能是 NULL。

## <a name="return-value"></a>傳回值
 成功建立標記系列時傳回 S_OK，發生任何錯誤時則傳回錯誤碼。 您可以使用 SUCCEEDED/FAILED 巨集檢查是否有錯誤狀況。

## <a name="requirements"></a>規格需求
 **標頭︰** *cvmarkers.h*

## <a name="see-also"></a>另請參閱
- [C + + 程式庫參考](../profiling/cpp-library-reference.md)