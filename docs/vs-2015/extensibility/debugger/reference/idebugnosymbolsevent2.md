---
title: IDebugNoSymbolsEvent2 |Microsoft Docs
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
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1dec7ef8a17a078bc94f41e3270f17ae2cb438a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499966"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugNoSymbolsEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugnosymbolsevent2)。  
  
訊號[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]偵錯工具 UI 來警告使用者符號找不到啟動可執行檔。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 藉由將偵錯引擎，而且由[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]UI 偵錯工具。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

