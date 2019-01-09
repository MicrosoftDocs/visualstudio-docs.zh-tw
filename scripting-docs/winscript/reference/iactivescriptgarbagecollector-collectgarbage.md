---
title: IActiveScriptGarbageCollector::CollectGarbage |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 478a7a39c69e0c2106e3c6cc308f44f8f7aa3201
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097119"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
動態指令碼主機會呼叫此方法以啟動記憶體回收。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>參數  
 `scriptgctype`  
 [in][SCRIPTGCTYPE 列舉](../../winscript/reference/scriptgctype-enumeration.md)，指定是否要執行標準或完整記憶體回收。  
  
## <a name="return-value"></a>傳回值  
 會傳回 HRESULT。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptGarbageCollector 介面](../../winscript/reference/iactivescriptgarbagecollector-interface.md)