---
title: IDebugDynamicField |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 41cf0e397834f337863baa46abb4e6bbccee98ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198504"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面代表變數的類型。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 此介面是由符號提供者實作為可在執行時間決定之任何類型的基類。 這僅適用于 managed 程式碼。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 這個介面代表基類，可從中衍生更特製化的介面。  
  
## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法  
 這個介面不提供繼承自的任何方法 `IDebugField` 。  
  
## <a name="requirements"></a>需求  
 標頭： sh. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
