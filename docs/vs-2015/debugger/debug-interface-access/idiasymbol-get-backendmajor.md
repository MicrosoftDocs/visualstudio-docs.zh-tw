---
title: IDiaSymbol：： get_backEndMajor |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMajor method
ms.assetid: 900a05dd-c29b-44ad-b46b-f43bda819a66
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bc692056f1418c55ce1038101f1a60946de507e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839060"
---
# <a name="idiasymbolget_backendmajor"></a>IDiaSymbol::get_backEndMajor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取編譯器的後端主要版本號碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_backEndMajor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回後端主要版本號碼。 請參閱＜備註＞。  
  
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
