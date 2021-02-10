---
title: CvIsEnabled 函式 | Microsoft Docs
description: 請參閱並行視覺化檢視 SDK 函式 CvIsEnabled (C 程式庫) 的參考資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0be750f62e248b3d9f837c5baa561765e14bfba5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940939"
---
# <a name="cvisenabled-function"></a>CvIsEnabled 函式
判斷任何工作階段是否已啟用指定的 ETW 提供者。

## <a name="syntax"></a>語法

```C
HRESULT CvIsEnabled(
   _In_ PCV_PROVIDER pProvider
);
HRESULT CvIsEnabledEx(
   _In_ PCV_PROVIDER pProvider,
   _In_ CV_IMPORTANCE level,
   _In_ int category
);
```

#### <a name="parameters"></a>參數
 `category` 分類。

 `level` 重要性層級。

 `pProvider` 有效的提供者物件。 不能是 NULL。

## <a name="return-value"></a>傳回值
 如果提供者目前已啟用，傳回 S_OK。 如果提供者目前已停用，傳回 S_FALSE。 發生任何錯誤時傳回錯誤碼。 使用 FAILED 巨集可檢查是否有錯誤狀況，然後檢查是 S_OK/S_FALSE。

## <a name="requirements"></a>規格需求
 **標頭︰** *cvmarkers.h*

## <a name="see-also"></a>另請參閱
- [C + + 程式庫參考](../profiling/cpp-library-reference.md)