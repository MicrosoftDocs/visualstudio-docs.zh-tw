---
title: 幾何圖案的屬性
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb1088dafea1c43e624d029de6b890c9b597b061
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658182"
---
# <a name="properties-of-geometry-shapes"></a>幾何圖案的屬性
您可以使用 geometry 圖形來指定如何以特定領域語言來顯示網域類別的實例。 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 Geometry 圖形具有下表所列的屬性。

|屬性|描述|Default|
|-|-|-|
|填滿色彩|此圖形的填滿色彩。|份|
|填滿漸層模式|這個形狀的填滿漸層模式（水準、垂直、正斜線、向後對角線或無）。|水平|
|性質|這個形狀的幾何（矩形、圓角矩形、橢圓形或圓形）。|矩形|
|具有預設連接點|如果 `True`，圖形將會在產生的設計工具中使用頂端、下、左和右連接點。|False|
|外框色彩|此圖形的外框色彩。|黑色|
|外框虛線樣式|此圖形的外框虛線樣式（實線、虛線、點、點、DashDotDot 或自訂）。|實線|
|外框粗細|此圖形的外框粗細。|0.03125|
|文字色彩|用於與此圖形相關聯之文字裝飾專案的色彩。|黑色|
|存取修飾詞|類別的存取修飾詞（公用或內部）。|Public|
|自訂屬性|用來將屬性新增至為此圖形產生的原始程式碼類別。|\<無>|
|產生雙重衍生|如果 `True`，則會產生基類和部分類別（以支援透過覆寫的自訂）。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|有自訂的函數|如果 `True`，則會在原始程式碼中提供自訂的函式。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|繼承修飾詞|描述從圖形（`none`、`abstract` 或 `sealed`）產生之原始程式碼類別的繼承類型。|none|
|基底幾何圖形|這個圖形的基類。|(無)|
|[屬性]|這個圖形的名稱。|目前名稱|
|命名空間|與這個圖形關聯的命名空間。|目前的命名空間|
|工具提示類型|工具提示的定義方式（[固定]、[變數] 或 [無]）。 若已修正，則會使用 `Fixed Tooltip Text` 屬性的值做為工具提示;如果變數，則會在自訂程式碼中定義工具提示。|None|
|備註|與此元素相關聯的非正式附注。|\<無>|
|初始高度|此圖形的初始高度（以英寸為單位）。|1|
|初始寬度|此圖形的初始寬度（以英寸為單位）。|1.5|
|已公開填滿色彩做為屬性<br /><br /> 公開填滿漸層模式<br /><br /> 公開大綱色彩做為屬性<br /><br /> 將大綱虛線樣式公開為屬性<br /><br /> 公開大綱粗細做為屬性<br /><br /> 公開文字色彩|如果 `True`，使用者可以設定圖形的 [所述] 屬性。 若要進行此設定，請以滑鼠右鍵按一下圖形定義，然後按一下 [新增] [**公開**]。|False|
|描述|用來記錄產生的設計工具的描述。|\<無>|
|顯示名稱|將在產生的設計工具中顯示此圖形的名稱。|\<無>|
|已修正工具提示文字|用於固定工具提示的文字。|\<無>|
|說明關鍵字|用來為此圖形的 F1 說明編制索引的關鍵字。|\<無>|

## <a name="see-also"></a>請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)