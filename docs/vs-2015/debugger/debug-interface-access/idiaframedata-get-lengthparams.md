---
title: IDiaFrameData::get_lengthParams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthParams method
ms.assetid: a9177ed6-9ba8-4384-b411-24cad07d031b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f633fe4633ba92b1054aec7f516a6a0921bc64ca
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943809"
---
# <a name="idiaframedatagetlengthparams"></a>IDiaFrameData::get_lengthParams
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取位元組的推送到堆疊上的參數數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_lengthParams (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回參數的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法所傳回的值通常用於程式字串的解譯 (請參閱[idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)方法定義的程式字串)。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
