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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153733"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion 方法
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

偵錯工具用來當做中斷點目標的預留位置方法。 這個方法不得內嵌或優化。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **元件：** mscorlib.dll) 中的 mscorlib (  
  
## <a name="syntax"></a>語法  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>備註  
 如果已設定偵錯工具通知位，則所有具有工作的聯結作業都應該呼叫這個方法。  
  
## <a name="requirements"></a>需求  
  
## <a name="see-also"></a>另請參閱  
 [Task 類別](../../extensibility/debugger/task-class-internal-members.md)
