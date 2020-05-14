---
title: IDebugError事件2::獲取錯誤消息 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ff1da2f2a2d24b958a613e6fe5cb58c0081ed3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730038"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
返回允許構造人類可讀錯誤消息的資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>參數
`pMessageType`\
[出]從[消息類型](../../../extensibility/debugger/reference/messagetype.md)枚舉中返回一個值,描述消息的類型。

`pbstrErrorFormat`\
[出]向使用者發送的最後消息的格式(有關詳細資訊,請參閱"備註")。

`hrErrorReason`\
[出]消息所講述的錯誤代碼。

`pdwType`\
[出]錯誤的嚴重性(使用`MessageBox`MB_XXX常量`MB_EXCLAMATION``MB_WARNING`;

`pbstrHelpFileName`\
[出]説明檔的路徑(如果沒有説明檔,則設置為空值)。

`pdwHelpId`\
[出]要顯示的幫助主題的 ID(如果沒有幫助主題,則設置為 0)。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 錯誤訊息的格式應沿`"What I was doing.  %1"`的行。 然後`"%1"`,調用方將替換為從錯誤代碼派生的錯誤消息(在`hrErrorReason`中返回)。 參數`pMessageType`告訴調用方如何顯示最終錯誤消息。

## <a name="see-also"></a>另請參閱
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [訊息類型](../../../extensibility/debugger/reference/messagetype.md)
