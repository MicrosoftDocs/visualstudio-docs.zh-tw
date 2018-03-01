---
title: "Idiaenumsegments:: Item |Microsoft 文件"
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
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bbb2aeef0fe2bb6e5d844dac61c43ce0c4d67a73
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
擷取透過索引的區段。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Item (   
   DWORD         index,  
   IDiaSegment** segment  
);  
```  
  
#### <a name="parameters"></a>參數  
 索引  
 [in]索引的[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)要擷取的物件。 索引是在 0 到`count`-1，其中`count`傳回[idiaenumsegments:: Get_count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)方法。  
  
 區段  
 [out]傳回[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)物件，代表所需的區段。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)