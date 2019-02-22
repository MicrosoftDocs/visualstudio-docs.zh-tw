---
title: IDiaSession::symsAreEquiv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91a3081cc32eb4286ed7b981dfa2a070dbf4a0ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036689"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
檢查兩個符號是否相等。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>參數  
 `symbolA`  
 [in]第一個[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)用於比較的物件。  
  
 `symbolB`  
 [in]第二個`IDiaSymbol`用於比較的物件。  
  
## <a name="return-value"></a>傳回值  
 如果符號相等，則會傳回`S_OK`; 否則傳回`S_FALSE`，符號不相等。 否則，傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)