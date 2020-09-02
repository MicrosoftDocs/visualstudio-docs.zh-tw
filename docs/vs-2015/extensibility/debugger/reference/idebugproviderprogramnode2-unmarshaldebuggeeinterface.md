---
title: IDebugProviderProgramNode2：： UnmarshalDebuggeeInterface |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3007d13ec3eae46511e4775497d0aad5b6325b2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146249"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得跨進程界限的指定介面。  
  
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
 在要取得之介面的 GUID。  
  
 `ppvObject`  
 擴展傳回物件，此物件會執行所需的介面。 [C + +] 這可以直接轉換為所需的介面類別型。 [C #] 使用 <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 方法來取得所需的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當 debug engine 在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 進程空間中執行，而且正在進行偵錯工具的進程空間中執行時，就會使用這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
