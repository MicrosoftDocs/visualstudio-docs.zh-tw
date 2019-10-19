---
title: APPLICATION_NODE_EVENT_FILTER 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- APPLICATION_NODE_EVENT_FILTER Constants
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 481e015ec84d833f52220276bffa4ce0163f98ff
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572656"
---
# <a name="application_node_event_filter-enumeration"></a>APPLICATION_NODE_EVENT_FILTER 列舉
指定篩選程式代碼檔時要排除的節點類型。 用於[IDebugApplicationNode100：： GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)和[IDebugApplicationNode100：： SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> 這些常數是由 PDM 10.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {    FILTER_EXCLUDE_NOTHING = 0,    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,    FILTER_EXCLUDE_EVAL_CODE = 0x2} APPLICATION_NODE_EVENT_FILTER;  
```  
  
## <a name="members"></a>Members  
  
|成員|值|描述|  
|------------|-----------|-----------------|  
|FILTER_EXCLUDE_NOTHING|0x00000000|傳送所有事件。|  
|FILTER_EXCLUDE_ANONYMOUS_CODE|0x00000001|排除匿名程式碼節點。 @No__t_0 的 JScript 執行時間會使用這些節點。|  
|FILTER_EXCLUDE_EVAL_CODE|0x00000002|排除 eval 程式碼節點。 JScript 執行時間會使用這些節點來評估支援。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)