---
title: CV_access_e |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 373149884078b58926493fd7f37756ddb4eb8829
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838751"
---
# <a name="cvaccesse"></a>CV_access_e
指定的成員函式和變數的可見性 （存取層級） 的範圍。  
  
## <a name="syntax"></a>語法  
  
```C++  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>項目  
 CV_private  
 成員具有私用存取。  
  
 CV_protected  
 成員具有保護的存取權。  
  
 CV_public  
 成員具有公用存取權。  
  
## <a name="remarks"></a>備註  
 `friend`存取規範就不會包含這裡因為通常由具有類別的私用和受保護項目的存取權的非成員函式。 使用[idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)方法來尋找具有符號`SymTagFriend`存取。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)