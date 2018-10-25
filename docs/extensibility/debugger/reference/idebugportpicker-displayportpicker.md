---
title: IDebugPortPicker::DisplayPortPicker |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d05f49f8fa91a0b193be10169a4dcebcd561f92d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910572"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
顯示指定的對話方塊中，可讓使用者選取一個連接埠。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `hwndParentDialog`  
 [in]父對話方塊中的控制代碼。  
  
 `pbstrPortId`  
 [out]連接埠識別碼字串。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 傳回值`S_FALSE`(或傳回值`S_OK`具有`BSTR`設定為`NULL`) 指出使用者已按下**取消**。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)