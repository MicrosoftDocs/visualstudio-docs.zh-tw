---
title: CvWriteAlert 函式 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteAlertVA
- cvmarkers/CvWriteAlertVW
- cvmarkers/CvWriteAlertA
- cvmarkers/CvWriteAlertW
helpviewer_keywords:
- CvWriteAlertVW method
- CvWriteAlertA method
- CvWriteAlertVA method
- CvWriteAlertW method
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f5c428b471c576c1ca15b73a1c8b2ccfa2cc7b6
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54770981"
---
# <a name="cvwritealert-function"></a>CvWriteAlert 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將警示寫入並行視覺化檢視追蹤檔。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CvWriteAlertW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteAlertVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### <a name="parameters"></a>參數  
 `argList`  
 列出引數。  
  
 `pMarkerSeries`  
 有效的標記系列內容。 不可以是 NULL。  
  
 `pMessage`  
 訊息格式字串。 不可以是 NULL。  
  
## <a name="return-value"></a>傳回值  
 當訊息成功寫入時傳回 S_OK。 發生任何錯誤時傳回錯誤碼。 您可以使用 SUCCEEDED/FAILED 巨集檢查是否有錯誤狀況。  
  
## <a name="requirements"></a>需求  
 **標頭︰** cvmarkers.h  
  
 **Unicode：** CvWriteAlertW、CvWriteAlertVW  
  
 **ANSI：** CvWriteAlertA、CvWriteAlertVA  
  
## <a name="see-also"></a>請參閱  
 [C++ 程式庫參考](../profiling/cpp-library-reference.md)
