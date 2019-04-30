---
title: IDebugDocumentTextEvents2::onReplaceText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnReplaceText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onReplaceText
ms.assetid: cb39f025-66d8-4dc0-bef6-1bdc8e07db92
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68c1097e622da25717a4bd3b2893dfe118b4c588
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875415"
---
# <a name="idebugdocumenttextevents2onreplacetext"></a>IDebugDocumentTextEvents2::onReplaceText
文件中，已被取代的文字會告知偵錯封裝。

## <a name="syntax"></a>語法

```cpp
HRESULT onReplaceText( 
   TEXT_POSITION pos,
   DWORD         dwNumToReplace
);
```

```csharp
int onReplaceText( 
   enum_TEXT_POSITION pos,
   uint               dwNumToReplace
);
```

#### <a name="parameters"></a>參數
 `pos`

 [in]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)表示已取代文字。

 `dwNumToReplace`

 [in]指定文字的已取代的字元數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)