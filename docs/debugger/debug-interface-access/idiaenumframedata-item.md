---
title: 'Idiaenumframedata:: Item |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96dce9ab3853964be7ce88c6327fa7f180933ba9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
透過索引擷取的畫面格的資料元素。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>參數  
 索引  
 [in]索引的[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)要擷取的物件。 索引是在 0 到`count`-1，其中`count`傳回[idiaenumframedata:: Get_count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)方法。  
  
 section  
 [out]傳回[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件，代表所要的畫面格的資料元素。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)