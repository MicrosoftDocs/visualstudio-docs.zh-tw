---
title: IDebugTypeFieldBuilder |Microsoft Docs
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
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e88ab51bd6af9b2b1741d00d7097a9b07baa5c15
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487066"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugTypeFieldBuilder](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugtypefieldbuilder)。  
  
表示建立的欄位，表示類型的能力。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugTypeFieldBuilder : IUnknown  
```  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面被取自符號提供者。  
  
## <a name="methods"></a>方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|建立表示基本類型的物件。|  
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|建立指定類型的指標。|  
  
## <a name="requirements"></a>需求  
 標頭： Sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

