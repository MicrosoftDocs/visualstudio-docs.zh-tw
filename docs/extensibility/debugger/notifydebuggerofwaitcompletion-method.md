---
title: "NotifyDebuggerOfWaitCompletion 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bfd605665627bcc9269f9225acb7d2e12418ab4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion 方法
預留位置方法作為偵錯工具的中斷點目標。 這個方法不能內嵌或最佳化。  
  
 **命名空間：**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll)  
  
## <a name="syntax"></a>語法  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>備註  
 如果已設定其偵錯工具通知位元，與工作的所有聯結作業應該都呼叫這個方法。  
  
## <a name="requirements"></a>需求  
  
## <a name="see-also"></a>另請參閱  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)