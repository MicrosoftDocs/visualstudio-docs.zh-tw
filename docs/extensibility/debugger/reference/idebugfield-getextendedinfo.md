---
title: "IDebugField::GetExtendedInfo |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetExtendedInfo
helpviewer_keywords: IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5b52c5634b4b34edf11ddb8a56317cc237063bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
這個方法取得擴充欄位的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidExtendedInfo`  
 [in]選取要傳回的資訊。 有效值為：  
  
|值|說明|  
|-----------|-----------------|  
|`guidConstantValue`|以一連串的位元組值。|  
|`guidConstantType`|類型簽章為型別。|  
  
 `prgBuffer`  
 [out]傳回擴充的資訊。  
  
 `pdwLen`  
 [in、 out]傳回的大小擴充的資訊，以位元組為單位。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 目前，這個方法只會傳回型別或常數的值。 呼叫端必須釋放中傳回的緩衝區`prgBuffer`藉由呼叫 COM 的`CoTaskMemFree`函式 （c + +） 或<xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>(C#)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)