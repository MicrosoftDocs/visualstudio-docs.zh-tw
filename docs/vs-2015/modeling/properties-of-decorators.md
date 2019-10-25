---
title: 裝飾專案的屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb837c9b3d465d229f64fac08dac02af8d50f5fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652010"
---
# <a name="properties-of-decorators"></a>Decorator 的屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

裝飾專案是可在圖表上的圖形或接點上出現的圖示、文字或展開/折迭符號。 下表顯示三種裝飾專案的屬性。 某些屬性只會出現在 [圖形] 裝飾專案或 [連接器] 裝飾專案上。

 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

## <a name="expandcollapse-decorator"></a>展開/折迭裝飾專案

|屬性|描述|預設|
|--------------|-----------------|-------------|
|DisplayName|將顯示在產生的設計工具中的裝飾專案名稱。|展開折迭裝飾專案|
|名稱|裝飾專案的名稱。|ExpandCollapseDecorator|
|注意|與這個裝飾專案相關聯的非正式附注。|\<無>|
|System.windows.controls.primitives.popup.horizontaloffset|相對於裝飾專案之預設位置的水準位移（以英寸為單位）。 （僅適用于圖形）。|0|
|VerticalOffset|相對於裝飾專案之預設位置的垂直位移（以英寸為單位）。 （僅適用于圖形）。|0|
|OffsetFromLine|線條的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|OffsetFromShape|圖形的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|位置|裝飾專案的預設位置。|SourceTop|

## <a name="icon-decorator"></a>圖示裝飾專案

|屬性|描述|預設|
|--------------|-----------------|-------------|
|DefaultIcon|要顯示之圖示或影像檔案的路徑。|\<無>|
|DisplayName|要在產生的設計工具中顯示之裝飾專案的名稱。|圖示裝飾專案|
|名稱|裝飾專案的名稱。|IconDecorator|
|注意|與裝飾專案相關聯的非正式附注。|\<無>|
|System.windows.controls.primitives.popup.horizontaloffset|相對於裝飾專案之預設位置的水準位移（以英寸為單位）。 （僅適用于圖形）。|0|
|VerticalOffset|相對於裝飾專案之預設位置的垂直位移（以英寸為單位）。 （僅適用于圖形）。|0|
|OffsetFromLine|線條的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|OffsetFromShape|圖形的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|位置|裝飾專案的預設位置。|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|屬性|描述|預設|
|--------------|-----------------|-------------|
|DefaultText|要顯示的預設文字。|ThisAddIn|
|DisplayName|要在產生的設計工具中顯示之裝飾專案的名稱。|ThisAddIn|
|FontSize|裝飾專案中顯示之文字的字型大小。|8|
|FontStyle|裝飾專案中顯示之文字的字型樣式。|Regular|
|名稱|裝飾專案的名稱。|ThisAddIn|
|注意|與裝飾專案相關聯的非正式附注。|\<無>|
|System.windows.controls.primitives.popup.horizontaloffset|相對於裝飾專案之預設位置的水準位移（以英寸為單位）。 （僅適用于圖形）。|0|
|VerticalOffset|相對於裝飾專案之預設位置的垂直位移（以英寸為單位）。 （僅適用于圖形）。|0|
|OffsetFromLine|線條的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|OffsetFromShape|圖形的裝飾專案相對於其預設位置的位移（以英寸為單位）。 （僅限在連接器上）。|0|
|位置|裝飾專案的預設位置。|TargetBottom|

## <a name="see-also"></a>另請參閱
 [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)
