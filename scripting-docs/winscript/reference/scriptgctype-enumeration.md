---
title: SCRIPTGCTYPE 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f28e0ddd3764b3810d25bfbb9403c391c1bfd54
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238448"
---
# <a name="scriptgctype-enumeration"></a>SCRIPTGCTYPE 列舉
要執行的垃圾收集類型。 用於 [IActiveScriptGarbageCollector：： CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) 方法中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>列舉值  
  
|值|垃圾收集類型|  
|-|-|  
|SCRIPTGCTYPE_NORMAL|執行一般垃圾收集。 整數值為0。|  
|SCRIPTGCTYPE_EXHAUSTIVE|執行徹底的垃圾收集。 整數值是1。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)