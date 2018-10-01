---
title: 實作和註冊連接埠提供者 |Microsoft Docs
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
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe8e5cac0b1737d7c3dbd7e9301e0ca25d778db4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497874"
---
# <a name="implementing-and-registering-a-port-supplier"></a>實作和註冊連接埠提供者
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[實作和註冊連接埠供應商](https://docs.microsoft.com/visualstudio/extensibility/debugger/implementing-and-registering-a-port-supplier)。  
  
連接埠提供者的角色是追蹤，並提供連接埠，進而管理程序。 您必須建立一個連接埠時，連接埠提供者具現化 CoCreate 使用連接埠提供者的 GUID （連接埠提供者選取的使用者或專案系統所指定的連接埠提供者，將會使用工作階段的偵錯管理員 [SDM]）。 會接著呼叫 SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)以查看是否可以加入任何連接埠。 如果可以加入一個連接埠，藉由呼叫要求新的連接埠[下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)並將其傳遞[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)描述連接埠。 `AddPort` 會傳回新的連接埠，由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面。  
  
## <a name="discussion"></a>討論  
 依序相關聯的機器或偵錯伺服器連接埠供應商提供的被建立連接埠。 伺服器可以列舉透過其通訊埠供應商[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)方法，以及連接埠提供者可以列舉它的連接埠，透過[EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)方法。  
  
 除了一般的 COM 註冊、 連接埠提供者必須將自己登錄與 Visual Studio 將其 CLSID 和名稱放在特定的登錄位置。 偵錯的 SDK 協助程式函式呼叫`SetMetric`處理這項作業： 它會呼叫一次進行註冊，因此每個項目：  
  
```cpp#  
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
  
```cpp#  
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
>  [SDK 協助程式進行偵錯](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)`SetMetric`和`RemoveMetric`dbgmetric.h 中定義，並編譯成 ad2de.lib 的靜態函數。 `metrictypePortSupplier`， `metricCLSID`，和`metricName`dbgmetric.h 中也會定義協助程式。  
  
 連接埠提供者可以透過方法提供它的名稱和 GUID [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)並[GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)分別。  
  
## <a name="see-also"></a>另請參閱  
 [實作連接埠提供者](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [偵錯的 SDK 協助程式](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [連接埠提供者](../../extensibility/debugger/port-suppliers.md)

