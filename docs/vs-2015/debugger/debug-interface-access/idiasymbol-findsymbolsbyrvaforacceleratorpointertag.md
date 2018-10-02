---
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cb9f928cd239bf9072e2aaa3ad9af56acadef8f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497889"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag)。  
  
指定對應的標記值，這個方法會傳回此虛設常式函式，在指定的相對虛擬位址中所包含的符號的列舉。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>參數  
 `tagValue`  
 [in]位於 pointee 符號記錄指標標記值。  
  
 `rva`  
 [in]用來篩選對應至 pointee 變數，以指定的標記值的符號 rva。  
  
 `ppResult`  
 [out]指標`IDiaEnumSymbols`初始化與結果的介面指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="remarks"></a>備註  
 只有在呼叫這個方法`IDiaSymbol`加速器虛設常式函式對應的介面。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)



