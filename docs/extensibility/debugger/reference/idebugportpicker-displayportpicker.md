---
title: IDebugPortPicker::DisplayPortPicker |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e115c4e45784b2072bf626d90ebab0d980491e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871499"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

顯示指定的對話方塊中，可讓使用者選取一個連接埠。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
