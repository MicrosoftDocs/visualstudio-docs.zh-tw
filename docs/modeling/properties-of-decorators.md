---
title: Decorator 的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 567cba4be2d225985b5a6d690f0d8264f24190f4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747495"
---
# <a name="properties-of-decorators"></a>Decorator 的屬性
裝飾專案是可在圖表上的圖形或接點上出現的圖示、文字或展開/折迭符號。 下表顯示三種裝飾專案的屬性。 某些屬性只會出現在 [圖形] 裝飾專案或 [連接器] 裝飾專案上。

 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

## <a name="expandcollapse-decorator"></a>展開/折迭裝飾專案

|屬性|描述|Default|
|-|-|-|
|DisplayName|將顯示在產生的設計工具中的裝飾專案名稱。|展開折迭裝飾專案|
|[屬性]|裝飾專案的名稱。|ExpandCollapseDecorator|
|備註|與這個裝飾專案相關聯的非正式附注。|\<無>|
|System.windows.controls.primitives.popup.horizontaloffset|相對於裝飾專案之預設位置的水準位移（以英寸為單位）。 （僅適用于圖形）。|0|
|VerticalOffset|相對於裝飾專案之預設位置的垂直位移（以英寸為單位）。 （僅適用于圖形）。|0|
|OffsetFromLine|線條的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|OffsetFromShape|圖形的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|位置|裝飾專案的預設位置。|SourceTop|

## <a name="icon-decorator"></a>圖示裝飾專案

|屬性|描述|Default|
|-|-|-|
|DefaultIcon|要顯示之圖示或影像檔案的路徑。|\<無>|
|DisplayName|要在產生的設計工具中顯示之裝飾專案的名稱。|圖示裝飾專案|
|[屬性]|裝飾專案的名稱。|IconDecorator|
|備註|與裝飾專案相關聯的非正式附注。|\<無>|
|System.windows.controls.primitives.popup.horizontaloffset|相對於裝飾專案之預設位置的水準位移（以英寸為單位）。 （僅適用于圖形）。|0|
|VerticalOffset|相對於裝飾專案之預設位置的垂直位移（以英寸為單位）。 （僅適用于圖形）。|0|
|OffsetFromLine|線條的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|OffsetFromShape|圖形的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|位置|裝飾專案的預設位置。|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|屬性|描述|Default|
|-|-|-|
|DefaultText|要顯示的預設文字。|ThisAddIn|
|DisplayName|要在產生的設計工具中顯示之裝飾專案的名稱。|ThisAddIn|
|FontSize|裝飾專案中顯示之文字的字型大小。|8|
|FontStyle|裝飾專案中顯示之文字的字型樣式。|Regular|
|[屬性]|裝飾專案的名稱。|ThisAddIn|
|備註|與裝飾專案相關聯的非正式附注。|\<無>|
|System.windows.controls.primitives.popup.horizontaloffset|相對於裝飾專案之預設位置的水準位移（以英寸為單位）。 （僅適用于圖形）。|0|
|VerticalOffset|相對於裝飾專案之預設位置的垂直位移（以英寸為單位）。 （僅適用于圖形）。|0|
|OffsetFromLine|線條的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|OffsetFromShape|圖形的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|位置|裝飾專案的預設位置。|TargetBottom|

## <a name="see-also"></a>請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)