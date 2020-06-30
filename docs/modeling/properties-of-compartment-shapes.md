---
title: 區間圖案的屬性
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51b652adcc482d6e326c0b64eda3a9d32efab309
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532285"
---
# <a name="properties-of-compartment-shapes"></a>區間圖案的屬性
區間圖形是您可以用來以特定領域語言顯示網域類別的其中一種圖形。 您可以展開和折迭區間。

 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 區間圖形具有下表所列的屬性。

|屬性|描述|預設|
|-|-|-|
|預設展開折迭狀態|如果 `Expanded` 為，則會在建立時顯示區間。 如果 `Collapsed` 為，則為，否則為。|展開|
|填滿色彩|此圖形的填滿色彩。|白色|
|填滿漸層模式|此圖形的填滿漸層模式。|水平|
|幾何|這個形狀的幾何（矩形或圓角矩形）。|矩形|
|具有預設連接點|如果 `True` 為，則圖形會在產生的設計工具中使用上、下、左和右連接點。|False|
|是否顯示單一區間標頭|如果 `False` 和圖形具有單一區間，則不會顯示區間的標頭。|True|
|外框色彩|此圖形的外框色彩。|黑色|
|外框虛線樣式|此圖形的外框虛線樣式（實線、虛線、點、點、DashDotDot、Custom）。|實線|
|外框粗細|此圖形的外框粗細。|0.03125|
|文字色彩|用於與此圖形相關聯之文字裝飾專案的色彩。|黑色|
|存取修飾詞|區間圖形（或）的存取層級 `public` `internal` 。|公用|
|自訂屬性|用來將屬性新增至從這個區間圖形產生的原始程式碼類別|\<none>|
|產生雙重衍生|如果為 `True` ，則會產生基類和部分類別（以支援透過覆寫的自訂）。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|有自訂的函數|如果為 `True` ，則會在原始程式碼中提供自訂的函式。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|繼承修飾詞|描述從區間圖形（或）產生之原始程式碼類別的繼承類型 `none` `abstract` `sealed` 。|None|
|基底區間圖形|這個圖形的基類。|(無)|
|名稱|這個圖形的名稱。|目前名稱|
|命名空間|與這個圖形關聯的命名空間。|目前的命名空間|
|工具提示類型|工具提示的定義方式（[固定]、[變數] 或 [無]）。 若已修正，則 `Fixed Tooltip Text` 會使用屬性的值做為工具提示; 如果變數，則會在自訂程式碼中定義工具提示。|無|
|注意|與此圖形相關聯的非正式附注。|\<none>|
|初始高度|此圖形的初始高度（以英寸為單位）。 針對區間圖形，這是標頭區段的高度，而且無法調整大小。|1|
|初始寬度|此圖形的初始寬度（以英寸為單位）。|1.5|
|已公開填滿色彩做為屬性<br /><br /> 公開填滿漸層模式<br /><br /> 公開大綱色彩做為屬性<br /><br /> 將大綱虛線樣式公開為屬性<br /><br /> 公開大綱粗細做為屬性<br /><br /> 公開文字色彩|如果為 `True` ，則使用者可以設定圖形的指定屬性。 若要進行此設定，請以滑鼠右鍵按一下圖形定義，然後按一下 [新增] [**公開**]。|False|
|描述|用來記錄產生的設計工具。|\<none>|
|顯示名稱|將在產生的設計工具中顯示此圖形的名稱。|\<none>|
|已修正工具提示文字|用於固定工具提示的文字。|\<none>|
|說明關鍵字|用來為此圖形的 F1 說明編制索引的關鍵字。|\<none>|

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)