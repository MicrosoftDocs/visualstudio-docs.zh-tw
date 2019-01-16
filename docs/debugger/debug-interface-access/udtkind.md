---
title: UdtKind |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35631a3913f067e6520da630cd49969d8a2b40f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924224"
---
# <a name="udtkind"></a>UdtKind
描述各種不同的使用者定義型別 (UDT)。  
  
## <a name="syntax"></a>語法  
  
```C++  
enum UdtKind {   
   UdtStruct,  
   UdtClass,  
   UdtUnion,  
   UdtInterface  
};  
```  
  
## <a name="elements"></a>項目  
 UdtStruct  
 UDT 是一種結構。  
  
 UdtClass  
 UDT 是一個類別。  
  
 UdtUnion  
 UDT 是等位。  
  
 UdtInterface  
 UDT 是一種介面。  
  
## <a name="remarks"></a>備註  
 傳回這個列舉型別中的值[idiasymbol:: Get_udtkind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)