---
title: IDebugDefaultPort2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca0b6b7e9753b346b8a995ffd8ddcb6cc53fe7c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697520"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面提供數種存取埠伺服器和通知設備的方法。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Visual Studio 會執行此介面來代表用來存取程式的 debug 埠。 如果自訂埠供應商處理遠端偵錯，也可以執行這個介面。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)介面上方法的引數會提供這個介面。 在[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面上呼叫[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)也可以取得這個介面。  
  
## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法  
 除了 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)中定義的方法之外，這個介面也會執行下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|從這個埠取得埠通知介面。|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|取得裝載此埠之伺服器的介面。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|判斷此埠是否正在本機電腦上執行。|  
  
## <a name="remarks"></a>備註  
 名稱 " `IDebugDefaultPort2` " 有點 misnomer，因為它不代表預設埠。 它可能稱為「IDebugPort3」。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
