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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444682"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取列舉型別，可讓用戶端來逐一查看所有函式是內嵌，直接或間接地在 指定的來源檔案和行號的行號資訊。  
  
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
 [in][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示要在其中搜尋的行號編譯模組。 這個參數不可以是 `NULL`。  
  
 `file`  
 [in][IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件，表示要在其中搜尋原始程式檔。 這個參數不可以是 `NULL`。  
  
 `linenum`  
 [in]指定以一為基的行號。  
  
> [!NOTE]
> 您無法使用零來指定所有行 (使用[idiasession:: Findlines](../../debugger/debug-interface-access/idiasession-findlines.md)方法來尋找所有行)。  
  
 `column`  
 [in]指定的資料行編號。 使用指定的所有資料行的零。 資料行是一條線的位元組位移。  
  
 `ppResult`  
 [out]傳回[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)物件，其中包含一份已擷取的行號。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
