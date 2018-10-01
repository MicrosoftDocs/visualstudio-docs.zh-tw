---
title: IDebugField::GetExtendedInfo |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd17bfdb3f1d78fd095accef66f197ec0c1d8c27
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490844"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugField::GetExtendedInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfield-getextendedinfo)。  
  
這個方法取得擴充欄位的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
  
|值|描述|  
|-----------|-----------------|  
|`guidConstantValue`|以一連串的位元組值。|  
|`guidConstantType`|做為型別簽章類型。|  
  
 `prgBuffer`  
 [out]傳回擴充的資訊。  
  
 `pdwLen`  
 [in、 out]會傳回大小的擴充的資訊，以位元組為單位。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 目前，這個方法只會傳回型別或常數的值。 呼叫端必須釋放中傳回的緩衝區`prgBuffer`藉由呼叫 COM 的`CoTaskMemFree`函式 （c + +） 或<xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>(C#)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

