---
title: CV_access_e |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 35b10f8a98284fdec9e94043a4b827fab226d3aa
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="cvaccesse"></a>CV_access_e
指定的成員函式和變數的可見性 （存取層級） 的範圍。  
  
## <a name="syntax"></a>語法  
  
```C++  
typedef enum CV_access_e {   
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
 `friend`存取規範就不會包含此處因為它通常供具有私用和受保護的項目類別的存取權的非成員函式。 使用[idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)方法來尋找符號`SymTagFriend`存取。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol:: Get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)