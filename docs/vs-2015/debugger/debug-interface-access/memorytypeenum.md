---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ded136da4d601fd7c11a10c21aac0c90864bc0bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158122"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定要存取記憶體的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>參數  
 `MemTypeCode`  
 存取僅限程式碼的記憶體。  
  
 `MemTypeData`  
 存取資料或堆疊記憶體。  
  
 `MemTypeStack`  
 存取僅堆疊記憶體。  
  
 `MemTypeAny`  
 存取任何種類的記憶體。  
  
## <a name="remarks"></a>備註  
 這個列舉型別中的值會傳遞至[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)方法，以限制存取不同類型的記憶體。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
