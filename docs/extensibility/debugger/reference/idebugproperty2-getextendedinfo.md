---
title: IDebugProperty2::GetExtendedInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b652ffc96bd50fea2988cce2130f2bf5e556605f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Gets extended information for the property.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `guidExtendedInfo`  
 [in] GUID that determines the type of extended information to be retrieved. See Remarks for details.  
  
 `pExtendedInfo`  
 [out] Returns a `VARIANT` (C++) or object (C#) that can be used to retrieve the extended property information. For example, this parameter might return an `IUnknown` interface that can be queried for an [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interface. See Remarks for details.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise returns error code. Returns `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` if there is no extended information to retrieve.  
  
## <a name="remarks"></a>Remarks  
 This method exists for the purpose of retrieving information that does not lend itself to being retrieved by calling the [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) method.  
  
 The following GUIDs are typically recognized by this method (the GUID values are specified for C# since the name is not available in any assembly). Additional GUIDs can be created for internal use.  
  
|Name|GUID|Description|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Returns an `IUnknown` interface to the document. Typically, the [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interface can be obtained from this `IUnknown` interface.|  
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Returns an `IUnknown` interface to the document context. Typically, the [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface can be obtained from this `IUnknown` interface.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Returns a string containing the CLSID of a custom viewer, typically implemented by an expression evaluator.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Returns a 32-bit number representing the desired slot number if this property represents a managed code local address.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Returns a string containing the signature of the variable associated with the property object.|  
  
## <a name="see-also"></a>See Also  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
