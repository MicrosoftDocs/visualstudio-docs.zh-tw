---
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf274bb0f572da11a9aa43248da7eaa72a2e73c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150420"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取符合名稱和符號類型之指定父識別碼的所有子系。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 在代表父系的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。 如果這個父系符號是函式、模組或區塊，則會在中傳回其詞法子系 `ppResult` 。 如果父符號是型別，則會傳回其類別子系。 如果這個參數是 `NULL` ，則 `symtag` 必須將設為 `SymTagExe` 或 `SymTagNull` ，這會傳回全域範圍 ( .exe 檔) 。  
  
 `symtag`  
 在指定要抓取之子系的符號標記。 值取自 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 列舉。 設定為 `SymTagNull` 以取得所有子系。  
  
 `name`  
 在指定要抓取之子系的名稱。 `NULL`針對要取出的所有子系，設定為。  
  
 `compareFlags`  
 在指定套用至名稱比對的比較選項。 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉中的值可以單獨使用或合併使用。  
  
 `ppResult`  
 擴展傳回 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 物件，其中包含已抓取之子符號的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例顯示如何尋找符合名稱之函式的區域變數 `pFunc` `szVarName` 。  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>另請參閱  
 [概述](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
