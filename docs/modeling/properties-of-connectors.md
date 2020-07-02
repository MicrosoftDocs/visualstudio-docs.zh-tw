---
title: 接點的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7bf5492d7da845b65904959cb57737fd438c28b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532271"
---
# <a name="properties-of-connectors"></a>接點的屬性
連接器代表產生的設計工具中的網域關聯性。

 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 連接器具有下表所列的屬性。

|屬性|描述|預設|
|-|-|-|
|Color|此連接器的色彩。|黑色|
|虛線樣式|此連接器線條的虛線樣式（實線、虛線、點、點、DashDotDot 或自訂）。|實線|
|來源結束樣式|此連接器的來源結束樣式（HollowArrow、EmptyArrow、FilledArrow、EmptyDiamond、FilledDiamond 或 None）。|None|
|目標結束樣式|此連接器的目標端樣式（HollowArrow、EmptyArrow、FilledArrow、EmptyDiamond、FilledDiamond 或 None）。|None|
|文字色彩|用於與此連接器相關聯之文字裝飾專案的色彩。|黑色|
|Thickness|此接點的線條粗細（以英寸為單位）。|0.03125|
|存取修飾詞|類別（或）的存取層級 `public` `internal` 。|公用|
|自訂屬性|用來將屬性新增至此連接器所產生的原始程式碼類別。|\<none>|
|產生雙重衍生|如果為 `True` ，則會產生基類和部分類別（以支援透過覆寫的自訂）。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|有自訂的函數|如果為 `True` ，則會在原始程式碼中提供自訂的函式。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|繼承修飾詞|描述從連接器（或）產生之原始程式碼類別的繼承類型 `none` `abstract` `sealed` 。|無|
|基底連接器|此連接器的基類。|(無)|
|名稱|此連接器的名稱。|目前名稱|
|命名空間|與此連接器關聯的命名空間。|目前的命名空間|
|工具提示類型|工具提示的定義方式（[固定]、[變數] 或 [無]）。 若已修正，則 `Fixed Tooltip Text` 會使用屬性的值做為工具提示; 如果變數，則會在自訂程式碼中定義工具提示。|\<none>|
|注意|與此連接器相關聯的非正式附注。|\<none>|
|路由樣式|用來路由連接器的樣式。 連接器會將 `Rectilinear` 右角轉變成必要; 連接器則 `Straight` 不會。|折線|
|公開色彩做為屬性<br /><br /> 以屬性形式公開的虛線樣式<br /><br /> 以屬性形式公開的粗細<br /><br /> 公開文字色彩|如果為 `True` ，則使用者可以設定圖形的指定屬性。 若要進行此設定，請以滑鼠右鍵按一下圖形定義，然後按一下 [新增] [**公開**]。|False|
|描述|用來記錄產生的設計工具。|\<none>|
|顯示名稱|將在為此連接器產生的設計工具中顯示的名稱。|\<none>|
|已修正工具提示文字|用於固定工具提示的文字。|\<none>|
|說明關鍵字|用來為這個元素的 F1 說明編制索引的關鍵字。|\<none>|

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)