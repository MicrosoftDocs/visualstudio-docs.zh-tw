---
title: 視覺化及檢視資料 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a88969139c993163c88f2dc16fc8cbdb7a62feb6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202770"
---
# <a name="visualizing-and-viewing-data"></a>視覺化及檢視資料
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

類型視覺化檢視和自訂檢視器中的開發人員快速有意義的方式呈現的資料。 運算式評估工具 (EE) 可支援第三方類型視覺化檢視，以及提供它自己的自訂檢視器。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 決定多少類型視覺化檢視和自訂檢視器會與物件的型別相關聯藉由呼叫[GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)方法。 如果沒有至少一個類型的視覺化檢視或自訂檢視器，Visual Studio 會呼叫[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法來擷取這些視覺化檢視和檢視器的清單 (事實上，一份`CLSID`實作的 s視覺化檢視和檢視器） 並將它們呈現給使用者。  
  
## <a name="supporting-type-visualizers"></a>支援的類型視覺化檢視  
 有許多的 EE 必須實作以支援類型視覺化檢視的介面。 這些介面可以分成兩大類別： 這些清單類型視覺化檢視和存取的屬性資料。  
  
### <a name="listing-type-visualizers"></a>清單類型視覺化檢視  
 EE 支援列出在實作類型視覺化檢視`IDebugProperty3::GetCustomViewerCount`和`IDebugProperty3::GetCustomViewerList`。 這些方法都會傳遞至對應的方法呼叫[GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)並[GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)。  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)藉由呼叫取得[CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)。 這個方法會要求[IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)介面，這取自[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)介面傳遞給[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。 `IEEVisualizerServiceProvider::CreateVisualizerService` 也需要[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)並[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)介面可傳遞至`IDebugParsedExpression::EvaluateSync`。 若要建立所需的最後一個介面`IEEVisualizerService`介面[IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) EE 實作的介面。 這個介面允許對正在視覺化的屬性所做的變更。 屬性的所有資料會都封裝在[IDebugObject](../../extensibility/debugger/reference/idebugobject.md) EE 也實作的介面。  
  
### <a name="accessing-property-data"></a>存取屬性資料  
 存取屬性資料透過[IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面。 若要取得這個介面，Visual Studio 會呼叫[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)要取得的屬性物件上[IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)介面 (可實作相同物件上實作[IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)介面)，然後呼叫[GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)方法，以取得`IPropertyProxyEESide`介面。  
  
 所有的資料傳遞傳入和傳出`IPropertyProxyEESide`介面會封裝在[IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)介面。 此介面會表示為位元組陣列，而且由 Visual Studio 和 EE 實作。 若要變更屬性的資料時，Visual Studio 會建立`IEEDataStorage`保留新的資料和呼叫的物件[CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)與該資料物件，以取得新`IEEDataStorage`物件，接著，傳遞給[InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)來更新屬性的資料。 `IPropertyProxyEESide::CreateReplacementObject` 可讓它自己實作的類別具現化 EE`IEEDataStorage`介面。  
  
## <a name="supporting-custom-viewers"></a>支援的自訂檢視器  
 旗標`DBG_ATTRIB_VALUE_CUSTOM_VIEWER`中設定`dwAttrib`欄位[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)結構 (藉由呼叫傳回[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) 來表示物件是否具有相關聯的自訂檢視器使用它。 當設定這個旗標時，會取得 Visual Studio [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)從介面[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面使用[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)。  
  
 如果使用者選取自訂檢視器，Visual Studio 會具現化使用檢視器的自訂檢視器`CLSID`所提供`IDebugProperty3::GetCustomViewerList`方法。 Visual Studio 接著會呼叫[DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)來向使用者顯示的值。  
  
 一般來說，`IDebugCustomViewer::DisplayValue`呈現資料的唯讀檢視。 若要讓資料變更，EE 必須實作自訂介面屬性物件上支援變更的資料。 `IDebugCustomViewer::DisplayValue`方法會使用這個自訂的介面，以支援的資料變更。 方法會尋找自訂介面`IDebugProperty2`當做傳入介面`pDebugProperty`引數。  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>同時支援輸入視覺化檢視和自訂檢視器  
 類型視覺化檢視和自訂檢視器中的，可支援 EE [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)並[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法。 首先，EE 會將它提供的自訂檢視器的數目所傳回的值加入[GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)方法。 第二，將附加 EE`CLSID`自己的自訂檢視器，以所傳回的清單之[GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)   
 [類型視覺化檢視和自訂檢視器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

