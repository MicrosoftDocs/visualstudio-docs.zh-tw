---
title: "實作和登錄連接埠提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [偵錯 SDK]，請註冊連接埠供應商"
  - "連接埠供應商註冊"
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 實作和登錄連接埠提供者
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

連接埠提供者的角色是追蹤，並提供連接埠，依序管理處理程序。  您必須建立一個連接埠時，連接埠提供者使用執行個體化 CoCreate \(工作階段偵錯管理員 \[SDM\] 會使用連接埠提供者選取的使用者或由專案系統所指定的連接埠提供者\) 的連接埠提供者的 guid。  SDM 會再呼叫[CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) ，查看是否可以加入任何連接埠。  如果可以加入一個連接埠，要求新的連接埠時藉由呼叫[下列](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) ，並將它傳遞[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) ，告訴您，連接埠。  `AddPort`會傳回新的連接埠，由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)介面。  
  
## 討論  
 建立一個連接埠的連接埠提供者，也就是依序關聯到電腦或偵錯的伺服器。  伺服器可以列舉透過其通訊埠供應商[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)方法，以及連接埠提供者可以列舉透過連接埠[EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)方法。  
  
 除了一般的 COM 登錄中，連接埠提供者必須登錄 Visual Studio 藉由在特定的登錄位置中放置它的 CLSID 和名稱。  偵錯的 SDK helper 函式呼叫`SetMetric`處理這項作業： 它會呼叫一次註冊，因此每一個項目：  
  
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
  
 連接埠提供者會移除註冊本身藉由呼叫`RemoveMetric` \(另一個偵錯的 SDK helper 函式\) 已登錄，因此每一個項目一次：  
  
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
>  [SDK 協助程式進行偵錯](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric`和`RemoveMetric`都是靜態函式，在 dbgmetric.h 中定義，而且在編譯成 ad2de.lib。  `metrictypePortSupplier`， `metricCLSID`，以及 `metricName` dbgmetric.h 中也有定義的協助程式。  
  
 連接埠提供者可以透過方法提供它的名稱和 GUID [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)和[GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md)，分別。  
  
## 請參閱  
 [實作連接埠提供者](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [SDK 協助程式進行偵錯](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [連接埠供應商](../../extensibility/debugger/port-suppliers.md)