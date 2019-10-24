---
title: 泳道的屬性
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a21473f983c56181e3a5d2fc7f9e97cd1c2d6e7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748263"
---
# <a name="properties-of-swimlanes"></a>泳道的屬性
您可以將泳道新增至圖表。 泳道會將圖表分割成垂直或水準區域。 您可以定義其他要顯示在泳道內的圖形。 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 泳道具有下表所列的屬性。

|屬性|描述|Default|
|-|-|-|
|主體填滿色彩|泳道主體的填滿色彩。|份|
|標題填滿色彩|泳道標頭的填滿色彩。|DarkGray|
|分隔符號色彩|分隔線的色彩。|LightGray|
|分隔線樣式|分隔線的樣式（`Solid`、`Dash`、`Dot`、`DashDot`、`DashDotDot` 或 `Custom`）。|`Dash`|
|分隔符號粗細|分隔線的粗細（以英寸為單位）。|0.03125|
|文字色彩|用於與此泳道相關聯之文字裝飾專案的色彩。|黑色|
|存取修飾詞|類別的存取層級（`public` 或 `internal`）。|Public|
|自訂屬性|用來將屬性新增至此泳道所產生的程式碼類別。|\<無>|
|產生雙重衍生|如果 `True`，則會產生基類和部分類別（以支援透過覆寫的自訂）。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|有自訂的函數|如果 `True`，則會在原始程式碼中提供自訂的函式。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|繼承修飾詞|描述從泳道產生之原始程式碼類別的繼承類型（`none`、`abstract` 或 `sealed`）。|none|
|基底泳道|此泳道的基類。|(無)|
|[屬性]|此泳道的名稱。|目前名稱|
|命名空間|與這個泳道關聯的命名空間。|目前的命名空間|
|工具提示類型|如何定義工具提示（`fixed`、`variable` 或 `none`）。 如果 `fixed`，則會使用 `Fixed Tooltip Text` 屬性的值。如果 `variable`，則會在自訂程式碼中定義工具提示。|\<無>|
|備註|與這個泳道相關聯的非正式附注。|\<無>|
|對齊|水準或垂直對齊。|垂直|
|初始高度|此泳道的初始高度（以英寸為單位）。 僅適用于水準泳道。|0|
|初始寬度|此泳道的初始寬度（以英寸為單位）。 僅適用于垂直泳道。|0|
|公開文字色彩|如果 `True`，則使用者可以在產生的設計工具中設定泳道的色彩。 若要進行此設定，請以滑鼠右鍵按一下 [泳道] 圖形，然後按一下 [**加入公開**]。|False|
|描述|用來記錄產生的設計工具。|\<無>|
|顯示名稱|將在產生的設計工具中顯示的名稱，以參考此泳道類別。|\<無>|
|已修正工具提示文字|用於固定工具提示的文字。|\<無>|
|說明關鍵字|用來為此泳道的 F1 說明編制索引的關鍵字。|\<無>|

## <a name="see-also"></a>請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)