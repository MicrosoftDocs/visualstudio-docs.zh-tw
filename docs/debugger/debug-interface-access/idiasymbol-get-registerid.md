---
title: "Idiasymbol:: Get_registerid |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c944869d48c484f7ddf234f4e00a5d10e96f70ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
擷取位置的登錄指示項時[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設`LocIsEnregistered`。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回之位置的登錄指示項。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是使用符號。  
  
## <a name="remarks"></a>備註  
 如果符號為相對於暫存器，亦即，如果符號的[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設`LocIsRegRel`，使用`get_registerId`方法呼叫後面接著[idiasymbol:: Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)取得符號所在位置的暫存器從位移的方法。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)