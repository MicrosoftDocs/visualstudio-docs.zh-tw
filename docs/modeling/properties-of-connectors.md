---
title: 接點的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 754f479b99eef44159994425ddd7a0d812bcf2ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970805"
---
# <a name="properties-of-connectors"></a>接點的屬性
連接器會代表產生的設計工具中的網域關聯性。

 如需詳細資訊，請參閱 <<c0> [ 如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 連接器有下列表格中所列的屬性。

|屬性|描述|預設|
|-|-|-|
|色彩|此連接器的色彩。|黑色|
|虛線樣式|此連接器 （實線、 虛線、 點、 線、 虛線點點或自訂） 的列虛線樣式。|實線|
|來源端樣式|（HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond、 FilledDiamond，或無） 此接點來源端樣式。|None|
|目標端樣式|（HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond、 FilledDiamond，或無） 此接點目標端樣式。|None|
|文字色彩|使用此連接器與相關聯的文字裝飾項目的色彩。|黑色|
|Thickness|這個連接器的線條的粗細，單位為英吋。|0.03125|
|存取修飾詞|類別的存取層級 (`public`或`internal`)。|Public|
|自訂屬性|用來將屬性加入至來源的程式碼類別，產生來自此連接器。|\<無>|
|產生雙衍生|如果`True`，將產生的基底類別和部分類別 （以支援透過覆寫自訂）。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|具有自訂建構函式|如果`True`，以原始碼提供自訂建構函式。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|繼承修飾詞|描述從連接器會產生來源的程式碼類別繼承的類型 (`none`，`abstract`或`sealed`)。|none|
|基底接點|此接點的基底類別。|(無)|
|名稱|此連接器的名稱。|目前的名稱|
|命名空間|此連接器附屬於命名空間。|目前的命名空間|
|工具提示類型|（固定、 變數或 none） 」 來定義 「 工具提示的方式。 如果固定，則值`Fixed Tooltip Text`屬性做為工具提示; 若變數，然後工具提示中定義的自訂程式碼。|\<無>|
|注意|此連接器與相關聯的非正式附註。|\<無>|
|路徑樣式|用於路由接點的樣式。 A`Rectilinear`連接器可讓直角會視需要;`Straight`連接器不會執行。|直線形|
|公開為屬性的色彩<br /><br /> 當做屬性公開的虛線樣式<br /><br /> 公開為屬性的粗細<br /><br /> 公開 （expose) 的文字色彩|如果`True`，使用者可以設定圖形的所述的屬性。 若要設定這種情況，請以滑鼠右鍵按一下圖形定義，然後按一下**加入已公開**。|False|
|描述|用來產生的設計工具的文件。|\<無>|
|顯示名稱|將會顯示在產生的設計工具，此連接器的名稱。|\<無>|
|固定的工具提示文字|用於固定工具提示文字。|\<無>|
|說明關鍵字|用來編製索引的這個項目 F1 說明關鍵字。|\<無>|

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)