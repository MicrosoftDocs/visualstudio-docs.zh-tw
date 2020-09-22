---
title: IDiaSymbol：： get_length |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_length method
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9f8c757d3da3049c29f7da13b13985dc2c50b4b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840219"
---
# <a name="idiasymbolget_length"></a>IDiaSymbol::get_length
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取此符號所表示之物件所使用的記憶體位數或位元組數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_length (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 擴展傳回這個符號所表示之物件所使用的記憶體位元組數目或位數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。  
  
> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。  
  
## <a name="remarks"></a>備註  
 如果符號的 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) 為，則 `LocIsBitField` 這個方法所傳回的長度會是位，否則，所有其他位置類型的長度會以位元組為單位。  
  
## <a name="example"></a>範例  
  
```cpp#  
IDiaSymbol* pSymbol;  
ULONGLONG   length;  
pSymbol->get_length( &length );  
```  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2。h|  
|版本：|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)
