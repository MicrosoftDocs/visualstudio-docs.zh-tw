---
title: 'Idiasession:: Findfile |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 32c8fa5c6f3cd8ec3cf1cead397eadadb99e050d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909937"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
擷取原始程式檔編譯模組和名稱。  
  
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
 [in][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示要當做內容用於搜尋的編譯。 將此參數設定為`NULL`若要在所有編譯中都尋找原始程式檔。  
  
 `name`  
 [in]指定要擷取的來源檔案的名稱。 將此參數設定為`NULL`所有原始程式檔，來擷取。  
  
 `option`  
 [in]指定套用至搜尋名稱的比較選項。 從數值[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)單獨或合併，就可以使用列舉型別。  
  
 `ppResult`  
 [out]傳回[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)擷取物件，包含來源檔案的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
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