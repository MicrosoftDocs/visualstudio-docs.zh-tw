---
title: IDiaSession::findInlineeLinesByLinenum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d16bc6f3e2e8f190e3a26023407237509984cece
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838959"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

抓取列舉，可讓用戶端逐一查看在指定的原始程式檔和行號中，直接或間接內嵌的所有函式的行號資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `compiland`  
 在 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件，代表要在其中搜尋行號的編譯單位。 這個參數不可以是 `NULL`。  
  
 `file`  
 在 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 物件，代表要在其中搜尋的原始程式檔。 這個參數不可以是 `NULL`。  
  
 `linenum`  
 在指定以一個為基礎的行號。  
  
> [!NOTE]
> 您無法使用零來指定所有的行 (使用 [IDiaSession：： findLines](../../debugger/debug-interface-access/idiasession-findlines.md) 方法來尋找) 的所有行。  
  
 `column`  
 在指定資料行編號。 使用零來指定所有資料行。 資料行是一行的位元組位移。  
  
 `ppResult`  
 擴展傳回 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) 物件，其中包含已取出行號的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
