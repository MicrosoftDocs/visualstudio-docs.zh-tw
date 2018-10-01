---
title: m_stateObject 欄位 |Microsoft Docs
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
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d062d8a052ec89401d8b801ad329ed55ac86eb89
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492244"
---
# <a name="mstateobject-field"></a>m_stateObject 欄位
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[m_stateObject 欄位](https://docs.microsoft.com/visualstudio/extensibility/debugger/m-stateobject-field)。  
  
物件，表示該動作將會使用的資料。  
  
 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll 中)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>備註  
 這是`state`中的參數<xref:System.Threading.Tasks.Task.%23ctor%2A>建構函式。 它也是支援欄位<xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName>屬性。  
  
## <a name="see-also"></a>另請參閱  
 [Task 類別](../../extensibility/debugger/task-class-internal-members.md)

