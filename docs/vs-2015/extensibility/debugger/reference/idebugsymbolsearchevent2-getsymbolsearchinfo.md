---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo |Microsoft Docs
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
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec8c09a2bbb618f5d758ca00dfc43e9a573b5ca0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906958"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

呼叫以擷取結果的符號載入處理序相關的事件處理常式。  
  
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
 [in、 out]傳回字串，包含從模組的任何錯誤訊息。 如果沒有任何錯誤，此字串只會包含模組的名稱，但永遠不會是空白。  
  
> [!NOTE]
>  [C + +]`pbstrDebugMessage`不可`NULL`，而且必須與釋放`SysFreeString`。  
  
 `pdwModuleInfoFlags`  
 [out]從旗標的組合[MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)列舉，指出是否已載入任何符號。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當處理常式收到[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)事件之後嘗試載入模組的偵錯符號，處理常式可以呼叫 thismethod 來判斷該負載的結果。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)

