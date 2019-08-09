---
title: 範例 Excel 延伸模組:ActionFilter 類別 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26eb001de3a8fed7c6bb1d9d1a547aa618e745e8
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871608"
---
# <a name="sample-excel-extension-actionfilter-class"></a>範例 Excel 延伸模組:ActionFilter 類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

這個內部類別會擴充[microsoft.visualstudio.testtools.uitest.common.uitestactionfilter>](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))類別, 並代表[!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]元素上測試動作的篩選。

## <a name="simple-properties"></a>簡單屬性
 這些唯讀屬性可讓開發人員指定自動程式化 UI 測試架構執行此測試動作篩選條件的方式。 例如，`UITestActionFilter.Name` 屬性提供動作篩選的名稱。 其他屬性會取得動作篩選的 `UITestActionFilter.Category`、`UITestActionFilter.FilterType`、此測試動作篩選所篩選之測試動作的 `UITestActionFilter.Group` 名稱。 其他則指出 `UITestActionFilter.ApplyTimeout` 和測試動作是否都是 `UITestActionFilter.Enabled`。

## <a name="processrule-method"></a>ProcessRule 方法
 此方法是由自動程式化 UI 測試架構所呼叫，並對提供的 `IUITestActionStack` 執行篩選。 這個特定的覆寫會在堆疊中的下一個動作傳送按鍵動作至儲存格時，移除儲存格上的滑鼠選擇動作。 然後它會傳回 `false`。

## <a name="private-methods"></a>私用方法
 `IsLeftClick` 方法會判斷提供的動作是否代表按下滑鼠左鍵。 `AreActionsOnSameExcelCell` 方法會判斷兩個提供的動作是否在 Excel 中的同一個儲存格上執行。

## <a name="see-also"></a>另請參閱

- [擴充自動程式化 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
