---
title: 'Idiainjectedsource:: Get_objectfilename |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_objectFilename method
ms.assetid: 7c42847a-f0df-443a-a9fe-c495c1271ea8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98ec28996a217c2472a992fa44bed228a147987f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949426"
---
# <a name="idiainjectedsourcegetobjectfilename"></a>IDiaInjectedSource::get_objectFilename
擷取來源已編譯的物件檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_objectFilename (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回來源已編譯的物件檔案名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)