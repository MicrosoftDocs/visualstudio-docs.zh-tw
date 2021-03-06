---
description: 表示建立代表型別之欄位的能力。
title: IDebugTypeFieldBuilder |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1bc4f58470792cac8bdb68ede4ddf37567bac208
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223104"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
表示建立代表型別之欄位的能力。

## <a name="syntax"></a>Syntax

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>呼叫者注意事項
 這個介面是從符號提供者取得。

## <a name="methods"></a>方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|建立代表基本類型的物件。|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|建立指定類型的指標。|

## <a name="requirements"></a>規格需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
