---
title: IDebugPortPicker::DisplayPortPicker |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e115c4e45784b2072bf626d90ebab0d980491e4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687350"
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
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)