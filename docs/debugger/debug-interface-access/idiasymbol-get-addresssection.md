---
title: 'Idiasymbol:: Get_addresssection |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e62f6738d07b2f0e4463cd685bf3111cd7011a10
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820017"
---
# <a name="idiasymbolgetaddresssection"></a>IDiaSymbol::get_addressSection
擷取位址位置中區段的一部分。 使用時機[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設定為`LocIsStatic`。  
  
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
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是適用於符號。  
  
## <a name="remarks"></a>備註  
 位於外部的 DLL 中的靜態成員，這個方法所傳回的區段可能是 0，因為這個方法依賴於取得之成員的虛擬位址。 虛擬位址的有效期才[idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)方法中的[IDiaSession](../../debugger/debug-interface-access/idiasession.md)已呼叫具有非零參數指定的 dll 載入位址的介面。  
  
 若要取得為位址位移的一部分，請呼叫[idiasymbol:: Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)方法。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)