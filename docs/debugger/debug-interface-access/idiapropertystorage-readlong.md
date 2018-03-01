---
title: "IDiaPropertyStorage::ReadLONG |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fca0d07dab3559bbd806a6eb5a34b2a9dbe466eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
讀取`LONG`屬性集合中的值。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 [in]要讀取之屬性的識別項 (`PROPID`定義為在 WTypes.h 中`ULONG`)。  
  
 `pValue`  
 [out]傳回屬性值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_INVALIDARG`如果屬性不是類型`LONG`。  
  
## <a name="remarks"></a>備註  
 A`LONG`由 Windows，做為 32 位元帶正負號的整數所定義。  
  
## <a name="see-also"></a>請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)