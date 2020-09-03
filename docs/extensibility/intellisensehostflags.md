---
title: IntelliSenseHostFlags |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710262"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
指定 IntelliSense 主機旗標。

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
|`IHF_READONLYCONTEXT`|內容緩衝區是唯讀的。|
|`IHF_NOSEPARATESUBJECT`|沒有主體文字。 內容緩衝區包含 IntelliSense-目標 (意指 `!IHF_READONLYCONTEXT`) 。|
|`IHF_SINGLELINESUBJECT`|主體文字無法支援多行功能。|
|`IHF_FORCECOMMITTOCONTEXT`|與 `CanCommitIntoReadOnlyBuffer` 相同。|
|`IHF_OVERTYPE`|在 [主體] 或 [內容]) 中編輯 (應該在 [改寫] 模式中完成。|

## <a name="requirements"></a>需求
 SingleFileeditor .idl

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.TextManager.Interop>
