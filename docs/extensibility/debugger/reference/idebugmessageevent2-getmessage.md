---
title: IDebug消息事件2::獲取消息 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 819b796a656f0ef8775fbb1c9e800e3019b81729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727408"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
獲取要顯示的消息。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMessage( 
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrMessage,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetMessage( 
   out enum_MESSAGETYPE pMessageType,
   out string           pbstrMessage,
   out uint             pdwType,
   out string           pbstrHelpFileName,
   out uint             dwHelpId
);
```

## <a name="parameters"></a>參數
`pMessageType`\
[出]從[消息類型](../../../extensibility/debugger/reference/messagetype.md)枚舉中返回描述消息類型的值。

`pbstrMessage`\
[出]返回消息。

`pdwType`\
[出]使用 Win32`MessageBox`函數的約定返回消息的類型。 有關詳細資訊,請參閱[AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)功能。

`pbstrHelpFileName`\
[進出]返回説明檔名。 如果沒有説明檔,則可能是空(C++)或空 (C#) 值。

`pdwHelpId`\
[進出]返回幫助標識碼。 如果沒有與此消息關聯的説明,則可能是 0。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [訊息類型](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
