---
title: 'Idiadatasource:: Get_lasterror |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08d17e0532d4d5d987d69afa7de062a193371950
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
擷取最後一個載入錯誤的檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 pRetVal  
 [out]傳回包含與前次載入錯誤相關聯的.pdb 檔案名稱的字串。  
  
## <a name="return-value"></a>傳回值  
 傳回負載作業所導致的最後一個錯誤碼。 傳回`E_INVALIDARG`如果`pRetVal`參數是`NULL`。  
  
## <a name="example"></a>範例  
  
```C++  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)