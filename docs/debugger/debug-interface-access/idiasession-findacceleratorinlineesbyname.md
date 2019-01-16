---
title: IDiaSession::findAcceleratorInlineesByName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a13400cab447f4122a88bfbcec1265ae8e7e2fd5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828091"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
傳回對應到指定的內嵌函式名稱的內嵌框架的符號的列舉。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `name`  
 [in]要搜尋的內嵌項函式名稱。  
  
 `option`  
 [in]搜尋內嵌框架時所要使用的名稱搜尋選項對應至`name`。 如需詳細資訊，請參閱 < [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)。  
  
 `ppResult`  
 [out]指標`IDiaEnumSymbols`初始化與結果的介面指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 此函式會搜尋只在加速器 stub 函式內的內嵌項屬性。 它會忽略原生 c + + 程序記錄。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)