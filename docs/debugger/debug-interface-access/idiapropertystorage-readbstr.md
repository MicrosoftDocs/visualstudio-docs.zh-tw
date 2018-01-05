---
title: "IDiaPropertyStorage::ReadBSTR |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7c8fc8520791228158ad336a7bb709cdbf83a5dc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
讀取`BSTR`屬性集合中的值。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 [in]要讀取之屬性的識別項 (`PROPID`定義為在 WTypes.h 中`ULONG`)。  
  
 `pValue`  
 [out]傳回屬性值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_INVALIDARG`如果屬性不是類型`BSTR`。  
  
## <a name="remarks"></a>備註  
 A `BSTR` Windows 所定義的以零結尾的寬字元字串。  
  
## <a name="see-also"></a>請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)