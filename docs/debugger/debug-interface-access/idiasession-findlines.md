---
title: 'Idiasession:: Findlines |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2dc5e2509e3edda0c9cd89b84a3e109e0ac2d0e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828356"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
擷取指定的編譯模組和來源檔案識別碼內的行號。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `compiland`  
 [in][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示編譯的模組。 使用此介面做為內容，以在其中搜尋的行號。  
  
 `file`  
 [in][IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件，表示原始程式檔，在其中搜尋的行號。  
  
 `ppResult`  
 [out]傳回[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)擷取物件，其中包含一份的行號。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)