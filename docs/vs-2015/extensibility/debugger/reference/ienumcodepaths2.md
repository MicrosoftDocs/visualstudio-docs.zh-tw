---
title: IEnumCodePaths2 |Microsoft Docs
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
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51cb5881e20f9eff8465bf38c64006170aaeaed2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732696"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面代表程式碼路徑的清單。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 會實作這個介面來代表程式碼路徑的清單。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)來取得這個介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumCodePaths2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|擷取指定的數目的列舉型別序列中的程式碼路徑。|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|略過指定的數目的列舉型別序列中的程式碼路徑。|  
|[Reset](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|將列舉型別序列重設到開頭。|  
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|取得列舉值中的程式碼路徑數目。|  
  
## <a name="remarks"></a>備註  
 程式碼路徑代表在程式中的分支點或函式呼叫。 程式碼路徑的清單代表透過它已執行程式碼的路徑。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)

