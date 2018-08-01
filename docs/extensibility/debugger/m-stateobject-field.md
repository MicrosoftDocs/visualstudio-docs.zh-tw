---
title: m_stateObject 欄位 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d33879ca8aaaba08288f9e16d54ab462d92f67b
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231313"
---
# <a name="mstateobject-field"></a>m_stateObject 欄位
物件，表示該動作將會使用的資料。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib (在*mscorlib.dll*)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>備註  
 這是`state`中的參數<xref:System.Threading.Tasks.Task.%23ctor%2A>建構函式。 它也是支援欄位<xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName>屬性。  
  
## <a name="see-also"></a>另請參閱  
 [Task 類別](../../extensibility/debugger/task-class-internal-members.md)