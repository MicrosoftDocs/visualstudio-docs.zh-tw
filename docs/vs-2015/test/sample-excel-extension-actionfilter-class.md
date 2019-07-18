---
title: 範例 Excel 延伸模組：ActionFilter 類別 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86c1dda46ed0e62649a576a12c9f9e48561ec891
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158169"
---
# <a name="sample-excel-extension-actionfilter-class"></a>範例 Excel 延伸模組：ActionFilter 類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此內部類別延伸 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> 類別，並代表 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 項目之測試動作的篩選。  
  
## <a name="simple-properties"></a>簡單屬性  
 這些唯讀屬性可讓開發人員指定自動程式化 UI 測試架構執行此測試動作篩選條件的方式。 例如，<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> 屬性提供動作篩選的名稱。 其他屬性會取得動作篩選的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>、此測試動作篩選所篩選之測試動作的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> 名稱。 其他則指出 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> 和測試動作是否都是 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>。  
  
## <a name="processrule-method"></a>ProcessRule 方法  
 此方法是由自動程式化 UI 測試架構所呼叫，並對提供的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> 執行篩選。 這個特定的覆寫會在堆疊中的下一個動作傳送按鍵動作至儲存格時，移除儲存格上的滑鼠選擇動作。 然後它會傳回 `false`。  
  
## <a name="private-methods"></a>私用方法  
 `IsLeftClick` 方法會判斷提供的動作是否代表按下滑鼠左鍵。 `AreActionsOnSameExcelCell` 方法會判斷兩個提供的動作是否在 Excel 中的同一個儲存格上執行。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [擴充自動程式化 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
