---
title: 'Idiasymbol:: Get_symbolsfilename |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symbolsFileName method
ms.assetid: c1aa39ee-d645-431e-bf5f-0640c0998934
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93f04d4ffee712a87dc784b5b83496b86d70ae25
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470393"
---
# <a name="idiasymbolgetsymbolsfilename"></a>IDiaSymbol::get_symbolsFileName
擷取要從中載入符號檔的名稱。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_symbolsFileName (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回從中載入符號檔的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 這個屬性是僅適用於具有符號[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值`SymTagExe`中也具有全域範圍。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)