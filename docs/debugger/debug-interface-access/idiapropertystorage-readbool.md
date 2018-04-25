---
title: IDiaPropertyStorage::ReadBOOL |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a7ec4afc044af9d63fc65826e473d9036bf9ca3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
讀取`BOOL`屬性集合中的值。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 [in]要讀取之屬性的識別項 (`PROPID`定義為在 WTypes.h 中`ULONG`)。  
  
 `pValue`  
 [out]傳回屬性值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_INVALIDARG`如果屬性不是類型`BOOL`。  
  
## <a name="remarks"></a>備註  
 取得一致的結果，解譯`BOOL`值，使非零的值為`TRUE`零且`FALSE`。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)