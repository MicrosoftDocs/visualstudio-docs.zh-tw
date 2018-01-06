---
title: "IDiaSession::findAcceleratorInlineesByName |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 084fa6d3021e7657ae0aef639a110450ed9f083d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
傳回對應至指定的內嵌函式名稱的內嵌框架的符號的列舉。  
  
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
 [in]要搜尋的內嵌函式名稱。  
  
 `option`  
 [in]名稱搜尋選項來搜尋的內嵌框架時，使用對應至`name`。 如需詳細資訊，請參閱[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)。  
  
 `ppResult`  
 [out]指標`IDiaEnumSymbols`初始化與結果的介面指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 此函式會搜尋 inlinees 只在 Accelerator stub 函式內。 它會略過原生 c + + 程序的記錄。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)