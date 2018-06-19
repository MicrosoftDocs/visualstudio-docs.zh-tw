---
title: JsThreadServiceCallback Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4b7ea4d0d5eaba17269a1777cdf96b5a2a5cda3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568768"
---
# <a name="jsthreadservicecallback-typedef"></a>JsThreadServiceCallback Typedef
執行緒服務回呼。  
  
## <a name="syntax"></a>語法  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>參數  
 callback  
 背景工作項目的回呼。  
  
 callbackData  
 傳遞給回呼的資料引數。  
  
## <a name="remarks"></a>備註  
 當主機呼叫 JsCreateRuntime 時，可指定背景執行緒服務。 如果指定，則會將背景工作項目傳遞給使用這個回呼的主機。 主機必須立即開始執行背景工作項目並傳回 true，或傳回 false，執行階段將處理執行緒中的工作項目。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)