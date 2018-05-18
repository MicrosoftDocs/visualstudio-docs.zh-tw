---
title: CvReleaseMarkerSeries 函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 73f2b7f930a4e58eb3c14380df16892e92a870f5
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2018
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
 `pMarkerSeries`  
 提供者物件變數的位址。 位址不能是 NULL，變數可以是任何值。  
  
## <a name="return-value"></a>傳回值  
 成功釋放標記系列時傳回 S_OK，發生任何錯誤時則傳回錯誤碼。 您可以使用 SUCCEEDED/FAILED 巨集檢查是否有錯誤狀況。  
  
## <a name="requirements"></a>需求  
 **標頭︰** cvmarkers.h  
  
## <a name="see-also"></a>請參閱  
 [C++ 程式庫參考](../profiling/cpp-library-reference.md)