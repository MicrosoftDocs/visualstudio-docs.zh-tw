---
title: "Idiasession:: Findlinesbyrva |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findLinesByRVA method
ms.assetid: 06f53b0b-b5b4-42cf-9252-dcee0dbe2d71
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 00f7ddef98d64bb09c1c010f4f120e11180e48e5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindlinesbyrva"></a>IDiaSession::findLinesByRVA
擷取含有指定相對虛擬位址 (RVA) 中指定的編譯模組的行。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findLinesByRVA (   
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rva`  
 [in]指定的位址為 RVA。  
  
 `length`  
 [in]指定的位址範圍，以涵蓋此查詢使用的位元組數目。  
  
 `ppResult`  
 [out]傳回[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)物件，其中包含一份所有列數字的封面指定的位址範圍。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 此範例顯示的函式，會取得所有包含在指定的函式使用函式的相對虛擬位址和長度的行號。  
  
```C++  
IDiaEnumLineNumbers* GetLineNumbersByRVA(IDiaSymbol *pFunc, IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    DWORD                rva;  
    ULONGLONG            length;  
  
    if (pFunc->get_relativeVirtualAddress ( &rva ) == S_OK)  
    {  
        pFunc->get_length ( &length );  
        pSession->findLinesByRVA( rva, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)