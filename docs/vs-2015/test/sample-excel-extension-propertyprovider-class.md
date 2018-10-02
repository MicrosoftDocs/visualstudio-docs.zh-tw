---
title: 範例 Excel 擴充功能：PropertyProvider 類別 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: d421f4f5b2f5fbdb2f78c6b72830ac8722e56aa2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499127"
---
# <a name="sample-excel-extension-propertyprovider-class"></a>範例 Excel 延伸模組：PropertyProvider 類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[範例 Excel 延伸模組： PropertyProvider 類別](https://docs.microsoft.com/visualstudio/test/sample-excel-extension-propertyprovider-class)。  
  
這個內部類別會擴充 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> 類別，並且為 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 項目提供屬性服務，以記錄和播放使用者介面 (UI) 測試。  
  
## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel 方法  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> 方法會傳回數字，指出屬性提供者可針對所提供控制項提供的支援層級。 傳回的值越高，屬性提供者可支援控制項的層級就越高。 在此情況下，這個方法會檢查所提供控制項的 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> 屬性值。 如果此值為 "Excel" 而且 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> 指出它是 `CellElement`，這個方法就會傳回最高值；否則會傳回零，指出不提供任何支援。  
  
## <a name="getpropertynames-method"></a>GetPropertyNames 方法  
 針對支援的 Excel 儲存格控制項屬性傳回屬性名稱和屬性描述元的字典。  
  
## <a name="getpropertydescriptor-method"></a>GetPropertyDescriptor 方法  
 這個方法是由測試架構呼叫，以便針對提供的屬性名稱取得預先定義的屬性描述元。  
  
## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>GetPropertyValue 和 SetPropertyValue 方法  
 `GetPropertyValue` 方法會使用此擴充功能的 `Communicator` 類別來傳回 Excel 中的屬性值。 `SetPropertyValue` 方法會使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> 類別和 `Communicator` 元件來設定屬性值。 這些方法是由測試架構呼叫。  
  
## <a name="code-generation-customization-methods"></a>程式碼產生自訂方法  
 這些方法並未針對此擴充功能實作。 因此，它們會傳回 `null` 或擲回 <xref:System.NotImplementedException>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [擴充自動程式化 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



