---
title: m_children 欄位 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f044c2dae278a0656f1f9e4c41a3940d87658a64
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731035"
---
# <a name="mchildren-field"></a>m_children 欄位
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用這項工作中註冊的子工作的清單。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件：** mscorlib （在 mscorlib.dll 中)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。  
  
## <a name="syntax"></a>語法  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>備註  
 當工作執行時，只有執行工作的執行緒應該存取此陣列。  
  
 如果工作已完成，其他執行緒可以存取這個欄位，只要它們不將任何項目新增至其中或從中移除任何項目。  
  
## <a name="see-also"></a>另請參閱  
 [ContingentProperties 類別](../../extensibility/debugger/contingentproperties-class-internal-members.md)

