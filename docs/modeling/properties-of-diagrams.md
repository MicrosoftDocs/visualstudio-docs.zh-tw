---
title: 圖表的屬性
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f66c4597116c2dd27320a8ae0bf69314bbb558b4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="properties-of-diagrams"></a>圖表的屬性
您可以設定指定如何圖表會顯示在設計工具中產生的屬性。 例如，您可以指定文字的預設色彩在圖表中。

 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 下表列出的圖表的屬性。

|屬性|描述|預設|
|--------------|-----------------|-------------|
|填滿色彩|圖表的填滿色彩。|白色|
|文字色彩|顯示在圖表的文字色彩。|黑色|
|存取修飾詞|類別 （公用或內部） 的存取修飾詞。|Public|
|自訂屬性|用來將屬性加入至產生的程式碼類別。|\<無 >|
|會產生雙衍生|如果`True`，就會產生 （以支援自訂透過覆寫） 的部分類別和基底類別。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|具有自訂建構函式|如果`True`，會在原始程式碼中提供的自訂建構函式。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)...|False|
|繼承修飾詞|描述產生自圖表來源的程式碼類別的繼承種類 (`none`，`abstract`或`sealed`)。|無|
|基底的圖表|這個圖表基底類別。|(無)|
|名稱|此圖表的名稱。|目前的名稱|
|命名空間|這個圖表附屬於命名空間。|目前的命名空間|
|表示類別|這個圖代表根網域類別。|如果適用於目前的根類別|
|注意|這個項目相關聯的非正式附註。|\<無 >|
|會公開為屬性填滿色彩|如果`True`，使用者可以設定圖表設計工具產生的填滿色彩。 若要設定這種情況，以滑鼠右鍵按一下圖表圖形，並按一下**新增 Explosed**。|False|
|公開為屬性的文字色彩|如果`True`，使用者可以在產生的設計工具中設定圖表的文字色彩。 若要設定這種情況，以滑鼠右鍵按一下圖表圖形，並按一下**新增 Explosed**。|False|
|描述|描述用來產生的設計工具的文件。|\<無 >|
|顯示名稱|會產生這個圖表設計工具中顯示的名稱。|\<無 >|
|說明關鍵字|用於檢索這個圖表 F1 說明關鍵字。|\<無 >|

## <a name="see-also"></a>另請參閱

- [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)