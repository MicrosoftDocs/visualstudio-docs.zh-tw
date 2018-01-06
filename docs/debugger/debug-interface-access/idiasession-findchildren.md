---
title: "Idiasession:: Findchildren |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0cae2dd492fd11ff4a5d707ba95c571711358358
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
擷取符合的名稱和符號類型指定的父系識別碼的所有子系。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `parent`  
 [in][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)表示父物件。 如果這個父符號函式、 模組或區塊，則會傳回其子語彙`ppResult`。 如果父符號是類型，則會傳回其子類別。 如果這個參數是`NULL`，然後`symtag`必須設為`SymTagExe`或`SymTagNull`，它會傳回全域範圍 （.exe 檔案）。  
  
 `symtag`  
 [in]指定要擷取的子系的符號標記。 值取自[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別。 設定為`SymTagNull`擷取所有子系。  
  
 `name`  
 [in]指定要擷取的子系的名稱。 設定為`NULL`要擷取的所有子系。  
  
 `compareFlags`  
 [in]指定套用至名稱比對的比較選項。 從數值[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉型別可以單獨或合併使用。  
  
 `ppResult`  
 [out]傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)擷取物件，包含子符號清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例顯示如何尋找函式的區域變數`pFunc`該相符項目名稱`szVarName`。  
  
```C++  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>請參閱  
 [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)