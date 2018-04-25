---
title: 'Idiaenumlinenumbers:: Get__newenum |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::get__NewEnum method
ms.assetid: 8b15f76b-a431-4f60-8bed-3206256b0d10
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5da5277fad1ca0183a9f397a80e84871a120c147
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumlinenumbersgetnewenum"></a>IDiaEnumLineNumbers::get__NewEnum
擷取<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>這個列舉值的版本。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 pRetVal  
 [out]傳回`IUnknown`表示介面<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>這個列舉值的版本。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)