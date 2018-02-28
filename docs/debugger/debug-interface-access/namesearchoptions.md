---
title: "NameSearchOptions |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4a6a4237e806a6906ef984cd942e027fe7d9227d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="namesearchoptions"></a>NameSearchOptions
指定符號和檔案名稱的搜尋選項。  
  
## <a name="syntax"></a>語法  
  
```C++  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>項目  
 `nsNone`  
 未指定任何選項。  
  
 `nsfCaseSensitive`  
 適用於區分大小寫名稱相符。  
  
 `nsfCaseInsensitive`  
 適用於不區分大小寫的名稱相符。  
  
 `nsfFNameExt`  
 視為路徑名稱，並套用 filename.ext 名稱相符。  
  
 `nsfRegularExpression`  
 適用於使用星號 （*） 和問號 （？） 做為萬用字元區分大小寫名稱相符。  
  
 `nsfUndecoratedName`  
 僅適用於具有未裝飾和裝飾名稱的符號。  
  
## <a name="remarks"></a>備註  
 這個列舉的值傳遞給下列方法：  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>需求  
 標頭： dia2.h  
  
## <a name="see-also"></a>請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Idiasession:: Findfile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)