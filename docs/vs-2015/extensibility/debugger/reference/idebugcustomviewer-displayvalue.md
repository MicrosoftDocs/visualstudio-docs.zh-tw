---
title: IDebugCustomViewer::DisplayValue |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d75ff31ef9ba0ba1badad5cd298b0f8f7220541e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486493"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugCustomViewer::DisplayValue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcustomviewer-displayvalue)。  
  
顯示指定的值，會呼叫這個方法。  
  
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
 [in]父視窗  
  
 `dwID`  
 [in]支援多個類型的自訂檢視器的識別碼。  
  
 `pHostServices`  
 [in]保留。 一律設為 null。  
  
 `pDebugProperty`  
 [in]介面，可用來擷取要顯示的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會建立必要的視窗、 顯示值、 等待輸入，並關閉視窗，所有傳回給呼叫端之前，顯示是"modal"。 這表示此方法必須處理的顯示屬性的值，無法建立輸出，以等候使用者輸入，若要終結視窗的視窗的所有層面。  
  
 若要支援上變更值，指定[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)物件，您可以使用[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)方法： 如果此值可以表示為字串。 否則，就必須建立自訂的介面 — 獨佔運算式評估工具實作此`DisplayValue`方法，實作的相同物件上`IDebugProperty3`介面。 這個自訂的介面會提供方法來變更資料的任意規模或複雜度。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)

