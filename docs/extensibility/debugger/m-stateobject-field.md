---
title: m_stateObject 欄位 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fbd5404f7138fd2f98d56d63089acdb2afdad9f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850199"
---
# <a name="mstateobject-field"></a>m_stateObject 欄位
物件，表示該動作將會使用的資料。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib (在*mscorlib.dll*)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>備註  
 這是`state`中的參數<xref:System.Threading.Tasks.Task.%23ctor%2A>建構函式。 它也是支援欄位<xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName>屬性。  
  
## <a name="see-also"></a>另請參閱  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)