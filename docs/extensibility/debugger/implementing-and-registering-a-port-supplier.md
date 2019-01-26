---
title: 實作和註冊連接埠提供者 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e02c7e7ff030d2fd2bb9de86dfd1e7211f8de1f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946707"
---
# <a name="implement-and-register-a-port-supplier"></a>實作並註冊連接埠提供者
連接埠提供者的角色是追蹤，並提供連接埠，進而管理程序。 當需要建立一個連接埠時，連接埠提供者會使用具現化 CoCreate （工作階段的偵錯管理員 [SDM] 會使用指定的專案系統在選取的使用者或連接埠提供者的連接埠供應商） 的連接埠提供者的 guid。 然後呼叫 SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)以查看是否可以加入任何連接埠。 如果可以加入一個連接埠，藉由呼叫要求新的連接埠[下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)並將其傳遞[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)描述連接埠。 `AddPort` 傳回新的連接埠，由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面。  
  
## <a name="discussion"></a>討論  
 連接埠會建立與電腦或偵錯伺服器相關聯的連接埠供應商。 伺服器會列舉其透過的連接埠供應商[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)方法，以及連接埠提供者列舉其連接埠通過[EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)方法。  
  
 除了一般的 COM 註冊、 連接埠提供者必須將自己登錄與 Visual Studio 將其 CLSID 和名稱放在特定的登錄位置。 偵錯的 SDK 協助程式函式呼叫`SetMetric`處理這項作業： 它會呼叫一次進行註冊，因此每個項目：  
  
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
  
 連接埠提供者取消註冊本身呼叫`RemoveMetric`（另一個偵錯的 SDK 協助程式函式） 一次註冊，因此每個項目：  
  
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
>  [進行偵錯的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)`SetMetric`並`RemoveMetric`靜態函式定義於*dbgmetric.h*並編譯成*ad2de.lib*。 `metrictypePortSupplier`， `metricCLSID`，並`metricName`協助程式也會定義於*dbgmetric.h*。  
  
 連接埠提供者可以透過方法提供它的名稱和 GUID [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)並[GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)分別。  
  
## <a name="see-also"></a>另請參閱  
 [實作連接埠提供者](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [偵錯的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [連接埠提供者](../../extensibility/debugger/port-suppliers.md)