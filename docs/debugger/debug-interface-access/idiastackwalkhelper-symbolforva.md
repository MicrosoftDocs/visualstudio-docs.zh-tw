---
title: 'Idiastackwalkhelper:: Symbolforva |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22148ce55cbf3d12f1de9c11e8865debde74aa87
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902733"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
擷取包含指定的虛擬位址的符號。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### <a name="parameters"></a>參數  
 `va`  
 [in]包含在要求的符號中的虛擬位址。 符號必須是`SymTagFunctionType`(取值[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別)。  
  
 `ppSymbol`  
 [out][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示在指定位址的符號。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)