---
title: IDebugCoreServer3::CreateInstanceInServer |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: cbd287f5ab75374a3272ecbb34c36ffdf384ba84
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
 [in]實作中指定的 CLSID 的 dll 路徑`clsidObject`參數。 如果這是`NULL`，然後 COM 的`CoCreateInstance`呼叫函式。  
  
 `wLangId`  
 [in]偵錯引擎的地區設定。 這可以是 0，如果[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)不應該呼叫方法。  
  
 `clsidObject`  
 [in]若要建立的偵錯引擎的 CLSID。  
  
 `riid`  
 [in]特定介面的介面識別碼來擷取類別物件。  
  
 `ppvObject`  
 [out]`IUnknown`從具現化物件的介面。 轉型，或此物件所需的介面來封送處理。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)