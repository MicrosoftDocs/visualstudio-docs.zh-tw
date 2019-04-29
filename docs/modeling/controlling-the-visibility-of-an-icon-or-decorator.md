---
title: 控制圖示或 Decorator 的可見度
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7cfe6ce02b03ed69435f8056ccd340b92f9eb5a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62421495"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>控制圖示或 Decorator 的可見度
A*裝飾項目*是圖示或特定領域語言 (DSL) 中的圖形上顯示的文字行。 您可以進行裝飾項目會顯示，並根據模型中屬性的狀態會消失。 例如，代表個人的圖形，您可能有不同的圖示會出現取決於該人員的性別，子系數目等等。

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>控制圖示或 decorator 的可視性
 下列程序會假設，您已定義的圖形和其對應至網域類別。 如需詳細資訊，請參閱 <<c0> [ 如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>若要控制的可見性 圖示或文字裝飾項目

1. 在 DSL 定義圖表中，加入圖形類別，圖示或您想要顯示的文字裝飾項目。

   1. 以滑鼠右鍵按一下圖形類別，指向**新增**，然後按一下 所需的裝飾項目類型。

   2. 設定裝飾項目**位置**屬性。 多個裝飾項目可以有相同的位置。 例如，您可能有圖示男性和女性共用相同的位置。

   3. 設定**預設圖示**圖示裝飾項目屬性。

2. 選取圖表項目對應，也就是 shape 類別與 DSL 定義圖上的網域類別之間的灰線。

3. 在 DSL 詳細資料 視窗中，在**裝飾項目對應**索引標籤上，選取 裝飾項目。 比方說，MaleDecorator。

4. 請檢查**Visibility Filter**  方塊中。

5. 如果應該控制可見性的網域屬性是立即網域類別上，保留**篩選條件屬性的路徑**空白。

    否則，請按一下下拉式選單，並瀏覽至的關聯性或類別之屬性所在的位置。

   - 若要避免錯誤報告，您應該不瀏覽關聯性標示為 「 * 」 中瀏覽工具。

6. 設定**篩選條件屬性**網域屬性。 例如，性別。

7. 在 **可見度輸入**清單中，新增的裝飾項目應該為可見的這個網域屬性的值。 例如，男性。

8. 重複步驟，針對每個圖示。

9. **轉換所有範本**、 建置和執行和開啟測試圖表。

10. 當您變更控制的屬性值時，裝飾項目應該會出現並消失。

    通常，您會想控制更複雜的公式比簡單的一組值的可見性。 比方說，有特定類型的連結數目而定的圖示，或將它取決於是否數字就會處於特定範圍。 在此情況下，使用下列程序。

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>若要控制的裝飾項目，以公式為基礎的可見性

1. 將導出的網域屬性加入至網域類別。 在 [**屬性**] 視窗中，設定下列值：

     **IsBrowsable =**`False`**-這可能會隱藏來自使用者的屬性**

     **類型 =**`Calculated`**-這表示您將提供程式碼會計算其值**

     **名稱**例如**DecoratorControl**

     **Type** = `Boolean`

     如需詳細資訊，請參閱 <<c0> [ 計算和儲存體的自訂屬性](../modeling/calculated-and-custom-storage-properties.md)。

2. 讓新的屬性，控制 decorator 的可視性。

    1. 選取圖表項目對應，也就是從網域類別到圖形，灰線。 在 [ **DSL 詳細資料**視窗中，開啟**DecoratorMap** ] 索引標籤。

    2. 請檢查**Visibility Filter**  方塊中。

    3. 在 **篩選條件屬性**，選取的控制項屬性**DecoratorControl**。

    4. 底下**可見性的項目**，輸入`True`。

3. 按一下 [**轉換所有範本**中**方案總管] 中**工具列。

4. 按一下 **建置方案**上**建置**功能表。

5. 按兩下出現的錯誤報表：「*YourClass*未包含定義 GetDecoratorControlValue...」。

     文字編輯器會開啟 Dsl\GeneratedCode\DomainClasses.cs。 上述反白顯示的錯誤會要求您將方法加入的註解。

6. 請注意所缺少的命名空間、 類別和方法。  比方說，Company.FamilyTree.Person.GetDecoratorControlValue()。

7. 在不同的程式碼檔案中，撰寫部分類別定義，其中包含遺漏的方法。 例如: 

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     如需有關自訂程式碼之模型的詳細資訊，請參閱[巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

8. 重新建置並執行方案。

## <a name="see-also"></a>另請參閱

- [定義圖案和接點](../modeling/defining-shapes-and-connectors.md)
- [設定圖表上的背景影像](../modeling/setting-a-background-image-on-a-diagram.md)
- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)