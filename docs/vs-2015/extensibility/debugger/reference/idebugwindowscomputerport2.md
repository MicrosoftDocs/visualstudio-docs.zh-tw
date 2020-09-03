---
title: IDebugWindowsComputerPort2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd11e57c8e2ec03da1dcfa9ff76b3b3ec2ded5e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149311"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

允許查詢目的電腦的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 這個介面是由會話偵錯工具管理員的埠物件所執行。  
  
## <a name="methods"></a>方法  
 下表顯示的方法 `IDebugWindowsComputerPort2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|抓取正在執行之偵錯工具的電腦相關資訊。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll
