---
title: IDebugPrimitiveTypeField |Microsoft Docs
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
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e27680fee38732eea740f11b66e768c9348af1b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485945"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugPrimitiveTypeField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprimitivetypefield)。  
  
表示基本類型列舉值從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPrimitiveTypeField : IDebugField  
```  
  
## <a name="methods"></a>方法  
 上的方法除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|擷取這個欄位相關聯的基本類型。|  
  
## <a name="requirements"></a>需求  
 標頭： Sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

