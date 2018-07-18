---
title: JsRef Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9d4c478a45f53e83dfa59fdde21cfa4c988c92e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568528"
---
# <a name="jsref-typedef"></a>JsRef Typedef
Chakra 記憶體回收行程擁有之物件的參考。  
  
## <a name="syntax"></a>語法  
  
```  
typedef void *JsRef;  
```  
  
## <a name="remarks"></a>備註  
 只要 JsRef 參考儲存在區域變數或參數中 (也就是在堆疊上)，Chakra 執行階段將會自動追蹤這些參考。 如果將 JsRef 儲存在堆疊以外的位置，則需要呼叫 JsAddRef 和 JsRelease 來管理物件的存留期，否則記憶體回收行程可能會釋放仍在使用中的物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)