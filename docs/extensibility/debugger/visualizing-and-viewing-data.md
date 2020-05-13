---
title: 視覺化和查看資料 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b5f984e6c6a3c1c8f3835dfa93a8679ae16680a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712369"
---
# <a name="visualizing-and-viewing-data"></a>視覺化與檢視資料
鍵入可視化工具並自定義查看器以對開發人員來說快速有意義的方式呈現數據。 運算式賦值器 (EE) 可以支援第三方類型可視化器,以及提供自己的自定義檢視器。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通過調用[GetCustomViewerCount 方法](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)確定與物件類型關聯的類型可視化器和自定義查看器的數量。 如果至少有一種類型可視化工具或自定義查看器可用,Visual Studio 調用[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法來檢索這些可視化工具和查看器的清單(實際上,是實現可視化器和查看器的 s 清單),並將其呈現給使用者。

## <a name="supporting-type-visualizers"></a>支援類型視覺化工具
 EE 必須實現許多介面來支援類型可視化工具。 這些介面可以分為兩大類:列出類型可視化器的介面和訪問屬性數據的介面。

### <a name="listing-type-visualizers"></a>清單類型視覺化工具
 EE 支援在其`IDebugProperty3::GetCustomViewerCount``IDebugProperty3::GetCustomViewerList`實現和 中列出類型可視化器。 這些方法將呼叫傳遞給相應的方法[GetCustomViewer( GetCustomViewer) Count 和](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) [getCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)。

 [IEE可視化服務](../../extensibility/debugger/reference/ieevisualizerservice.md)是通過調用[創建可視化服務](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)獲得的。 此方法需要[IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)介面,該介面是從傳遞給[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)的[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)介面獲得的。 `IEEVisualizerServiceProvider::CreateVisualizerService`需要[IDebugSymbol 提供者](../../extensibility/debugger/reference/idebugsymbolprovider.md)與[IDebug 位址](../../extensibility/debugger/reference/idebugaddress.md)`IDebugParsedExpression::EvaluateSync`介面,這些介面已傳遞到 。 創建`IEEVisualizerService`介面所需的最終介面是 EE 實現的[IEEVisualizer 資料提供程式](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)介面。 此介面允許對要可視化的屬性進行更改。 所有屬性數據都封裝在[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)介面中,該介面也由 EE 實現。

### <a name="accessing-property-data"></a>存取屬性資料
 訪問屬性數據是透過[IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面完成的。 要獲取此介面,Visual Studio 調用屬性物件的[QueryInterface](/cpp/atl/queryinterface)以獲取[IProperty Proxy Provider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)介面(實現在實現[IDebug Property3](../../extensibility/debugger/reference/idebugproperty3.md)介面的同一物件上),然後調用[GetProperty Proxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)方法`IPropertyProxyEESide`以獲取該介面。

 傳入和流出介面的`IPropertyProxyEESide`所有數據都封裝在[IEEDataStorage介面](../../extensibility/debugger/reference/ieedatastorage.md)中。 此介面表示位元組,由 Visual Studio 和 EE 實現。 更改屬性資料時,Visual `IEEDataStorage` Studio 會建立一個包含新資料的物件,並調用[CreateCreate 替代物件](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md),`IEEDataStorage`以便獲取一個新 物件,該物件又傳遞到[InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)以更新屬性的數據。 `IPropertyProxyEESide::CreateReplacementObject`允許 EE 實例`IEEDataStorage`化實現 介面的自身類。

## <a name="supporting-custom-viewers"></a>支援自訂檢視器
 標誌`DBG_ATTRIB_VALUE_CUSTOM_VIEWER``dwAttrib`在[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)結構的欄位中設定(透過呼叫[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)傳回)來指示物件具有與其關聯的自訂檢視器。 設置此標誌時,Visual Studio 使用[查詢介面](/cpp/atl/queryinterface)從[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面獲取[IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)介面。

 如果用戶選擇自定義檢視器,Visual Studio`CLSID``IDebugProperty3::GetCustomViewerList`將使用 該方法提供的查看器實例化自定義查看器。 然後,視覺化工作室調用[DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)向用戶顯示該值。

 通常,`IDebugCustomViewer::DisplayValue`顯示數據的唯讀檢視。 要允許對數據進行更改,EE 必須實現一個自定義介面,該介面支援更改屬性物件上的數據。 該方法`IDebugCustomViewer::DisplayValue`使用此自定義介面支援更改數據。 該方法查找作為`IDebugProperty2``pDebugProperty`參數傳入的介面上的自定義介面。

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>支援類型視覺化器和自訂檢視器
 EE 可以在[GetCustomViewerCount 和](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)[獲取自訂檢視器清單](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法中同時支援類型可視化器和自定義查看器。 首先,EE 會將其提供的自定義查看器數添加到[GetCustomViewerCount 方法](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)返回的值。 其次,EE 將自己的自`CLSID`定義 檢視器的 s 追加到[GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)方法返回的清單。

## <a name="see-also"></a>另請參閱
- [除錯工作](../../extensibility/debugger/debugging-tasks.md)
- [類型視覺化器和自訂檢視器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
