---
title: CvReleaseProvider 函式 | Microsoft Docs
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
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c59e5516129d5712983a228f68e4e91301656c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738806"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

釋放標記提供者。 釋放標記提供者不會影響此提供者先前建立的標記系列。 標記系列必須個別由 CvReleaseMarkerSeries 呼叫釋放。 釋放提供者失敗會造成記憶體流失。  
  
## <a name="syntax"></a>語法  
  
```  
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
 **標頭︰** cvmarkers.h  
  
## <a name="see-also"></a>另請參閱  
 [C++ 程式庫參考](../profiling/cpp-library-reference.md)



