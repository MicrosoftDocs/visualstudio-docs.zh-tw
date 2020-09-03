---
title: IDebugPortPicker：:D isplayPortPicker |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0a02169b37bba804034990ed5d972f973244769
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724899"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
顯示允許使用者選取埠的指定對話方塊。

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

## <a name="parameters"></a>參數
`hwndParentDialog`\
在父對話方塊的控制碼。

`pbstrPortId`\
擴展埠識別碼字串。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  (的傳回值 `S_FALSE` 或傳回值， `S_OK` 且 `BSTR` 設定為 `NULL`) 表示使用者按一下 [ **取消**]。

## <a name="see-also"></a>另請參閱
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
