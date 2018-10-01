---
title: IDebugDocumentChecksum2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85e6d3428b5091841f0229b146c9e086ceb208d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497740"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugDocumentChecksum2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentchecksum2)。  
  
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
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

