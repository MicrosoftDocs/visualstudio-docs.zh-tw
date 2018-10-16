---
title: 範例 Excel 擴充功能：TechnologyManager 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: b23c3e735aba74d86b31afb4b83862d83bcd2bdb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190576"
---
# <a name="sample-excel-extension-technologymanager-class"></a>範例 Excel 延伸模組：TechnologyManager 類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此類別會擴充 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> 類別，並負責提供 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 延伸模組的核心服務。 雖然基底類別有許多方法，但在這個範例中只會使用一部分的子集。  
  
 有些方法只會傳回屬性值。 許多方法是為了讓開發人員覆寫內建於自動程式化 UI 測試引擎中的預設演算法。 這些方法會擲回 <xref:System.NotSupportedException> 或傳回 `null`，告知架構應使用預設演算法。  
  
 根據基礎技術的複雜度，開發技術管理員程式碼可能會需要數星期到數月之久。 Excel 能提供建立涵蓋可能非常廣泛之技術管理員的機會。 這個範例故意局限於 Excel 工作表和儲存格，並使用有限的格式。  
  
 可能的話，技術管理員程式碼會使用由 `Communicator` 類別開啟的 .NET Remoting 通道，以從執行於 Excel 處理序的增益集擷取資訊。  
  
## <a name="com-visibility"></a>COM 可視性  
 請注意，此類別以及擴充 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 類別的每個項目類別都會有值為 `true` 的 <xref:System.Runtime.InteropServices.ComVisibleAttribute>，以確定 COM 可以看到這些類別。  
  
## <a name="technologyname-property"></a>TechnologyName 屬性  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> 屬性的這個覆寫必須提供唯一且有意義的名稱，以識別延伸模組之每個其他元件的基本技術。 對於這個擴充功能，值為 "Excel"。  
  
## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel 方法  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> 方法的這個覆寫會傳回數字，指出技術管理員可為所提供控制代碼代表之控制項提供的支援層級。 傳回的值越高，技術管理員可支援控制項的層級就越高。 在這個案例中，方法會檢查包含控制項的視窗，如果它是 Excel 工作表，方法就會傳回最高的值；否則會傳回零，表示不提供任何支援。  
  
## <a name="methods-to-get-an-element"></a>取得項目的方法  
 自動程式化 UI 測試架構使用數個重要方法，以取得技術特有的項目：藉由提供控制代碼、螢幕上的點，或是來自不同技術的項目。 這些方法的程式碼意義相當明顯。 基底方法如下：  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>ParseQueryId 方法  
 建立自動程式化 UI 測試時，使用者可以針對測試中部分或全部控制項指定屬性值。 測試架構會使用這些屬性值，建立稱為搜尋屬性的名稱值組，用來在測試期間尋找特定 UI 控制項。 所有搜尋屬性都代表技術中每個項目的 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> 屬性值，其中包含每個控制項。 因為在測試期間可能必須多次尋找控制項，所以這個方法可以讓技術管理員以最佳方式針對指定的控制項剖析搜尋屬性。 這個方法也會傳回 Cookie，讓架構在後續搜尋該控制項時可以使用它。 此方法的這個實作會使用 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> 方法來剖析搜尋屬性。  
  
## <a name="matchelement-method"></a>MatchElement 方法  
 若要執行技術管理員的控制項搜尋，您可以實作 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> 方法來傳回可能相符項目的陣列，或者擲回 <xref:System.NotSupportedException>，告知架構使用它自己的搜尋演算法。 任一方式，您都必須實作 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> 方法，而這項實作會再次使用 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> 方法。  
  
## <a name="navigation-methods"></a>Navigation 方法  
 這些方法會從 UI 階層取得所提供之項目的父代、子系或同層級。 程式碼很簡單並有清楚的註解。  
  
## <a name="getexcelelement-internal-method"></a>GetExcelElement 內部方法  
 這個內部方法會取得 Excel 項目的視窗控制代碼和資訊，並傳回要求的 Excel 項目。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [擴充自動程式化 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



