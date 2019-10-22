---
title: 自訂及擴充網域指定的語言
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e6346f960efe1cd3af6ad9cbd070227d9171f01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654025"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>自訂及擴充特定領域語言

Visual Studio 模型化和視覺化 SDK （VMSDK）提供數個層級，您可以在其中定義模型工具：

1. 使用 DSL 定義圖表來定義特定領域語言（DSL）。 您可以使用圖表標記法、可讀取的 XML 表單，以及產生程式碼和其他成品所需的基本工具，快速建立 DSL。 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。

2. 使用 DSL 定義的更先進功能來微調 DSL。 例如，您可以在使用者建立專案時，顯示其他連結。 這些技術大多是在 DSL 定義中達成，而有些則需要幾行程式碼。

3. 使用程式碼擴充您的模型工具。 VMSDK 是為了能讓您輕鬆整合擴充功能與從 DSL 定義產生的程式碼而專門設計的。 如需詳細資訊，請參閱[撰寫程式碼以自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)。

> [!NOTE]
> 當您更新 DSL 定義檔時，別忘了在重建解決方案之前，按一下**方案總管**的工具列中的 [**轉換所有範本**]。

## <a name="article-reference"></a>文章參考

|若要達到此效果|請參閱本主題|
|-|-|
|允許使用者設定圖形的色彩和樣式屬性。|以滑鼠右鍵按一下圖形或連接器類別，指向 [**加入已公開**]，然後按一下專案。|
|不同類別的模型專案在圖表上看起來類似，共用屬性，例如初始高度和寬度、色彩、工具提示。|使用圖形或連接器類別之間的繼承。 衍生的圖形與衍生的網域類別之間的對應會繼承父代的對應詳細資料。<br /><br /> 或者，將不同的網域類別對應至相同的 shape 類別。|
|模型專案的類別是由不同的圖形內容所顯示。|將一個以上的圖形類別對應至相同的網域類別。 當您建立方案時，請遵循錯誤報表，並提供要求的程式碼來決定要使用哪一個圖形。|
|圖形色彩或其他功能（例如字型）表示目前狀態。|請參閱[更新圖形和連接器以反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 建立可更新已公開屬性的規則。 請參閱[規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。<br /><br /> 或者，使用 OnAssociatedPropertyChanged （）來更新未公開的功能，例如連結箭號或字型。|
|圖形上的圖示會變更以指出狀態。|在 [DSL 詳細資料] 視窗中設定裝飾專案對應的可見度。 在相同位置上找出數個影像裝飾專案。 請參閱[更新圖形和連接器以反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 或者，覆寫 `ImageField.GetDisplayImage()`。 請參閱 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> 中的範例。|
|在任何圖形上設定背景影像|覆寫 InitializeInstanceResources （）以加入錨定的 ImageField。|
|將圖形嵌套到任何深度|設定遞迴內嵌樹狀結構。 定義 BoundsRules 以包含圖形。|
|在專案界限上的固定點附加連接器。|定義內嵌的終端機元素，以圖表上的小型埠表示。 使用 BoundsRules 來就地修正埠。 請參閱[視覺效果和模型化 SDK](http://go.microsoft.com/fwlink/?LinkID=186128)中的線路圖表範例。|
|文字欄位：顯示衍生自其他值的值。|將文字裝飾專案對應至計算或自訂的儲存網域屬性。 如需詳細資訊，請參閱[計算和自訂儲存體屬性](../modeling/calculated-and-custom-storage-properties.md)。|
|在模型專案之間或在圖形之間傳播變更|請參閱[以特定領域語言進行驗證](../modeling/validation-in-a-domain-specific-language.md)。|
|將變更傳播至存放區以外的資源，例如其他 Visual Studio 延伸模組。|請參閱[事件處理常式會將變更傳播到模型外部](../modeling/event-handlers-propagate-changes-outside-the-model.md)。|
|屬性視窗：顯示相關元素的屬性。|設定屬性轉送。 請參閱[自訂屬性視窗](../modeling/customizing-the-properties-window.md)。|
|屬性類別|[屬性] 視窗會分成稱為「分類」的區段。 設定網域屬性的**類別**。 具有相同分類名稱的屬性會出現在相同的區段中。 您也可以設定關聯性角色的**分類**。|
|控制使用者對網域屬性的存取權|Set **Is 可流覽**false，防止網域屬性在執行時間出現在屬性視窗中。 您仍然可以將它對應到文字裝飾專案。<br /><br /> [ **IS UI Read Only] 會**防止使用者變更網域屬性。<br /><br /> 對網域屬性的程式存取不受影響。|
|變更 DSL 的 [模型瀏覽器] 中節點的名稱、圖示和可見度。|請參閱[自訂模型瀏覽器](../modeling/customizing-the-model-explorer.md)。|
|啟用複製、剪下和貼上|在 [DSL Explorer] 中設定 [**編輯器**] 節點的 [**啟用複製貼**上] 屬性。|
|每次複製專案時，複製參考連結和其目標。 例如，複製附加至專案的批註。|設定來源角色的 [**傳播複本**] 屬性（以行在 DSL 定義圖中的網域關聯性的一端表示）。<br /><br /> 撰寫程式碼以覆寫 ProcessOnCopy，以達到更複雜的效果。<br /><br /> 請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)。|
|刪除、重做或重新連結元素時的相關元素。|設定關聯性角色的**傳播刪除**值。 如需更複雜的效果，請覆寫在**DomainModel.cs**中定義的 `MyDslDeleteClosure` 類別中 `ShouldVisitRelationship` 和 `ShouldVisitRolePlayer` 方法。|
|在複製和拖放上保留圖形版面配置和外觀。|將圖形和連接器加入至複製的 `ElementGroupPrototype`。 最方便覆寫的方法是 `ElementOperations.CreateElementGroupPrototype()`<br /><br /> 請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)。|
|在選擇的位置貼上圖形，例如目前的游標位置。|覆寫 `ClipboardCommandSet.ProcessOnCopy()` 若要使用位置特定版本的 `ElementOperations.Merge().`，請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)。|
|在貼上時建立其他連結|覆寫 ClipboardCommandSet ProcessOnPasteCommand （）|
|從這個圖表、其他 Dsl 和 Windows 元素啟用拖放|請參閱[如何：加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|允許將圖形或工具拖曳至子圖形（例如埠），就像是拖曳到父系上一樣。|在目標物件類別上定義元素合併指示詞，以將捨棄的物件轉送至父系。 請參閱[自訂元素的建立和移動](../modeling/customizing-element-creation-and-movement.md)。|
|允許將圖形或工具拖曳至圖形上，並建立額外的連結或物件。 例如，允許將批註放到要連結的專案上。|在目標網域類別上定義元素合併指示詞，並定義要產生的連結。 在複雜的情況下，您可以新增自訂程式碼。 請參閱[自訂元素的建立和移動](../modeling/customizing-element-creation-and-movement.md)。|
|使用一個工具來建立一組元素。 例如，具有一組固定埠的元件。|覆寫 ToolboxHelper.cs 中的 [工具箱] 初始化方法。 建立專案群組原型（EGP），其中包含元素及其關聯性連結。 請參閱[自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。<br /><br /> 請在 EGP 中包含主體和埠圖形，或定義 BoundsRules 在 EGP 具現化時放置埠圖形。|
|使用一個連接工具來具現化數種類型的關聯性。|將連結連接指示詞（LCD）新增至工具所叫用的連接產生器。 Lcd 會從兩個元素的類型判斷關聯性的類型。 若要讓這項操作取決於元素的狀態，您可以加入自訂程式碼。 請參閱[自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。|
|[粘滯工具]-使用者可以按兩下任何工具，連續建立許多圖形或連接器。|在 [DSL Explorer] 中，選取 [`Editor`] 節點。 在屬性視窗中，set 會**使用 [粘滯工具箱] 專案**。|
|定義功能表命令|請參閱[如何：修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|使用驗證規則來限制模型|請參閱[特定領域語言的驗證](../modeling/validation-in-a-domain-specific-language.md)|
|從 DSL 產生程式碼、設定檔或檔。|[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)|
|自訂如何將模型儲存至檔案。|請參閱[自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|
|將模型儲存至資料庫或其他媒體。|覆寫*YourLanguage*DocData<br /><br /> 請參閱[自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|
|整合數個 Dsl，使其可做為一個應用程式的一部分。|請參閱[使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。|
|允許協力廠商擴充您的 DSL，並控制延伸模組。|[使用 MEF 擴充您的 DSL](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [使用 DSL 程式庫共用 DSL 之間的類別](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [定義鎖定原則來建立唯讀區段](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>請參閱

- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
