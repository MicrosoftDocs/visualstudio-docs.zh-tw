---
title: 'Idiainjectedsource:: Get_sourcecompression |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86679c1e97ab50f55e8f887d582e8d8b46a35ae7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912645"
---
# <a name="idiainjectedsourcegetsourcecompression"></a>IDiaInjectedSource::get_sourceCompression
擷取來源所用的壓縮的指標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回來源所用的壓縮的指標。 值為零表示已使用該沒有來源壓縮。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法所傳回的值是特定編譯器使用。 例如，編譯器可能會使用執行長度編碼方式編碼或 Huffman 式壓縮。  
  
## <a name="see-also"></a>請參閱  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)