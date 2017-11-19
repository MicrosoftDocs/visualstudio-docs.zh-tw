---
title: "SetNotificationForWaitCompletion 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 385ae98e90d8f3a466c0983405c367347bb8ca10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion 方法
設定或清除 TASK_STATE_WAIT_COMPLETION_NOTIFICATION 狀態位元。  
  
 **命名空間：**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll)  
  
## <a name="syntax"></a>語法  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>參數  
 `enabled`  
  
 `true`若要設定的位元。`false`為未設定位元。  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 偵錯工具設定此位元，以協助逐步從非同步方法的本文。 如果`enabled`是`true`，必須只能在尚未完成的工作上呼叫這個方法。 如果`enabled`是`false`，可能已完成的工作上呼叫這個方法。 在可能情況下，它應該只用於承諾樣式的工作。  
  
## <a name="requirements"></a>需求  
  
## <a name="see-also"></a>另請參閱  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)