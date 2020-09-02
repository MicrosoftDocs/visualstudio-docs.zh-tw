---
title: IDebugCustomViewer：:D isplayValue |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bda4c60e9164ae195c0e3ba49893b1a818c66f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421368"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

呼叫這個方法來顯示指定的值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 在父視窗  
  
 `dwID`  
 在支援多個類型之自訂檢視器的識別碼。  
  
 `pHostServices`  
 [in] 保留。 一律設為 null。  
  
 `pDebugProperty`  
 在介面，可用來取得要顯示的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。  
  
## <a name="remarks"></a>備註  
 顯示為「強制回應」，這個方法將會建立必要的視窗、顯示值、等候輸入，以及關閉視窗，然後再返回呼叫端。 這表示此方法必須處理顯示內容值的所有層面，從建立輸出視窗到等候使用者輸入，到終結視窗。  
  
 若要支援變更指定之 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 物件的值，您可以使用 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) 方法（如果值可以表示為字串）。 否則，您必須 `DisplayValue` 在相同的物件上建立自訂介面，此介面是執行此方法的運算式評估工具所特有 `IDebugProperty3` 。 這個自訂介面會提供方法來變更任意大小或複雜度的資料。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
