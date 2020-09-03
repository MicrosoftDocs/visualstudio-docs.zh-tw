---
title: IEnumCodePaths2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 577b2691ed67751407621d5000ee9a8abec318df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192010"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面代表程式碼路徑的清單。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Debug engine (DE) 會執行這個介面，以代表程式碼路徑的清單。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 呼叫 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) 以取得這個介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IEnumCodePaths2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[下一個](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|抓取列舉序列中指定的程式碼路徑數目。|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|略過列舉序列中指定數目的程式碼路徑。|  
|[重設](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|將列舉順序重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|取得列舉值中的程式碼路徑數目。|  
  
## <a name="remarks"></a>備註  
 程式碼路徑代表程式中的分支點或函式呼叫。 程式碼路徑清單代表執行程式碼的路徑。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
