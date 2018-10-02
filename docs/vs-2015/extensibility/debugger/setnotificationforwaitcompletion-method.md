---
title: SetNotificationForWaitCompletion 方法 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b1443bbbd49216330d1df9978052bf4d10f7157
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484738"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion 方法
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[SetNotificationForWaitCompletion 方法](https://docs.microsoft.com/visualstudio/extensibility/debugger/setnotificationforwaitcompletion-method)。  
  
設定或清除 TASK_STATE_WAIT_COMPLETION_NOTIFICATION 狀態位元。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll 中)  
  
## <a name="syntax"></a>語法  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>參數  
 `enabled`  
  
 `true` 若要設定的位元;`false`為未設定此位元。  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 偵錯工具設定此位元，以協助從非同步方法主體中的步驟。 如果`enabled`是`true`，必須只能在尚未完成的工作上呼叫這個方法。 如果`enabled`是`false`，可能會在 已完成的工作上呼叫這個方法。 在可能情況下，它應該只用於承諾樣式工作。  
  
## <a name="requirements"></a>需求  
  
## <a name="see-also"></a>另請參閱  
 [Task 類別](../../extensibility/debugger/task-class-internal-members.md)

