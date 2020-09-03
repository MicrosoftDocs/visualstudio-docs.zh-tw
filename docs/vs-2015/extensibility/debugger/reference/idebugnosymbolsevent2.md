---
title: IDebugNoSymbolsEvent2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d36b1091f34318ccba1ce0a997ad23043cbdeb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155569"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

通知 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 偵錯工具 UI 警告使用者，找不到已啟動可執行檔的符號。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 由偵錯工具 UI 所執行，並由調試 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 程式 UI 使用。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll
