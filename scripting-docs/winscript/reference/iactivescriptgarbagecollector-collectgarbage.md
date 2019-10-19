---
title: IActiveScriptGarbageCollector：： CollectGarbage |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0539ed2cb3540cf33ceaaa15827c3ca08c156698
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573589"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
作用中腳本主機會呼叫這個方法，以開始垃圾收集。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>參數  
 `scriptgctype`  
 在指定是否要執行一般或完整垃圾收集的[SCRIPTGCTYPE 列舉](../../winscript/reference/scriptgctype-enumeration.md)。  
  
## <a name="return-value"></a>傳回值  
 傳回 HRESULT。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptGarbageCollector 介面](../../winscript/reference/iactivescriptgarbagecollector-interface.md)