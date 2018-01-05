---
title: "IDiaPropertyStorage::ReadDWORD |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b6389e5bf2a4df5a407b57be077134066803d33d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
讀取`DWORD`屬性集合中的值。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 [in]要讀取之屬性的識別項 (`PROPID`定義為在 WTypes.h 中`ULONG`)。  
  
 `pValue`  
 [out]傳回屬性值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_INVALIDARG`如果屬性不是類型`DWORD`。  
  
## <a name="remarks"></a>備註  
 A`DWORD`由 Windows，做為 32 位元不帶正負號的整數所定義。  
  
## <a name="see-also"></a>請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)