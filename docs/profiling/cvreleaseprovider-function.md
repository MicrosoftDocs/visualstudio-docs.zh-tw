---
title: CvReleaseProvider 函式 | Microsoft Docs
description: 請參閱並行視覺化檢視 SDK 函式 CvReleaseProvider (C 程式庫) 的參考資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae363f1909f169d2d5dc4004a79cfe3c2919bdf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948227"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider 函式
釋放標記提供者。 釋放標記提供者不會影響此提供者先前建立的標記系列。 標記系列必須個別由 CvReleaseMarkerSeries 呼叫釋放。 釋放提供者失敗會造成記憶體流失。

## <a name="syntax"></a>語法

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>參數
 `pProvider` 提供者的內容。 不能是 NULL。

## <a name="return-value"></a>傳回值
 成功釋放提供者時傳回 S_OK，發生任何錯誤時則傳回錯誤碼。 您可以使用 SUCCEEDED/FAILED 巨集檢查是否有錯誤狀況。

## <a name="requirements"></a>規格需求
 **標頭︰** *cvmarkers.h*

## <a name="see-also"></a>另請參閱
- [C + + 程式庫參考](../profiling/cpp-library-reference.md)