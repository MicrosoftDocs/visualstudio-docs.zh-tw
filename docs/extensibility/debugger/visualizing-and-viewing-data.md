---
title: "視覺化及檢視資料 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 14e5b641dc5bc51ac066f32332f3fdb2b01d1810
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="visualizing-and-viewing-data"></a>視覺化及檢視資料
類型的視覺化檢視和自訂檢視器的開發人員快速有意義的方式呈現的資料。 運算式評估工具 (EE) 可支援第三方類型視覺化檢視，以及提供它自己的自訂檢視器。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]決定類型視覺化檢視和自訂檢視器的數目與相關聯物件的型別呼叫[GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)方法。 如果沒有至少一個類型的視覺化檢視或自訂檢視器可用，Visual Studio 會呼叫[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法來擷取這些視覺化檢視和檢視器的清單 (事實上，一份`CLSID`實作的 s視覺化檢視和檢視器） 並呈現給使用者。  
  
## <a name="supporting-type-visualizers"></a>支援的類型視覺化檢視  
 有許多的 EE 必須實作以支援類型的視覺化檢視的介面。 這些介面可以分成兩大類別： 這些網域及存取屬性資料類型的視覺化檢視清單。  
  
### <a name="listing-type-visualizers"></a>清單類型視覺化檢視  
 列出在實作這些類型視覺化檢視的 EE 支援`IDebugProperty3::GetCustomViewerCount`和`IDebugProperty3::GetCustomViewerList`。 這些方法都會傳遞至對應的方法呼叫[GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)和[GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)。  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)透過呼叫[CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)。 此方法需要[IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)介面，取自[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)介面傳遞到[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。 `IEEVisualizerServiceProvider::CreateVisualizerService`也需要[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)和[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)介面已傳遞給`IDebugParsedExpression::EvaluateSync`。 若要建立所需的最終介面`IEEVisualizerService`介面是[IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) EE 實作的介面。 這個介面可讓必須對正在視覺化之屬性的變更。 所有的屬性資料封裝在[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)也由 EE 實作的介面。  
  
### <a name="accessing-property-data"></a>存取屬性資料  
 存取屬性資料透過[IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面。 若要取得此介面，Visual Studio 會呼叫[QueryInterface](/cpp/atl/queryinterface)要取得的屬性物件上[IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)介面 (可實作的相同物件上實作[IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)介面)，然後呼叫[GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)方法，以取得`IPropertyProxyEESide`介面。  
  
 所有的資料傳遞入和移出`IPropertyProxyEESide`介面會封裝在[IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)介面。 此介面代表的位元組陣列，而且由 Visual Studio 和 EE 實作。 若要變更屬性的資料時，Visual Studio 會建立`IEEDataStorage`保留新的資料和呼叫物件[CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)與該資料物件，以取得新`IEEDataStorage`物件，該物件，接著，傳遞至[InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)更新屬性的資料。 `IPropertyProxyEESide::CreateReplacementObject`可讓它自己實作的類別具現化 EE`IEEDataStorage`介面。  
  
## <a name="supporting-custom-viewers"></a>支援的自訂檢視器  
 旗標`DBG_ATTRIB_VALUE_CUSTOM_VIEWER`中設定`dwAttrib`欄位[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)結構 (呼叫所傳回的[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) 來表示物件是否具有相關聯的自訂檢視器使用它。 當設定這個旗標時，會取得 Visual Studio [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)介面從[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面使用[QueryInterface](/cpp/atl/queryinterface)。  
  
 如果使用者選取自訂檢視器時，Visual Studio 會具現化使用的檢視器的自訂檢視器`CLSID`所提供的`IDebugProperty3::GetCustomViewerList`方法。 Visual Studio 接著會呼叫[DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)向使用者顯示的值。  
  
 一般來說，`IDebugCustomViewer::DisplayValue`呈現資料的唯讀檢視。 若要讓資料的變更，EE 必須實作自訂介面屬性物件上支援變更的資料。 `IDebugCustomViewer::DisplayValue`方法會使用這個自訂的介面來支援變更的資料。 方法會尋找自訂介面`IDebugProperty2`介面當做傳入`pDebugProperty`引數。  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>同時支援類型的視覺化檢視和自訂檢視器  
 類型的視覺化檢視和自訂檢視器中的，可以支援 EE [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)和[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法。 EE 首先，它提供的自訂檢視器的數目將所傳回的值[GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)方法。 第二，將附加 EE`CLSID`自己自訂的檢視所傳回的清單進行之[GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)方法。  
  
## <a name="see-also"></a>請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)   
 [類型視覺化檢視和自訂檢視器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)