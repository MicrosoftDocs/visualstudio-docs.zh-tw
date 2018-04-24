---
title: LocationType |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb46eb1c7477f93ed63dfc4424d881886c8d0c8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="locationtype"></a>LocationType
表示包含在符號中的位置資訊的種類。  
  
## <a name="syntax"></a>語法  
  
```C++  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>項目  
 `LocIsNull`  
 無法使用位置資訊。  
  
 `LocIsStatic`  
 位置是靜態的。  
  
 `LocIsTLS`  
 位置是在執行緒區域儲存區中。  
  
 `LocIsRegRel`  
 位置是暫存器的相對位置。  
  
 `LocIsThisRel`  
 位置是`this`-相對。  
  
 `LocIsEnregistered`  
 位置是在暫存器。  
  
 `LocIsBitField`  
 位置是位元欄位。  
  
 `LocIsSlot`  
 位置是 Microsoft Intermediate Language (MSIL) 位置。  
  
 `LocIsIlRel`  
 位置是相對的 MSIL。  
  
 `LocInMetaData`  
 位置是在中繼資料。  
  
 `LocIsConstant`  
 位置是常數值。  
  
 `LocTypeMax`  
 此列舉中的位置類型數目。  
  
## <a name="remarks"></a>備註  
 可用的內容[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)介面的影像檔中的符號的位置而定。 如需詳細資訊，請參閱[符號位置](../../debugger/debug-interface-access/symbol-locations.md)。  
  
 這個列舉型別中的值會傳回透過呼叫[idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)