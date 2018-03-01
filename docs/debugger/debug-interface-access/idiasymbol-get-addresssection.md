---
title: "Idiasymbol:: Get_addresssection |Microsoft 文件"
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
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: af030d63c79901a41ea2704000de5b4d62e70e0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetaddresssection"></a>IDiaSymbol::get_addressSection
擷取位址位置中區段的一部分。 使用時機[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設`LocIsStatic`。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回位址位置中區段的一部分。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是使用符號。  
  
## <a name="remarks"></a>備註  
 針對位於外部 DLL 中的靜態成員，這個方法所傳回的區段可能還 0，因為這個方法會依賴取得之成員的虛擬位址。 虛擬位址都有效才[idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)方法中的[IDiaSession](../../debugger/debug-interface-access/idiasession.md)介面已使用指定的 dll 的載入位址則為非零參數呼叫。  
  
 若要取得時差的部分的位址，請呼叫[idiasymbol:: Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)方法。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)