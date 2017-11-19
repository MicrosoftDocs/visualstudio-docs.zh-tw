---
title: "IActiveScriptGarbageCollector::CollectGarbage |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07d5a00e04939331f85c4c74727aaf03b62814fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
使用中指令碼主機會呼叫此方法來開始記憶體回收。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>參數  
 `scriptgctype`  
 [in][SCRIPTGCTYPE 列舉](../../winscript/reference/scriptgctype-enumeration.md)，指定要執行標準或完整記憶體回收。  
  
## <a name="return-value"></a>傳回值  
 會傳回 HRESULT。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptGarbageCollector 介面](../../winscript/reference/iactivescriptgarbagecollector-interface.md)