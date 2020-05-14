---
title: IDebug文檔校驗和2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03cfb29cc54a2f0ab18bce3ec0761cfab62e20df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731905"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
表示調試文件的校驗和,並啟用在元件之間傳遞校驗和。

## <a name="syntax"></a>語法

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面可以由公開[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面的任何元件實現。 但是,它主要由調試引擎實現,以便符號檔 (*.pdb) 中嵌入的校驗和可以傳回 IDE 並在查找源時使用。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugDocumentChecksum2`。

|方法|描述|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|在最多要使用的位元組數的情況下檢索文件校驗和和演算法標識碼。|

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
