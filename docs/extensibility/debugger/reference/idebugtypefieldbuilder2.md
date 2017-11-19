---
title: "IDebugTypeFieldBuilder2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cee126ad63e0a50ec2b859c470c06a4f2ae07600
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
擴充**IDebugTypeFieldBuilder**能夠建立陣列類型。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder  
```  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面可以取自符號提供者。  
  
## <a name="methods"></a>方法  
 除了上[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)介面，這個介面會實作下列方法：  
  
|方法|說明|  
|------------|-----------------|  
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|建立指定的類型和大小的陣列。|  
  
## <a name="requirements"></a>需求  
 標頭： Sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll