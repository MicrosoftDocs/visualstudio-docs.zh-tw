---
title: "CvCreateMarkerSeriesWithCodePageA 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords: CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc266ff4a96fa96f89e1eaafe2eaa8377ef601fa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA 函式
建立指定提供者與指定字碼頁的標記系列。 此函式可以用來明確指定標記 API ANSI 函式所寫出文字的字碼頁。 如果要擷取追蹤並使用不同的地區設定/語言在不同電腦上進行分析，設定字碼頁會很有用。 預設會使用 GetACP() 函式所傳回的字碼頁。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pProvider`  
 CvInitProvider 先前初始化的提供者物件。 不可以是 NULL。  
  
 `pSeriesName`  
 標記系列名稱。 不可以是 NULL，但允許空字串。  
  
 `nTextCodePage`  
 有效的字碼頁。  
  
 `ppMarkerSeries`  
 將儲存標記系列內容的輸出變數位址。 不可以是 NULL。  
  
## <a name="return-value"></a>傳回值  
 成功建立標記系列時傳回 S_OK，發生任何錯誤時則傳回錯誤碼。 您可以使用 SUCCEEDED/FAILED 巨集檢查是否有錯誤狀況。  
  
## <a name="requirements"></a>需求  
 **標頭︰**cvmarkers.h  
  
## <a name="see-also"></a>另請參閱  
 [C++ 程式庫參考](../profiling/cpp-library-reference.md)