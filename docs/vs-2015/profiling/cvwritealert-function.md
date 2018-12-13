---
title: CvWriteAlert 函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: f75be62f46c44284a263fa5674a9bbea6e85a1b5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745515"
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
  
## <a name="see-also"></a>另請參閱  
 [C++ 程式庫參考](../profiling/cpp-library-reference.md)



