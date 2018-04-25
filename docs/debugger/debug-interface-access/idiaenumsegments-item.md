---
title: 'Idiaenumsegments:: Item |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64089113f0ad5b0e3fea0189a5dc3bf680213158
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
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
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)