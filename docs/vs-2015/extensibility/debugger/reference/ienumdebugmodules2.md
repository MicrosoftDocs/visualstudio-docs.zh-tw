---
title: IEnumDebugModules2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0f4b53a6c6290f57e6d54856b602edf3558ff841
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742982"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面列舉模組的清單。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 會實作這個介面來代表程式載入的模組清單。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 Visual Studio 呼叫[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)來取得這個介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugModules2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|擷取指定的列舉順序中的模組數目。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|略過指定的列舉順序中的模組數目。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|將列舉型別序列重設到開頭。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|取得模組的數目。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會使用此介面主要是用來更新**模組**視窗。  
  
 基於偵錯在 Visual Studio 中，程式會以邏輯順序的程式碼指令可以跨模組界限，因此需要一份適用於單一模組[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。 在清單中的第一個模組通常會包含相關聯的程式的初始的進入點。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)

