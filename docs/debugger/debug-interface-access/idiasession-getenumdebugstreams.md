---
title: 'Idiasession:: Getenumdebugstreams |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumDebugStreams method
ms.assetid: d294954b-80e9-476c-b9f0-5ca6fd575f68
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 00f9fe90b2c138fc4ca13940a186ecfedb20c9ee
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883992"
---
# <a name="idiasessiongetenumdebugstreams"></a>IDiaSession::getEnumDebugStreams
擷取偵錯資料流的列舉的順序。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT getEnumDebugStreams (   
   IDiaEnumDebugStreams** ppEnumDebugStreams  
)  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnumDebugStreams`  
 [out]傳回[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)物件，其中包含一份偵錯資料流。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)