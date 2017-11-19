---
title: "IDiaSymbol::get_baseSymbolId |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cd504d2b-194f-4106-8de5-2de827a79cbd
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b0fb7a89e94c8c0e8edb17e6adcfd0c66cae259
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetbasesymbolid"></a>IDiaSymbol::get_baseSymbolId
擷取要從中指標為基礎的符號 ID。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_baseSymbolId(   
   DWORD *pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]指標`DWORD`保存從中指標為基礎的符號 ID。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)