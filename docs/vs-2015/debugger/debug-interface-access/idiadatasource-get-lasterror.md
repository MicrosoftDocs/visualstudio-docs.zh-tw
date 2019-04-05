---
title: 'Idiadatasource:: Get_lasterror |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3ad0570436dda6ac9ae52325c891b32a563cf6f7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943938"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取最後一個載入錯誤的檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 pRetVal  
 [out]傳回包含與最後一個載入錯誤相關聯的.pdb 檔案名稱的字串。  
  
## <a name="return-value"></a>傳回值  
 傳回載入作業所造成的最後一個錯誤碼。 傳回`E_INVALIDARG`如果`pRetVal`參數是`NULL`。  
  
## <a name="example"></a>範例  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
