---
title: IDiaPropertyStorage::ReadPropertyNames |Microsoft Docs
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
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4dd1027d5921af482a71c7c45e5b6c90599df512
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232826"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取對應的字串名稱指定屬性識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cpropid`  
 [in]中的屬性識別碼的數目`rgpropid`。  
  
 `rgpropid`  
 [in]要取得名稱的屬性識別碼的陣列 (`PROPID`定義為 WTypes.h 中`ULONG`)。  
  
 `rglpwstrName`  
 [in、 out]指定的屬性識別碼的屬性名稱的陣列。 陣列必須預先配置來保存屬性名稱的要求的數目，而且必須能夠容納至少`cpropid``BSTR`字串。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 傳回的屬性名稱，必須釋放 (藉由呼叫`SysFreeString`函式) 在不再需要時。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)



