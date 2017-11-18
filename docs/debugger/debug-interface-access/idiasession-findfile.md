---
title: "Idiasession:: Findfile |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef230d1b82992f769011e0cb1d9d4ff11145b82d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
擷取原始程式檔的編譯模組和名稱。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pCompiland`  
 [in][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表要做為內容搜尋的編譯。 這個參數設定為`NULL`若要在所有編譯中都尋找原始程式檔。  
  
 `name`  
 [in]指定要擷取的來源檔案的名稱。 這個參數設定為`NULL`所有原始程式檔，來擷取。  
  
 `option`  
 [in]指定套用至搜尋名稱的比較選項。 從數值[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉型別可以單獨或合併使用。  
  
 `ppResult`  
 [out]傳回[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)擷取物件，其中包含來源檔案的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
  
```C++  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)