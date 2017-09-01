---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 9
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
ms.openlocfilehash: bf9e3ffdfe0598718a3b8bc9857c350d5d673ba7
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Displays the specified dialog box that allows the user to select a port.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `hwndParentDialog`  
 [in] Handle for the parent dialog box.  
  
 `pbstrPortId`  
 [out] Port identifier string.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code. A return value of `S_FALSE` (or a return value of `S_OK` with the `BSTR` set to `NULL`) indicates that the user  clicked **Cancel**.  
  
## <a name="see-also"></a>See Also  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
