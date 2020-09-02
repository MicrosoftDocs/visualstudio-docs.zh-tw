---
title: IDiaPropertyStorage：： ReadULONGLONG |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6da509e226a612e80a10ca0759b5e264f31a1e13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538665"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

讀取 `ULONGLONG` 屬性集中的值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 在要讀取之屬性的識別碼 (`PROPID` 在 wtypes.h 中定義為 `ULONG`) 。  
  
 `pValue`  
 擴展傳回屬性值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 `E_INVALIDARG`如果屬性不是型別，則會傳回 `ULONGLONG` 。  
  
## <a name="remarks"></a>備註  
 `ULONGLONG`由 Windows 定義為64位不帶正負號的整數。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
