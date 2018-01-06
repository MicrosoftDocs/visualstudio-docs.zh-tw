---
title: "IDiaSession::findInlineeLines |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b6822d8b-70d5-470b-8278-3aec4680326c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 83206c0c5f4aac76393e26c625c98bfbc28eb687
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindinlineelines"></a>IDiaSession::findInlineeLines
擷取可讓用戶端來逐一查看的所有函式內嵌，直接或間接地以指定的父符號的行號資訊的列舉。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findInlineeLines (   
   IDiaSymbol*       parent,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `parent`  
 [in]`IDiaSymbol`表示父物件。  
  
 `ppResult`  
 [out]保存`IDiaEnumLineNumbers`物件，其中包含所擷取的行號的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)