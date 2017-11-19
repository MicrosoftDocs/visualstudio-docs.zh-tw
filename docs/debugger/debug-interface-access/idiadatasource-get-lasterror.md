---
title: "Idiadatasource:: Get_lasterror |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 349477bed67450e897ec60a00635fb65442eb1ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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