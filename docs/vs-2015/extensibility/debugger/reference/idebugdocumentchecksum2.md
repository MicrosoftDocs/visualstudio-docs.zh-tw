---
title: IDebugDocumentChecksum2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ba1510745b4781d56655fe83fffbb18f4ca65254
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156471"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

表示 debug 檔的總和檢查碼，並且可在元件之間傳遞總和檢查碼。  
  
## <a name="syntax"></a>語法  
  
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
  
## <a name="requirements"></a>需求  
 標頭： Msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll
