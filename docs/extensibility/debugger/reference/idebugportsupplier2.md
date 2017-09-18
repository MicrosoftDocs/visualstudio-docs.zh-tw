---
title: "IDebugPortSupplier2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2"
helpviewer_keywords: 
  - "IDebugPortSupplier2 介面"
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會提供給工作階段的偵錯專案經理 \(SDM\) 的連接埠。  
  
## 語法  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## 實作器注意事項  
 自訂的連接埠提供者會實作這個介面代表連接埠提供者。  
  
## 呼叫者的備忘稿  
 呼叫`CoCreateInstance`與連接埠提供者`GUID`會傳回這個介面 \(這是一般的方式，來取得這個介面\)。  例如：  
  
```cpp#  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 呼叫[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)會傳回這個介面，代表目前正在使用的連接埠提供者[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]。  
  
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)傳回這個介面，代表建立該連接埠的連接埠提供者。  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)表示一份`IDebugPortSupplier`介面 \( `IEnumDebugPortSuppliers`介面取自[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)，代表所有連接埠供應商註冊的[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]\)。  
  
 偵錯引擎通常不常使用的連接埠提供者。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugPortSupplier2`。  
  
|方法|描述|  
|--------|--------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|取得連接埠的供應商名稱。|  
|[GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md)|取得連接埠的供應商的識別項。|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|從連接埠提供者取得連接埠。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|列舉已存在的連接埠。|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|請確認連接埠提供者支援加入新的連接埠。|  
|[下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|新增連接埠。|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|移除連接埠。|  
  
## 備註  
 連接埠提供者可以辨別它自己的名字和 ID、 新增和移除連接埠，並列舉連接埠提供者所提供的所有連接埠。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)