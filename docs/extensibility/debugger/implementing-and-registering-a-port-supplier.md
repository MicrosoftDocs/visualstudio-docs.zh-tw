---
title: 實作並註冊一個連接埠的供應商 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54d6a4ab90b5ad169c5c940f52322dfd9b4974a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-and-registering-a-port-supplier"></a>實作並註冊一個連接埠的供應商
連接埠供應商的角色是追蹤，並提供連接埠，接著管理處理程序。 您必須建立一個連接埠時，連接埠提供者具現化 CoCreate 使用連接埠供應商的 GUID （工作階段的偵錯管理員 [SDM] 將會使用連接埠供應商使用者選取或專案系統所指定的連接埠供應商）。 然後會呼叫 SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)以查看是否可以新增任何連接埠。 如果可以加入一個連接埠，藉由呼叫要求新的連接埠[下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)並將其傳遞[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)描述連接埠。 `AddPort` 會傳回新的連接埠由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面。  
  
## <a name="discussion"></a>討論  
 連接埠供應商，相關聯的電腦或偵錯伺服器接著會建立連接埠。 伺服器可以列舉透過其通訊埠供應商[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)方法，以及連接埠供應商可以列舉透過連接埠[EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)方法。  
  
 除了一般的 COM 登錄中，連接埠供應商必須向 Visual Studio 特定的登錄位置中放置其 CLSID 和名稱。 偵錯 sdk 》 helper 函式呼叫`SetMetric`處理這項作業： 它會呼叫一次進行註冊，因此每個項目：  
  
```cpp  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 連接埠供應商可取消登錄本身。 呼叫`RemoveMetric`（另一個偵錯 sdk 》 協助程式函式） 一次是針對已註冊，因此每個項目：  
  
```cpp  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
>  [SDK 進行偵錯的協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)`SetMetric`和`RemoveMetric`dbgmetric.h 中定義，並編譯成 ad2de.lib 的靜態函數。 `metrictypePortSupplier`， `metricCLSID`，和`metricName`dbgmetric.h 中也會定義協助程式。  
  
 連接埠供應商可以透過方法提供其名稱和 GUID [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)和[GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)分別。  
  
## <a name="see-also"></a>另請參閱  
 [實作連接埠供應商](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [SDK 進行偵錯的協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [連接埠提供者](../../extensibility/debugger/port-suppliers.md)