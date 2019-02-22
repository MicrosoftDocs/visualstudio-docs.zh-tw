---
title: IDiaEnumSegments::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e9e1632fa9031dc502cce6467e60e76d30bf874
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999037"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
透過索引中擷取的區段。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Item (   
   DWORD         index,  
   IDiaSegment** segment  
);  
```  
  
#### <a name="parameters"></a>參數  
 索引  
 [in]索引[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)要擷取的物件。 索引是在範圍介於 0 到`count`-1，其中`count`會傳回[idiaenumsegments:: Get_count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)方法。  
  
 segment  
 [out]傳回[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)物件，表示所需的區段。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)