---
description: 讓 Visual Studio UI 在 [附加至進程] 對話方塊的 [傳輸資訊] 區段中顯示文字。
title: IDebugPortSupplierDescription2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dba3cd07bb84843ff4d2531cdde63ab9e671f961
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071918"
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
