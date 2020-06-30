---
title: 控制圖示或 Decorator 的可見度
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d2082f7e26d3e335ed88bbced0f59d6d6c4780c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546637"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>控制圖示或 Decorator 的可見度
裝飾*專案是以*特定領域語言（DSL）形式出現在圖形上的圖示或文字行。 您可以根據模型中屬性的狀態，讓裝飾專案出現並消失。 例如，在代表個人的圖形上，您可能會有不同的圖示，視個人的性別、子女數目等等而有所不同。

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>控制圖示或裝飾專案的可見度
 下列程式假設您已經將圖形及其對應定義為網域類別。 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>控制圖示或文字裝飾專案的可見度

1. 在 DSL 定義圖中，將您想要顯示的圖示或文字裝飾專案加入至圖形類別。

   1. 以滑鼠右鍵按一下圖形類別，指向 [**加入**]，然後按一下所需的裝飾專案類型。

   2. 設定裝飾專案的**Position**屬性。 一個以上的裝飾專案可以有相同的位置。 例如，您可以讓男性和女性的圖示共用相同的位置。

   3. 設定圖示裝飾專案的**預設 icon**屬性。

2. 選取 [圖表專案對應]，這是在 DSL 定義圖上，圖形類別和網域類別之間的灰色線條。

3. 在 [DSL 詳細資料] 視窗的 [裝飾專案**對應**] 索引標籤中，選取裝飾專案。 例如，MaleDecorator。

4. 勾選 [**可見度篩選準則**] 方塊。

5. 如果應該控制可見度的網域屬性位於直屬網域類別上，請保留 [**篩選的路徑] 屬性**空白。

    否則，請按一下下拉式功能表，然後流覽至屬性所在的關聯性或類別。

   - 若要避免錯誤報表，您不應該流覽流覽工具中以 "*" 標示的關聯性。

6. 將**Filter 屬性**設定為網域屬性。 例如，性別。

7. 在 [**可見度專案**] 清單中，加入此網域屬性的值，而裝飾項應該是可見的。 例如，男性。

8. 針對每個圖示重複步驟。

9. **轉換所有範本**、建立和執行，以及開啟測試圖表。

10. 當您變更控制屬性值時，裝飾專案應該會出現並消失。

    通常，您會想要讓可見度受到比簡單的一組值更複雜的公式所控制。 例如，若要讓圖示根據特定類型的連結數而定，或使其相依于某個數位是否在特定範圍內。 在此情況下，請使用下列程式。

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>控制以公式為基礎之裝飾專案的可見度

1. 將匯出的定義域屬性加入至網域類別。 在 [**屬性**] 視窗中，設定下列值：

     **IsBrowsable =** `False`**-這會隱藏使用者的屬性**    

     **種類 =** `Calculated`**-這表示您將提供可計算其值的程式碼**    

     範例**DecoratorControl**的**名稱**

     **型** = `Boolean`

     如需詳細資訊，請參閱[計算和自訂儲存體屬性](../modeling/calculated-and-custom-storage-properties.md)。

2. 讓新的屬性控制裝飾專案的可見度。

    1. 選取 [圖表專案對應]，這是從網域類別到圖形的灰色線條。 在 [ **DSL 詳細資料**] 視窗中，開啟 [ **DecoratorMap** ] 索引標籤。

    2. 勾選 [**可見度篩選準則**] 方塊。

    3. 在 [**篩選] 屬性**中，選取控制項屬性**DecoratorControl**。

    4. 在 [**可見度專案**] 下，輸入 `True` 。

3. 按一下 [**方案總管**] 工具列中的 [**轉換所有範本**]。

4. 按一下 [**建立**] 功能表上的 [**建立方案**]。

5. 按兩下出現的錯誤報表：「*YourClass*不包含 GetDecoratorControlValue 的定義 ...」。

     文字編輯器會在 Dsl\GeneratedCode\DomainClasses.cs. 上開啟 上方反白顯示的錯誤是要求您新增方法的批註。

6. 請注意缺少的命名空間、類別和方法。  例如，FamilyTree. Person. GetDecoratorControlValue （）。

7. 在不同的程式碼檔案中，撰寫包含遺漏方法的部分類別定義。 例如：

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     如需使用程式碼自訂模型的詳細資訊，請參閱[在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

8. 重建並執行解決方案。

## <a name="see-also"></a>另請參閱

- [定義圖案和連接器](../modeling/defining-shapes-and-connectors.md)
- [設定圖表上的背景影像](../modeling/setting-a-background-image-on-a-diagram.md)
- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)