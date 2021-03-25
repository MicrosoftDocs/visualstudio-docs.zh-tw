---
description: 表示 debug 檔的總和檢查碼，並且可在元件之間傳遞總和檢查碼。
title: IDebugDocumentChecksum2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 518e5b089d0d34e2492297b27dd0829e5f00ef2f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066733"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
表示 debug 檔的總和檢查碼，並且可在元件之間傳遞總和檢查碼。

## <a name="syntax"></a>Syntax

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 此介面可由任何公開 [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 介面的元件來執行。 不過，它主要是由偵錯工具引擎所執行，因此在符號檔中內嵌的總和檢查碼 ( * .pdb) 可以傳回至 IDE，並在尋找來源時使用。

## <a name="methods"></a>方法
 下表顯示的方法 `IDebugDocumentChecksum2` 。

|方法|描述|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|使用指定的最大位元組數目，抓取檔總和檢查碼和演算法識別碼。|

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
