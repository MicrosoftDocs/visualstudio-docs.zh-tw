---
title: IDebugProperty2::GetExtendedInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e0366d547dea7f181c42fd5cccbacb568418c203
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935407"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
取得擴充屬性的資訊。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `guidExtendedInfo`  
 [in]決定要擷取的擴充資訊的類型的 GUID。 如需詳細資訊，請參閱 < 備註 >。  
  
 `pExtendedInfo`  
 [out]傳回`VARIANT`（c + +） 或物件 (C#)，可用來擷取擴充的屬性的資訊。 比方說，這個參數可能會傳回`IUnknown`介面，可以查詢[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)介面。 如需詳細資訊，請參閱 < 備註 >。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 傳回`S_GETEXTENDEDINFO_NO_EXTENDEDINFO`如果擷取沒有延伸資訊。  
  
## <a name="remarks"></a>備註  
 這個方法存在，以擷取本身就無法藉由呼叫所擷取的資訊[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。  
  
 （因為不提供任何組件名稱，GUID 值會指定 C#） 此方法通常可辨識下列的 Guid。 供內部使用，可以建立額外的 Guid。  
  
|名稱|GUID|描述|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|傳回`IUnknown`文件的介面。 通常[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)介面可以從此`IUnknown`介面。|  
|guidCodeContext|{e2fc65e-56ce-11 d 1-b528-00aax004a8797}|傳回`IUnknown`的文件內容的介面。 通常[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面可以從此`IUnknown`介面。|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|傳回字串，包含 CLSID 的自訂檢視器，通常由運算式評估工具進行實作。|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|傳回代表所要的位置數目，如果這個屬性表示 managed 程式碼的本機位址的 32 位元數字。|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|傳回字串，包含與屬性物件相關聯的變數簽章。|  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)