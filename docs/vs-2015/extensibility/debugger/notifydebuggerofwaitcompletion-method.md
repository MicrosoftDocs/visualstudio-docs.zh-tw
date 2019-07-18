---
title: NotifyDebuggerOfWaitCompletion 方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0548e1e791c41d806ccc222176ee571b037389
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153733"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion 方法
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用做為中斷點目標偵錯工具的預留位置方法。 這個方法不能內嵌或最佳化。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll 中)  
  
## <a name="syntax"></a>語法  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>備註  
 如果已設定其偵錯工具通知位元，與工作的所有聯結作業應該都呼叫這個方法。  
  
## <a name="requirements"></a>需求  
  
## <a name="see-also"></a>另請參閱  
 [Task 類別](../../extensibility/debugger/task-class-internal-members.md)
