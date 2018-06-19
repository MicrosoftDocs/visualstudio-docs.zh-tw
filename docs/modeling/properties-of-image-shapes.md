---
title: 影像圖案的屬性
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 780c9c98bc6be110a0c8bc987a70aeea3344d0e8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31952624"
---
# <a name="properties-of-image-shapes"></a>影像圖案的屬性
若要指定網域類別出現在產生的設計工具的方式，您可以使用映像的圖形。 設定以定義影像圖形`Image`預先定義的映像檔案類別的屬性。 支援下列格式：

-   .gif

-   .jpg

-   .jpeg

-   .bmp

-   .wmf

-   .emf

-   .png

 根據預設，設計工具資源檔，例如影像檔，位於**資源**資料夾中的**Dsl**專案。

 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 映像圖形有下表中列出的屬性。

|屬性|描述|預設|
|--------------|-----------------|-------------|
|填滿色彩|此圖形的填滿色彩。|白色|
|填滿漸層停駐模式|此圖形的填滿漸層的模式。|水平|
|具有預設的連接點|如果`True`、 圖形將會使用 top，bottom，left 和正確的連接點產生的設計工具中。|False|
|外框色彩|此圖形外框色彩。|黑色|
|外框虛線樣式|此圖形 （實線、 虛線、 點、 線、 虛線點點或自訂） 的外框虛線樣式。|實線|
|外框粗細|此圖形外框粗細。|0.03125|
|文字色彩|使用此圖形相關聯的文字裝飾色彩。|黑色|
|存取修飾詞|幾何圖案 （公用或內部） 的存取修飾詞。|Public|
|自訂屬性|用來將屬性加入至來源的程式碼類別從這個圖形所產生。|\<無 >|
|會產生雙衍生|如果`True`，就會產生 （以支援自訂透過覆寫） 的部分類別和基底類別。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|具有自訂建構函式|如果`True`，會在原始程式碼中提供的自訂建構函式。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|繼承修飾詞|描述從映像 」 圖形產生來源的程式碼類別的繼承種類 (`none`，`abstract`或`sealed`)。|無|
|基底映像圖形|此圖形的基底類別。|(無)|
|名稱|此圖形的名稱。|目前的名稱|
|命名空間|此圖形附屬於命名空間。|目前的命名空間|
|工具提示的型別|（固定，變數，或 none） 定義工具提示所在位置。 然後固定的值如果`Fixed Tooltip Text`屬性做為工具提示; 如果變數，然後在工具提示會定義自訂程式碼中。|無|
|注意|此圖形相關聯的非正式附註。|\<無 >|
|初始高度|此圖形，以英吋的初始高度。|1|
|初始寬度|此圖形，以英吋的初始寬度。|1.5|
|當做屬性公開的填滿色彩<br /><br /> 公開填滿漸層停駐模式<br /><br /> 公開為屬性的 外框色彩<br /><br /> 公開為屬性的 外框虛線樣式<br /><br /> 公開為屬性的外框粗細<br /><br /> 公開文字色彩|如果`True`，使用者可以設定圖形的所述的屬性。 若要設定這種情況，以滑鼠右鍵按一下圖形定義，然後按一下**新增公開**。|False|
|描述|用來產生的設計工具的文件。|\<無 >|
|顯示名稱|會產生此圖形設計工具中顯示的名稱。|\<無 >|
|固定的工具提示文字|使用固定的工具提示文字。|\<無 >|
|說明關鍵字|用來編製索引的這個項目 F1 說明關鍵字。|\<無 >|
|Image|使用此圖形影像檔案的路徑。|\<無 >|

## <a name="see-also"></a>另請參閱

- [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)