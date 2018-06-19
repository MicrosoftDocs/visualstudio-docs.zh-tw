---
title: 'Idiastackwalkhelper:: Symbolforva |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 0e70dac639f18f934bb997cc4979bdbe6a7d8c4c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31467533"
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
 [in]包含要求的符號中的虛擬位址。 符號必須`SymTagFunctionType`(介於[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別)。  
  
 `ppSymbol`  
 [out][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示在指定的位址的符號。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)