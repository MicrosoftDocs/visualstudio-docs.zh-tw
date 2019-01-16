---
title: 'Idiasymbol:: Get_iscvtcil |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isCVTCIL method
ms.assetid: 711b81fd-9549-44dc-9761-5eb862ed64c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab73bfbfb859967d9df4f27d6d254334a27e53ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879393"
---
# <a name="idiasymbolgetiscvtcil"></a>IDiaSymbol::get_isCVTCIL
擷取旗標，指出是否將模組已從通用中間語言 (CIL) 模組轉換為原生模組。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_isCVTCIL(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFlag`  
 [out]會傳回`TRUE`模組從 CIL 轉換至原生程式碼; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 這個屬性會使用來自`SymTagCompilandDetails`符號類型 (請參閱 < [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)。  
  
## <a name="requirements"></a>需求  
  
|需求|說明|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK 8.0 版|  
  
## <a name="see-also"></a>請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)