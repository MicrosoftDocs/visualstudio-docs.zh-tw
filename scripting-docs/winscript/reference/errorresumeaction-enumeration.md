---
title: ERRORRESUMEACTION 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ERRORRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d78852a05226f5112447dd142c06a2ba55ddba5a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090931"
---
# <a name="errorresumeaction-enumeration"></a>ERRORRESUMEACTION 列舉
描述如何從執行階段錯誤繼續執行。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|重新執行陳述式產生錯誤。|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|可讓處理錯誤的語言引擎。|  
|ERRORRESUMEACTION_SkipErrorStatement|在程式碼中產生錯誤的陳述式之後繼續執行。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)