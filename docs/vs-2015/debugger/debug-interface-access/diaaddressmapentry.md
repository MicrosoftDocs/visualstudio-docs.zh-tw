---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 67c0a3e297f3eebfbf44724e64c4989d9bb979fb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943482"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

描述中對應的位址的項目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>項目  
 `rva`  
 在圖中 A.相對虛擬位址 (RVA)  
  
 `rvaTo`  
 相對虛擬位址`rva`會對應到像 b。  
  
## <a name="remarks"></a>備註  
 對應的位址會提供從一個映像版面配置的翻譯 （A） 到另一個 （B）。 陣列`DiaAddressMapEntry`依排序的結構`rva`定義對應的位址。  
  
 要轉譯為位址， `addrA`，在映像的位址， `addrB`，在圖 B 中，執行下列步驟：  
  
1. 搜尋的項目，對應`e`，具有最大`rva`小於或等於`addrA`。  
  
2. 設定 `delta = addrA – e.rva`。  
  
3. 設定 `addrB = e.rvaTo + delta`。  
  
   陣列`DiaAddressMapEntry`結構傳遞給[idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： dia2.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
