---
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b4bfc51595e6414a3760d4e57ab6f9791259f83
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341291"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
表示偵錯文件的總和檢查碼，並讓傳遞元件之間的總和檢查碼。

## <a name="syntax"></a>語法

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 公開 （expose） 的任何元件可以實作這個介面[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面。 不過，它是主要被藉由偵錯引擎，讓內嵌在符號檔 (*.pdb) 的總和檢查碼可以傳回給 IDE，並尋找來源時使用。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugDocumentChecksum2`。

|方法|描述|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|擷取指定要使用的位元組數目上限的文件的總和檢查碼和演算法識別項。|

## <a name="requirements"></a>需求
 標頭：Msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll