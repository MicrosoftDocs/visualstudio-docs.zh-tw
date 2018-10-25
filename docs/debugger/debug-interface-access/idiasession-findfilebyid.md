---
title: 'Idiasession:: Findfilebyid |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c56d66a78b52e99aecb8cb744cc3d8465d0d243
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941408"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
依來源檔案識別碼擷取原始程式檔。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `uniqueId`  
 [in]指定來源檔案識別碼。  
  
 `ppResult`  
 [out]傳回[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)擷取代表原始程式檔的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 DIA sdk 在內部用來進行所有原始程式檔的唯一唯一值的來源檔案識別碼。 這個方法通常是在內部用來 DIA SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasession:: Findfile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)