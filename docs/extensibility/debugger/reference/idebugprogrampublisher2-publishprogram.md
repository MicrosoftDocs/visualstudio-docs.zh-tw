---
description: 此方法可讓您將程式用於偵錯工具， (DEs) 和會話偵錯工具管理員。
title: IDebugProgramPublisher2：:P ublishProgram |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2904376efa1a6798cbba967b93ad1c93d395b919
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171585"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
此方法可讓您將程式用於偵錯工具， (DEs) 和會話偵錯工具管理員。

## <a name="syntax"></a>語法

```cpp
HRESULT PublishProgram(
   CONST_GUID_ARRAY Engines,
   LPCOLESTR        szFriendlyName,
   IUnknown*        pDebuggeeInterface
);
```

```csharp
int PublishProgram(
   CONST_GUID_ARRAY Engines,
   string           szFriendlyName,
   object           pDebuggeeInterface
);
```

## <a name="parameters"></a>參數
`Engines`\
在可啟動或附加至此程式的 DEs Guid 陣列。

`szFriendlyName`\
在程式的易記名稱 (這會出現在顯示給使用者) 的功能表或對話方塊中。

`pDebuggeeInterface`\
[in] `IUnknown` 程式的介面 (此值會用來做為用來唯一識別程式的 cookie;這個相同的值是用來「取消發佈」程式) 

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 若要讓程式無法再進行偵錯工具，請呼叫 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)。

## <a name="see-also"></a>另請參閱
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
