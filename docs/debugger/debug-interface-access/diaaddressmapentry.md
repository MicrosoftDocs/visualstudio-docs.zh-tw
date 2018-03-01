---
title: "DiaAddressMapEntry |Microsoft 文件"
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
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2d6886ed55fbe8c48beabf81144a9551efa1a562
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
描述對應的位址中的項目。  
  
## <a name="syntax"></a>語法  
  
```C++  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>項目  
 `rva`  
 A.映像中相對虛擬位址 (RVA)  
  
 `rvaTo`  
 相對虛擬位址`rva`映像 b 中對應至  
  
## <a name="remarks"></a>備註  
 對應的位址會提供 （A） 到另一個 （B） 從一個映像配置翻譯。 陣列`DiaAddressMapEntry`結構依照`rva`定義對應的位址。  
  
 若要轉譯為位址， `addrA`，在映像的位址， `addrB`，在影像 B 中，執行下列步驟：  
  
1.  搜尋的項目，對應`e`，具有最大`rva`小於或等於`addrA`。  
  
2.  Set `delta = addrA - e.rva`.  
  
3.  Set `addrB = e.rvaTo + delta`.  
  
 陣列`DiaAddressMapEntry`結構傳遞至[idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： dia2.h  
  
## <a name="see-also"></a>請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)