---
title: "IDebugCustomViewer::DisplayValue |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer::DisplayValue
helpviewer_keywords: IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 701c5e33273dc6d00156e554e1abaa9a003568eb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
將指定的值顯示為呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```csharp  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### <a name="parameters"></a>參數  
 `hwnd`  
 [in]父視窗  
  
 `dwID`  
 [in]支援多個類型的自訂檢視器的識別碼。  
  
 `pHostServices`  
 [in]保留。 一律設為 null。  
  
 `pDebugProperty`  
 [in]可以用來擷取要顯示值的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會建立必要的視窗，顯示的值、 等候輸入，並關閉視窗，再傳回給呼叫端的所有，顯示為 「 強制回應 」。 這表示方法必須處理的顯示屬性的值，無法建立輸出，以等候使用者輸入，若要終結視窗的視窗的所有層面。  
  
 若要支援上變更此值指定[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)物件，您可以使用[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)方法-如果此值可以表示為字串。 否則，就必須建立自訂介面 — 獨佔實作此運算式評估工具`DisplayValue`方法-實作的相同物件上`IDebugProperty3`介面。 這個自訂的介面會提供方法來變更資料的任意大小或複雜度。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)