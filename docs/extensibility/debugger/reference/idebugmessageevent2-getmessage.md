---
description: 取得要顯示的訊息。
title: IDebugMessageEvent2：： GetMessage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc9b1747a504b761b369b2995dfef4c28ff3d012
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058465"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
取得要顯示的訊息。

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
擴展傳回 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) 列舉中的值，這個值會描述訊息的類型。

`pbstrMessage`\
擴展傳回訊息。

`pdwType`\
擴展使用 Win32 函數的慣例，傳回訊息的型別 `MessageBox` 。 如需詳細資訊，請參閱 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) 函數。

`pbstrHelpFileName`\
[in，out]傳回說明檔名稱。 如果沒有說明檔，則可以是 null (c + +) 或空的 (c # ) 值。

`pdwHelpId`\
[in，out]傳回說明識別碼。 如果沒有與此訊息相關聯的說明，則可能為0。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
