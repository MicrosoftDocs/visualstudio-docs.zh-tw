---
title: m_stateObject 欄位 |Microsoft 文件
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
ms.openlocfilehash: 79313460d380b2b505f6fa75f35351811ddaa470
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31097455"
---
# <a name="mstateobject-field"></a>m_stateObject 欄位
物件，表示動作會使用的資料。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
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