---
title: "m_stateObject 欄位 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85e8648fd757c6cdb7910123b3cd861f7abb3371
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="mstateobject-field"></a>m_stateObject 欄位
物件，表示動作會使用的資料。  
  
 **命名空間：**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>備註  
 這是`state`中的參數<xref:System.Threading.Tasks.Task.%23ctor%2A>建構函式。 它也是支援欄位的<xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName>屬性。  
  
## <a name="see-also"></a>另請參閱  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)