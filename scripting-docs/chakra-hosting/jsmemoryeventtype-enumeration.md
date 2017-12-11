---
title: "JsMemoryEventType 列舉 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsMemoryEventType
helpviewer_keywords: JsMemoryEventType enumeration
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef39008ba84337cebdc9613db17cc9fbdfc8aa79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="jsmemoryeventtype-enumeration"></a>JsMemoryEventType 列舉
配置回呼事件類型。  
  
## <a name="syntax"></a>語法  
  
```  
enum JsMemoryEventType;  
```  
  
## <a name="members"></a>Members  
  
### <a name="values"></a>值  
  
|名稱|說明|  
|----------|-----------------|  
|`JsMemoryAllocate`|表示記憶體配置的要求。|  
|`JsMemoryFailure`|表示失敗的配置事件。|  
|`JsMemoryFree`|表示記憶體釋放事件。|  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)