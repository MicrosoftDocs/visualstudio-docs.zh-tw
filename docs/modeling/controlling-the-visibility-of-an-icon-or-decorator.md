---
title: "控制圖示或裝飾項目的可見性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 835d9d356a06c831bb3decf6d0a5a6a4b5620302
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>控制圖示或 Decorator 的可見度
A *decorator*是圖示或出現在圖形中的網域特定定義域語言 (DSL) 的文字行。 您可以設裝飾項目會出現，並根據模型中屬性的狀態會消失。 例如，代表個人的圖形，您可以有不同的圖示會出現取決於該人員的性別的子系數目等等。  
  
## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>控制圖示或裝飾項目的可見性  
 下列程序假設您有已定義圖形和其對應的網域類別。 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。  
  
#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>若要控制的圖示或文字裝飾項目的可見性  
  
1.  DSL 定義圖表中，在類別中加入圖形圖示或您想要顯示的文字裝飾項目。  
  
    1.  圖形類別上按一下滑鼠右鍵，指向**新增**，然後按一下所需的裝飾項目的類型。  
  
    2.  設定 decorator**位置**屬性。 一個以上的裝飾項目可以有相同的位置。 例如，您可能會有圖示男性和女性共用相同的位置。  
  
    3.  設定**預設圖示**圖示裝飾項目的屬性。  
  
2.  選取的圖表項目對應，也就是圖形類別和 DSL 定義圖表上的網域類別之間灰線。  
  
3.  在 DSL 詳細資料視窗中，在**裝飾項目的對應**索引標籤上，選取裝飾項目。 例如，MaleDecorator。  
  
4.  請檢查**Visibility Filter**方塊。  
  
5.  如果應該控制可見性的 domain 內容是立即網域類別上，將**篩選屬性路徑**空白。  
  
     否則，按一下下拉式選單，並瀏覽關聯性或屬性所在的類別。  
  
    -   若要避免錯誤報告，您應該不巡覽關聯性標記為"*"瀏覽工具中。  
  
6.  設定**篩選屬性**網域屬性。 例如，性別。  
  
7.  在**可見性的項目**清單中，新增的裝飾項目應該為可見的這個網域屬性的值。 例如，男性。  
  
8.  重複步驟，針對每個圖示。  
  
9. **轉換所有範本**、 建置及執行和開啟測試圖表。  
  
10. 當您變更控制的屬性值時，裝飾項目應該會出現，並會消失。  
  
 通常，您想更複雜的公式比一組簡單的值來控制的可見性。 比方說，有特定的型別，連結數目而定的圖示，或讓它相依於是否數字是在特定範圍內。 在此情況下，使用下列程序。  
  
#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>若要控制可見性的公式為基礎的裝飾項目  
  
1.  將導出的網域屬性加入至網域類別。 在**屬性**視窗中，設定下列值：  
  
     **IsBrowsable =**`False`**-這會隱藏使用者屬性**   
  
     **類型 =**`Calculated`**-這表示您將會提供程式碼會計算其值**   
  
     **名稱**例如**DecoratorControl**  
  
     **Type** = `Boolean`  
  
     如需詳細資訊，請參閱[計算和儲存體的自訂屬性](../modeling/calculated-and-custom-storage-properties.md)。  
  
2.  讓新屬性控制的裝飾項目可見性。  
  
    1.  選取的圖表項目對應，也就是領域類別圖形的灰線。 在**DSL 詳細資料**視窗中，開啟**DecoratorMap**  索引標籤。  
  
    2.  請檢查**Visibility Filter**方塊。  
  
    3.  在**篩選屬性**，選取的控制項屬性**DecoratorControl**。  
  
    4.  在下**可見性的項目**，輸入`True`。  
  
3.  按一下**轉換所有範本**[方案總管] 工具列。  
  
4.  按一下**建置方案**上**建置**功能表。  
  
5.  按兩下出現的錯誤報告:"*YourClass*未包含定義 GetDecoratorControlValue...」。  
  
     文字編輯器開啟 Dsl\GeneratedCode\DomainClasses.cs 上。 反白顯示的錯誤之上會要求您加入的方法中的註解。  
  
6.  請注意命名空間、 類別和方法所遺漏。  例如，Company.FamilyTree.Person.GetDecoratorControlValue()。  
  
7.  在不同的程式碼檔案中，撰寫包含遺漏的方法的部分類別定義。 例如:   
  
    ```  
    namespace Company.FamilyTree  
    { partial class Person  
      { bool GetDecoratorControlValue()  
        {  
          return this.Children.Count > 0;  
    } } }  
    ```  
  
     如需自訂程式碼之模型的詳細資訊，請參閱[巡覽和更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
8.  重新建置並執行方案。  
  
## <a name="see-also"></a>請參閱  
 [定義圖形和連接器](../modeling/defining-shapes-and-connectors.md)   
 [在圖表上設定的背景影像](../modeling/setting-a-background-image-on-a-diagram.md)   
 [巡覽和更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)