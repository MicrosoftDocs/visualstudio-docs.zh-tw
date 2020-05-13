---
title: IntelliSenseHostFlags |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0df05e7363db01bd4f16fee5d75141dc93df1c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710262"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
指定 IntelliSense 主機標誌。

## <a name="syntax"></a>語法

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>參數

|成員|描述|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|上下文緩衝區是唯讀的。|
|`IHF_NOSEPARATESUBJECT`|無主題文本。 上下文緩衝區包含 IntelliSense 目標`!IHF_READONLYCONTEXT`(暗示 )。|
|`IHF_SINGLELINESUBJECT`|主題文本不支援多行。|
|`IHF_FORCECOMMITTOCONTEXT`|與 `CanCommitIntoReadOnlyBuffer` 相同。|
|`IHF_OVERTYPE`|編輯(在主題或上下文中)應在過度類型模式下完成。|

## <a name="requirements"></a>需求
 單檔案編輯器.idl

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.TextManager.Interop>
