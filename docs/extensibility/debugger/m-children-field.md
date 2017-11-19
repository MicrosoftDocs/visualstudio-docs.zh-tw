---
title: "m_children 欄位 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e6c7db4e05873ca0272da4eb551418d466ddc03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="mchildren-field"></a>m_children 欄位
使用這項工作中註冊的子工作的清單。  
  
 **命名空間：**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>備註  
 執行工作時，執行工作的執行緒應該存取這個陣列。  
  
 如果工作已完成，其他執行緒可以存取此欄位，只要這些不加入任何項目，或從中移除任何項目。  
  
## <a name="see-also"></a>另請參閱  
 [ContingentProperties 類別](../../extensibility/debugger/contingentproperties-class-internal-members.md)