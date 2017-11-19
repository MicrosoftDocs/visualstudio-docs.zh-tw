---
title: "IEnumCodePaths2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCodePaths2
helpviewer_keywords: IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a9c27084032e0492b1110b1a085ded4f8e556433
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
此介面代表程式碼路徑的清單。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面來代表的程式碼路徑清單。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumCodePaths2`。  
  
|方法|說明|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|擷取指定的數目的列舉順序中的程式碼路徑。|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|略過指定的數目的列舉順序中的程式碼路徑。|  
|[重設](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|列舉序列重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態相同。|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|取得列舉值中的程式碼路徑數目。|  
  
## <a name="remarks"></a>備註  
 程式碼路徑代表在程式中的分支點或函式呼叫。 程式碼路徑的清單表示執行程式碼已透過該採取的路徑。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)