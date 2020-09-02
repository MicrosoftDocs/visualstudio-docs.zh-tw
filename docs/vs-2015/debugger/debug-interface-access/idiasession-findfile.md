---
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e791bc09ba3dd4f1811c650926eadb0f7f0462a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431637"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

依編譯單位和名稱抓取原始程式檔。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pCompiland`  
 在 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件，代表要當做搜尋內容使用的編譯單位。 將此參數設定為， `NULL` 以在所有 compilands 中尋找原始檔。  
  
 `name`  
 在指定要取出的原始程式檔名稱。 `NULL`針對要取出的所有來源檔案，將此參數設定為。  
  
 `option`  
 在指定套用至名稱搜尋的比較選項。 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉中的值可以單獨使用或合併使用。  
  
 `ppResult`  
 擴展傳回 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) 物件，其中包含已抓取的原始程式檔清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)
