---
title: CV_access_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ce5997555b37cf5ab30f091e7124b5025284c0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164383"
---
# <a name="cv_access_e"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定成員函式和變數的可視性範圍 (存取層級) 。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>元素  
 CV_private  
 成員具有私用存取權。  
  
 CV_protected  
 成員擁有受保護的存取權。  
  
 CV_public  
 成員具有公用存取權。  
  
## <a name="remarks"></a>備註  
 此 `friend` 存取規範不包含在此，因為可以存取類別的私用和受保護專案的非成員函式通常會使用它。 使用 [IDiaSymbol：： get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 方法來尋找具有 `SymTagFriend` 存取權的符號。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst。h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol：： get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
