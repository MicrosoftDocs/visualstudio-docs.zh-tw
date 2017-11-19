---
title: "MemoryTypeEnum |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db6a66f8d496c73d05e05fd2f5398998c0a72484
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
指定記憶體存取的類型。  
  
## <a name="syntax"></a>語法  
  
```C++  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>參數  
 `MemTypeCode`  
 存取只撰寫程式碼的記憶體。  
  
 `MemTypeData`  
 存取資料或堆疊記憶體。  
  
 `MemTypeStack`  
 存取只堆疊記憶體。  
  
 `MemTypeAny`  
 存取任何種類的記憶體。  
  
## <a name="remarks"></a>備註  
 這個列舉型別中的值會傳遞至[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)方法，以限制存取不同類型的記憶體。  
  
## <a name="requirements"></a>需求  
 標頭： cvconst.h  
  
## <a name="see-also"></a>另請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)