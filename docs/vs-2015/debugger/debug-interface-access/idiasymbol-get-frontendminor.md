---
title: IDiaSymbol：： get_frontEndMinor |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 12e5956f880a79d7946ff9655ec1ef3d1a79ff22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839037"
---
# <a name="idiasymbolget_frontendminor"></a>IDiaSymbol::get_frontEndMinor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取前端次要版本號碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回 front. end 次要版本號碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="remarks"></a>備註  
 編譯器通常是由兩個主要元素組成：前端 (剖析器) ，其會將原始程式碼剖析成中繼格式，而後端 (程式碼產生器) ，這會將中繼格式轉換成元件。 前端與後端的版本不同，不是罕見的。  
  
 前端或後端版本號碼由三個部分組成： \<major> ... \<minor> \<build> ，其中 \<major> 是主要版本號碼， \<minor> 是次要版本號碼，而 \<build> 是組建編號。 例如 13.10.3077。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2。h|  
|版本：|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
