---
title: IDebugProcess3::設置託管進程語言 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a16f2c39fa2d53ffc4d113666ef7630557e61861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723561"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
此方法設置進程將承載下的語言。 然後,調試引擎 (DE) 可以使用此語言載入相應的運算式賦值器。

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

## <a name="parameters"></a>參數
`guidLang`\
[在]`GUID` DE 應使用的語言。 指定`GUID_NULL`(C++)`Guid.Empty`或 (C#) 讓 DE 使用預設語言。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
- [GetHostingProcess 語言](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)可用於檢索當前語言設置。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)
