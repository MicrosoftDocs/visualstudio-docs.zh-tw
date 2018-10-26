---
title: 'Idiaenumsymbolsbyaddr:: Symbolbyva |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByVA method
ms.assetid: ac84339f-70c6-48ed-85d0-6d7d1b5194e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 688d45cce181b7c4ac0b61584a65c7c755b0f2bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905749"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyva"></a>IDiaEnumSymbolsByAddr::symbolByVA
將列舉值的虛擬位址 (VA) 中執行查閱。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT symbolByVA (   
   DWORD**      virtualAddress,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### <a name="parameters"></a>參數  
 virtualAddress  
 [in]虛擬位址。  
  
 ppsymbol  
 [out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示找到的符號。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`如果找不到符號。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)