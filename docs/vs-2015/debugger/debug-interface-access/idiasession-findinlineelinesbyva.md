---
title: IDiaSession::findInlineeLinesByVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6b400c3483d200c6073eb4e75cf393a643e39e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68165566"
---
# <a name="idiasessionfindinlineelinesbyva"></a>IDiaSession::findInlineeLinesByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取列舉型別，可讓用戶端來逐一查看所有函式是內嵌的直接或間接由指定之父代符號的行號資訊，而且包含在指定的虛擬位址 (VA)。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           parent,   ULONGLONG             va,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `parent`  
 [in]`IDiaSymbol`物件表示父代。  
  
 `va`  
 [in]指定的位址為瑞斯  
  
 `length`  
 [in]指定位址範圍中涵蓋此查詢使用的位元組數目。  
  
 `ppResult`  
 [out]保存`IDiaEnumLineNumbers`物件，其中包含所擷取的行號的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
