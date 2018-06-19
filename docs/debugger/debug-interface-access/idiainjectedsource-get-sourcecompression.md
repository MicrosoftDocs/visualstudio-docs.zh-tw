---
title: 'Idiainjectedsource:: Get_sourcecompression |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: a56d1eac34c5076be8dbcd7b4e38363a12fe392f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457874"
---
# <a name="idiainjectedsourcegetsourcecompression"></a>IDiaInjectedSource::get_sourceCompression
擷取來源壓縮用於的指標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回來源使用的壓縮指標。 零值，指出沒有來源已使用壓縮。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法所傳回的值是使用編譯器專有的。 例如，編譯器可能會使用執行長度編碼方式編碼或 Huffman 樣式壓縮。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)