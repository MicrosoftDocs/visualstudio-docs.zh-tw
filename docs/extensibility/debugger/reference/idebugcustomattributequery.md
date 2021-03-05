---
description: 表示方法或型別上的自訂屬性查詢。
title: IDebugCustomAttributeQuery |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 31212a7c2d032dd22aa2fddb8df6718cceeff587
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154466"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
表示方法或型別上的自訂屬性查詢。

## <a name="syntax"></a>Syntax

```
IDebugCustomAttributeQuery : IUnknown
```

## <a name="methods"></a>方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|取得自訂屬性的名稱。|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|在指定的自訂屬性中判斷。|

## <a name="requirements"></a>規格需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
