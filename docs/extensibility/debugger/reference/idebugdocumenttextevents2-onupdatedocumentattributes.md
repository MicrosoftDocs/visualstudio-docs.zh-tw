---
description: 通知接收者已更新檔案屬性的事件。
title: IDebugDocumentTextEvents2：： onUpdateDocumentAttributes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateDocumentAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateDocumentAttributes
ms.assetid: 31b7d151-9ce2-438e-b405-f8cc46b9f537
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b217ca0f6fe21b2170ea0ae5a4b9c22e5a21a84f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084905"
---
# <a name="idebugdocumenttextevents2onupdatedocumentattributes"></a>IDebugDocumentTextEvents2::onUpdateDocumentAttributes
通知接收者已更新檔案屬性的事件。

## <a name="syntax"></a>語法

```cpp
HRESULT onUpdateDocumentAttributes( 
   TEXT_DOC_ATTR_2 textdocattr
);
```

```csharp
int onUpdateDocumentAttributes( 
   enum_TEXT_DOC_ATTR_2 textdocattr
);
```

## <a name="parameters"></a>參數
`textdocattr`\
在 [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) 列舉中的旗標組合，可指定檔的更新屬性。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)
