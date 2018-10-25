---
title: IDiaSession::findInlineFramesByAddr |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e7dc1ac7-bb09-45be-96d2-365a9b7336e4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 237fdb31b223db1434ec4a2c936ed956e8e339d7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899171"
---
# <a name="idiasessionfindinlineframesbyaddr"></a>IDiaSession::findInlineFramesByAddr
擷取列舉型別，可讓用戶端來逐一查看所有指定的位址上的內嵌框架。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findInlineFramesByAddr (   
   IDiaSymbol*       parent,   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `parent`  
 [in]`IDiaSymbol`物件表示父代。  
  
 `isect`  
 [in]指定位址的區段元件。  
  
 `offset`  
 [in]指定的位址位移的元件。  
  
 `ppResult`  
 [out]保存`IDiaEnumSymbols`物件，其中包含所擷取的畫面格的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)