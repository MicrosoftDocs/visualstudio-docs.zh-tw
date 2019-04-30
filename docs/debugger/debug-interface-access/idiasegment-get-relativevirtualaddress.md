---
title: IDiaSegment::get_relativeVirtualAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_relativeVirtualAddress method
ms.assetid: b6a573a1-3671-4c1c-a5c2-2ab8f07fd510
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6387b4e7cbf3ab100b641fe8694505c5e326fc8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827679"
---
# <a name="idiasegmentgetrelativevirtualaddress"></a>IDiaSegment::get_relativeVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取區段開頭的相對虛擬位址 (RVA)。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回區段開頭的 RVA。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
