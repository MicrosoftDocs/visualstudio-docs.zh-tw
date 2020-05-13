---
title: IDebugPortPicker::D播放波特皮克 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724899"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
顯示允許用戶選擇埠的指定對話方塊。

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
[在]父對話框的句柄。

`pbstrPortId`\
[出]埠識別字串。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 返回`S_FALSE`值 (或`S_OK``BSTR`與設置`NULL`為的返回值 ) 表示使用者按兩下 **「取消**」。

## <a name="see-also"></a>另請參閱
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
