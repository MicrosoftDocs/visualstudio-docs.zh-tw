---
description: 讓 Visual Studio UI 在 [附加至進程] 對話方塊的 [傳輸資訊] 區段中顯示文字。
title: IDebugPortSupplierDescription2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c3cd8d6fbeaf020ea772c9bd5cae783b6e8d127
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150376"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
讓 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 在 [**附加至進程**] 對話方塊的 [**傳輸資訊**] 區段中顯示文字。

## <a name="syntax"></a>Syntax

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 此介面是由埠供應商所執行。

## <a name="methods"></a>方法
 下表顯示的方法 `IDebugPortSupplierDescription2` 。

|方法|描述|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|抓取埠供應商的描述和描述中繼資料。|

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
