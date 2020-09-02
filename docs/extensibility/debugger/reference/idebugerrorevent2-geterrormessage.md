---
title: IDebugErrorEvent2：： GetErrorMessage |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730038"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
傳回可讓人看得懂的錯誤訊息的資訊。

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
擴展從 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) 列舉傳回值，描述訊息的類型。

`pbstrErrorFormat`\
擴展使用者的最終訊息格式 (如需詳細資料，請參閱「備註」) 。

`hrErrorReason`\
擴展訊息的相關錯誤碼。

`pdwType`\
擴展錯誤的嚴重性 (使用 MB_XXX 的常數 `MessageBox` ，例如 `MB_EXCLAMATION` 或 `MB_WARNING`) 。

`pbstrHelpFileName`\
擴展說明檔的路徑 (如果沒有說明檔) ，則設定為 null 值。

`pdwHelpId`\
擴展要顯示之說明主題的識別碼 (設定為0（如果沒有說明主題) ）。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 錯誤訊息應該依照的行格式化 `"What I was doing.  %1"` 。 `"%1"`然後，呼叫端會將取代為) 中所傳回之錯誤碼 (的錯誤訊息取代 `hrErrorReason` 。 `pMessageType`參數會告訴呼叫端應該如何顯示最終的錯誤訊息。

## <a name="see-also"></a>另請參閱
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
