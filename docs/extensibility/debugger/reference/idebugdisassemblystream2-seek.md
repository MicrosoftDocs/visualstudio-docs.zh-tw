---
title: IDebugdisassemblystream2::尋求 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4954b3b278b3c7a6b798a4ffda3856ab8bb200c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732080"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
相對於指定位置,在拆解流中移動讀取指標的給定指令數。

## <a name="syntax"></a>語法

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>參數
`dwSeekStart`\
[在][SEEK_START](../../../extensibility/debugger/reference/seek-start.md)枚舉中的值,用於指定開始尋價過程的相對位置。

`pCodeContext`\
[在][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件表示查找操作相對於的代碼上下文。 只當 使用時`dwSeekStart` = `SEEK_START_CODECONTEXT`, 才使用此參數。否則,將忽略此參數,並且可以是 null 值。

`uCodeLocationId`\
[在]尋找操作相對於的代碼位置識別碼。 `dwSeekStart` = 這裡`SEEK_START_CODELOCID`參數否則,將忽略此參數,並可以設置為 0。 有關代碼位置識別碼的說明,請參閱[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)方法的備註部分。

`iInstructions`\
[在]相對於`dwSeekStart`中 指定的位置移動的指令數。 此值可以是負值,以便向後移動。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果`S_FALSE`尋用位置超出可用指令列表的點,則返回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 如果搜索位於清單開頭之前的位置,則讀取位置將設置為清單中的第一個指令。 如果 see 位於清單末尾之後的位置,則讀取位置將設置為清單中的最後一個指令。

## <a name="see-also"></a>另請參閱
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
