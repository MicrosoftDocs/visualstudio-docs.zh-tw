---
title: m_children 欄位 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f8ea4f053d28ea14c05a50e3bc187faf6f6e207
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966851"
---
# <a name="mchildren-field"></a>m_children field
使用這項工作中註冊的子工作的清單。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib (在*mscorlib.dll*)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```csharp 
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>備註  
 當工作執行時，只有執行工作的執行緒應該存取此陣列。  
  
 如果工作已完成，其他執行緒可以存取這個欄位，只要它們不將任何項目新增至其中或從中移除任何項目。  
  
## <a name="see-also"></a>另請參閱  
 [ContingentProperties 類別](../../extensibility/debugger/contingentproperties-class-internal-members.md)