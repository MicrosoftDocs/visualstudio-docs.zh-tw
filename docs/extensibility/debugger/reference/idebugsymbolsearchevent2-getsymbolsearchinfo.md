---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 518429149ad1d997b860e486f3db4e519ef42cae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
呼叫事件處理常式來擷取有關符號載入處理序的結果。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```csharp  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `pModule`  
 [out]IDebugModule3 物件，表示已載入符號的模組。  
  
 `pbstrDebugMessage`  
 [in、 out]傳回字串，包含從模組的任何錯誤訊息。 如果沒有發生錯誤，這個字串將只包含模組的名稱，但不是能是空白。  
  
> [!NOTE]
>  [C + +]`pbstrDebugMessage`不可`NULL`，而且必須與釋放`SysFreeString`。  
  
 `pdwModuleInfoFlags`  
 [out]從旗標的組合[MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)列舉，指出是否已載入任何符號。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當處理常式會接收[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)事件之後嘗試載入模組的偵錯符號，處理常式會呼叫 thismethod 來判斷該負載結果。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)