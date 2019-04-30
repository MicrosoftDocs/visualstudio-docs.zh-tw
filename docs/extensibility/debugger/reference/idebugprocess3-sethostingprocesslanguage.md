---
title: IDebugProcess3::SetHostingProcessLanguage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e10c77fb7e4fd3e7a679e9954140760c282952b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917649"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
這個方法會設定程序會裝載下的語言。 然後偵錯引擎 (DE) 載入適當的運算式評估工具使用此語言。

## <a name="syntax"></a>語法

```cpp
HRESULT SetHostingProcessLanguage(
   REFGUID guidLang
);
```

```csharp
int SetHostingProcessLanguage(
   ref Guid guidLang
);
```

#### <a name="parameters"></a>參數
 `guidLang`

 [in]`GUID` DE 應該使用的語言。 指定`GUID_NULL`(C++) 或`Guid.Empty`(C#) 能夠使用預設的語言 DE。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。

## <a name="remarks"></a>備註
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)可用來擷取目前的語言設定。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)