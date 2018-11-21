---
title: 'Idiadatasource:: Get_lasterror |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abbca721d97db3fd33c6dd3ab13b1f9859156187
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771062"
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



