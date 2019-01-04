---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c91ac932692ac63cfd4f8129fdff65993cddf2e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856104"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
跨處理序界限，會取得指定的介面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `riid`  
 [in]若要取得介面的 GUID。  
  
 `ppvObject`  
 [out]傳回實作所需的介面的物件。 [C + +] 這可以直接為所需的介面型別轉換。 [C#] 使用<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>方法來取得所需的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當偵錯引擎中執行時，會使用這個方法[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]它自己的處理序空間中執行的處理序空間和正在偵錯程式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)