---
title: CvReleaseProvider 函式 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 419cf6c30822a041397e73104974989881ac6e59
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822472"
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
 `pProvider`  
 提供者的內容。 不可以是 NULL。  
  
## <a name="return-value"></a>傳回值  
 成功釋放提供者時傳回 S_OK，發生任何錯誤時則傳回錯誤碼。 您可以使用 SUCCEEDED/FAILED 巨集檢查是否有錯誤狀況。  
  
## <a name="requirements"></a>需求  
 **標頭︰** *cvmarkers.h*  
  
## <a name="see-also"></a>另請參閱  
 [C++ 程式庫參考](../profiling/cpp-library-reference.md)