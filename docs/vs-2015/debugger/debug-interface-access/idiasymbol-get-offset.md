---
title: IDiaSymbol：： get_offset |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f99a9cef4266be9a3373d20f09fca8c64e5a33b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839020"
---
# <a name="idiasymbolget_offset"></a>IDiaSymbol::get_offset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取符號位置的位移。 當 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) 為或時 `LocIsRegRel` 使用 `LocIsBitField` 。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_offset (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回符號位置的位移（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="remarks"></a>備註  
 位移是來自先前決定的某個已知點。 例如， `LocIsBitField` 位置類型的位移通常是來自包含類別的開頭。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2。h|  
|版本：|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)
