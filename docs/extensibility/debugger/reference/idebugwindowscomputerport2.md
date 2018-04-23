---
title: IDebugWindowsComputerPort2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d7482adf6405d04522cbc3137be25c7a5e18b2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
可讓目標電腦的相關資訊的查詢。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 實作這個介面是由偵錯工作階段管理員的連接埠物件。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugWindowsComputerPort2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|擷取電腦的相關資訊的偵錯工具中執行。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll