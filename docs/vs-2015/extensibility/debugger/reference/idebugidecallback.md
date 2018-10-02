---
title: IDebugIDECallback |Microsoft Docs
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
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec4e3fee021b02c80b47635d4872ec1bf51e0cc9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484933"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugIDECallback](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugidecallback)。  
  
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 可讓運算式評估工具 (EE)，才能偵錯工具的 [輸出] 視窗中顯示一則訊息。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 此回呼是由 managed 偵錯引擎實作。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 它可供將輸出傳送至偵錯工具的 [輸出] 視窗的運算式評估工具。  
  
## <a name="methods"></a>方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|將指定的訊息字串傳送至偵錯工具的 [輸出] 視窗中。|  
  
## <a name="requirements"></a>需求  
 標頭： Ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

