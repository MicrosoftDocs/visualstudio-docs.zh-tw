---
title: "Idiasession:: Findfilebyid |Microsoft 文件"
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
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 176e6a482212ee0cb6531d558e2b322ce4bec2d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
擷取的原始程式檔的原始檔識別項。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `uniqueId`  
 [in]指定原始檔識別項。  
  
 `ppResult`  
 [out]傳回[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)擷取代表來源檔案的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 原始檔識別項是 DIA sdk 在內部用來使所有原始程式檔的唯一的唯一值。 這個方法通常是在內部用來 DIA SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasession:: Findfile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)