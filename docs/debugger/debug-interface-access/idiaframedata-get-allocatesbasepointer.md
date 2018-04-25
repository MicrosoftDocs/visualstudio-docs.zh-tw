---
title: 'Idiaframedata:: Get_allocatesbasepointer |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: efbadae145fff951effc7413e432ab2570549c95
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
擷取這個旗標指示是否配置此位址範圍中的程式碼基底指標。 這個方法已被取代。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回`TRUE`如果配置基底指標; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個屬性應只能由程式碼，先前稱為存取 FPO_DATA，或當程式字串傳回[idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)方法`NULL`。 否則，程式字串包含要計算前一個暫存器值所需的所有資訊。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)