---
title: IDebugDocumentChecksum2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 50fbee2dbdb30873c97f1ca465d99161add90a19
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
代表偵錯文件的總和檢查碼，並可讓您傳遞元件之間的總和檢查碼。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 可以實作這個介面會公開任何元件[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面。 不過，它是主要所實作的偵錯引擎，這樣可以傳回給 IDE 和尋找來源時使用的符號檔 (*.pdb) 中內嵌的總和檢查碼。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugDocumentChecksum2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|擷取指定要使用的位元組數目上限的文件的總和檢查碼及演算法識別項。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll