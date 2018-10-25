---
title: IDebugCoreServer3::CreateInstanceInServer |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 171eda8b7c1b206ea54839366686ad43f690afe0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886470"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
在伺服器上建立偵錯引擎執行的個體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szDll`  
 [in]實作中指定的 CLSID 的 dll 路徑`clsidObject`參數。 如果是這`NULL`，然後 COM 的`CoCreateInstance`呼叫函式。  
  
 `wLangId`  
 [in]偵錯引擎的地區設定。 這可以是 0，如果[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)不應該呼叫方法。  
  
 `clsidObject`  
 [in]若要建立偵錯引擎的 CLSID。  
  
 `riid`  
 [in]特定介面的介面識別碼來擷取類別物件。  
  
 `ppvObject`  
 [out]`IUnknown`介面具現化物件。 轉型或封送處理這個物件所需的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)