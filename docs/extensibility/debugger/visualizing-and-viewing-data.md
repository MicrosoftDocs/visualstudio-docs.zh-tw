---
title: 視覺化和查看資料 |Microsoft Docs
description: 瞭解型別視覺化和自訂檢視器如何將資料呈現給開發人員。 運算式評估工具支援協力廠商型別視覺化檢視。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 61c2094564ea20c1073a198c3da162862c543e65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965352"
---
# <a name="visualizing-and-viewing-data"></a>視覺化和查看資料
鍵入視覺化程式和自訂檢視器，以對開發人員快速有意義的方式呈現資料。 運算式評估工具 (EE) 可以支援協力廠商類型的視覺化檢視，以及提供自己的自訂檢視器。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 藉由呼叫 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 方法，判斷有多少類型的視覺化程式和自訂檢視器與物件的型別相關聯。 如果至少有一個類型的視覺化檢視或自訂檢視器可供使用，Visual Studio 會呼叫 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 方法來取出這些視覺化程式和檢視器的清單 (實際的清單，這些會執行視覺化程式和) 檢視器，並將其呈現給使用者。

## <a name="supporting-type-visualizers"></a>支援型別視覺化
 EE 必須實行一些介面，才能支援型別視覺化檢視。 這些介面可以分為兩個廣泛的類別：列出可存取屬性資料之視覺化程式和介面的介面。

### <a name="listing-type-visualizers"></a>清單類型視覺化
 EE 支援在和的實作為型別視覺化程式 `IDebugProperty3::GetCustomViewerCount` 清單 `IDebugProperty3::GetCustomViewerList` 。 這些方法會將呼叫傳遞給對應的 [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) 和 [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)方法。

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)是藉由呼叫[CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)來取得。 這個方法需要[IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)介面，此介面是從傳遞至[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)的[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)介面取得的。 `IEEVisualizerServiceProvider::CreateVisualizerService` 也需要將 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) 和 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 介面傳遞給 `IDebugParsedExpression::EvaluateSync` 。 建立介面所需的最終介面 `IEEVisualizerService` 是 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 介面，也就是 EE 所實行的介面。 這個介面可讓您對要視覺化的屬性進行變更。 所有屬性資料都會封裝在 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 介面中，這也是由 EE 所執行。

### <a name="accessing-property-data"></a>存取屬性資料
 存取屬性資料是透過 [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) 介面來完成。 為了取得這個介面，Visual Studio 會在屬性物件上呼叫 [QueryInterface](/cpp/atl/queryinterface) 來取得 [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) 介面， (在實 [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) 介面的相同物件上實作為) ，然後呼叫 [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 方法來取得 `IPropertyProxyEESide` 介面。

 傳入和傳出介面的所有資料 `IPropertyProxyEESide` 都會封裝在 [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) 介面中。 這個介面代表位元組陣列，且是由 Visual Studio 和 EE 所執行。 當屬性的資料變更時，Visual Studio 會建立 `IEEDataStorage` 保存新資料的物件，並以該資料物件呼叫 [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) ，以便取得新的物件，而 `IEEDataStorage` 該物件接著會傳遞至 [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) 來更新屬性的資料。 `IPropertyProxyEESide::CreateReplacementObject` 允許 EE 具現化其本身的類別來實 `IEEDataStorage` 介面。

## <a name="supporting-custom-viewers"></a>支援自訂檢視器
 旗 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` 標設定于 `dwAttrib` [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 結構的欄位中， (由 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) 的呼叫所傳回，表示該物件具有與其相關聯的自訂檢視器。 當設定這個旗標時，Visual Studio 會使用[QueryInterface](/cpp/atl/queryinterface)從[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面取得[IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)介面。

 如果使用者選取自訂檢視器，Visual Studio 會使用方法所提供的檢視器來具現化自訂檢視器 `CLSID` `IDebugProperty3::GetCustomViewerList` 。 Visual Studio 接著會呼叫 [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) 來向使用者顯示值。

 通常會 `IDebugCustomViewer::DisplayValue` 提供資料的唯讀視圖。 若要允許變更資料，EE 必須執行支援變更屬性物件資料的自訂介面。 `IDebugCustomViewer::DisplayValue`方法會使用這個自訂介面來支援變更資料。 方法會在傳入做為引數的介面上尋找自訂介面 `IDebugProperty2` `pDebugProperty` 。

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>支援型別視覺化器和自訂檢視器
 EE 可同時支援 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 和 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 方法中的型別視覺化程式和自訂檢視器。 首先，EE 會將它所提供的自訂檢視器數目，加入至 [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) 方法所傳回的值。 其次，EE 會將 `CLSID` 其自訂檢視器的 s 附加至 [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) 方法所傳回的清單。

## <a name="see-also"></a>另請參閱
- [調試作業](../../extensibility/debugger/debugging-tasks.md)
- [型別視覺化器和自訂檢視器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
