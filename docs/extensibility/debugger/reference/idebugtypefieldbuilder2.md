---
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5fe9f0ba0182662a429cd7003caca5c48288309
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955267"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
擴充**IDebugTypeFieldBuilder**能夠建立陣列的型別。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder  
```  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面可以取自符號提供者。  
  
## <a name="methods"></a>方法  
 上的方法除了[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|建立指定的類型和大小的陣列。|  
  
## <a name="requirements"></a>需求  
 標頭：Sh.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll