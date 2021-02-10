---
title: 自訂及擴充網域指定的語言
description: 瞭解 Visual Studio 模型和視覺效果 SDK (VMSDK) 提供數個層級，您可以在其中定義模型工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9cfa8a3cda3f6bb2f564efe745a11863cf4d0e8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945301"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>自訂及擴充特定領域語言

Visual Studio 模型和視覺效果 SDK (VMSDK) 提供數個層級，您可以在其中定義模型工具：

1. 使用 DSL 定義圖表)  (DSL 定義特定領域語言。 您可以使用圖表標記法、可讀取的 XML 表單，以及產生程式碼和其他成品所需的基本工具，快速建立 DSL。 如需詳細資訊，請參閱 [如何定義 Domain-Specific 語言](../modeling/how-to-define-a-domain-specific-language.md)。

2. 使用 DSL 定義的更先進功能來微調 DSL。 例如，您可以在使用者建立專案時顯示其他連結。 這些技術大多是在 DSL 定義中達成的，有些則需要幾行程式碼。

3. 使用程式碼擴充您的模型工具。 VMSDK 是為了能讓您輕鬆整合擴充功能與從 DSL 定義產生的程式碼而專門設計的。 如需詳細資訊，請參閱 [撰寫程式碼以自訂 Domain-Specific 語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)。

> [!NOTE]
> 當您更新 DSL 定義檔時，別忘了在重建解決方案之前，先在 **方案總管** 的工具列中按一下 [**轉換所有範本**]。

## <a name="article-reference"></a>文章參考

|若要達成此效果|請參閱本主題|
|-|-|
|允許使用者設定圖形的色彩和樣式屬性。|以滑鼠右鍵按一下 [圖形] 或 [連接器] 類別，指向 [ **加入**]，然後按一下某個專案。|
|模型專案的不同類別在圖表上看起來類似，例如，共用屬性，例如初始高度和寬度、色彩、工具提示。|使用圖形或連接器類別之間的繼承。 衍生的圖形和衍生的網域類別之間的對應會繼承父系的對應詳細資料。<br /><br /> 或者，將不同的網域類別對應到相同的 shape 類別。|
|不同圖形內容會顯示模型專案的類別。|將一個以上的圖形類別對應到相同的網域類別。 當您建立方案時，請遵循錯誤報表，並提供要求的程式碼以決定要使用的圖形。|
|圖形色彩或其他功能（例如字型）表示目前的狀態。|請參閱 [更新圖形和連接器以反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 建立可更新公開屬性的規則。 請參閱 [規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。<br /><br /> 或者，使用 OnAssociatedPropertyChanged ( # A1 來更新非公開的功能，例如連結箭號或字型。|
|圖形上的圖示會變更以表示狀態。|在 [DSL 詳細資料] 視窗中，設定裝飾專案對應的可見度。 找出多個在相同位置裝飾專案的影像。 請參閱  [更新圖形和連接器以反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 或覆寫 `ImageField.GetDisplayImage()` 。 請參閱中的範例 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> 。|
|在任何圖形上設定背景影像|覆寫 InitializeInstanceResources ( # A1 以新增錨定的 ImageField。|
|將圖形嵌套至任何深度|設定遞迴內嵌樹狀結構。 定義 BoundsRules 以包含圖形。|
|在元素界限上的固定點附加連接器。|定義內嵌的終端元素，以圖表上的小埠表示。 使用 BoundsRules 來就地修正埠。 請參閱位於 [視覺效果和模型 SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)的電路圖範例。|
|文字欄位會顯示衍生自其他值的值。|將文字裝飾專案對應至計算或自訂的儲存體定義域屬性。 如需詳細資訊，請參閱 [計算和自訂儲存體屬性](../modeling/calculated-and-custom-storage-properties.md)。|
|傳播模型專案或圖形之間的變更|請參閱 [Domain-Specific 語言的驗證](../modeling/validation-in-a-domain-specific-language.md)。|
|將變更傳播到存放區以外的資源，例如其他 Visual Studio 延伸模組。|請參閱 [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。|
|[屬性] 視窗會顯示相關專案的屬性。|設定屬性轉送。 請參閱 [自訂屬性視窗](../modeling/customizing-the-properties-window.md)。|
|屬性類別目錄|[屬性] 視窗會分成稱為類別目錄的區段。 設定網域屬性的 **類別** 。 相同分類名稱的屬性會出現在相同的區段中。 您也可以設定關聯性角色的 **類別** 。|
|控制使用者對網域屬性的存取|Set **是可流覽** 的 false，以防止在執行時間于屬性視窗中顯示網域屬性。 您仍然可以將它對應到文字裝飾專案。<br /><br /> **是 UI 讀取，** 可防止使用者變更網域屬性。<br /><br /> 不會影響對網域屬性的程式存取。|
|在 DSL 的模型瀏覽器中變更節點的名稱、圖示和可見度。|請參閱 [自訂模型瀏覽器](../modeling/customizing-the-model-explorer.md)。|
|啟用複製、剪下和貼上|在 [DSL Explorer] 中，設定 **編輯器** 節點的 [**啟用複製貼** 上] 屬性。|
|每次複製專案時，複製參考連結和其目標。 例如，複製附加至專案的批註。|將來源角色的 [ **傳播複本** ] 屬性設定為 [DSL 定義圖] 中網域關聯性的某一端 (行表示) 。<br /><br /> 撰寫程式碼來覆寫 ProcessOnCopy，以達成更複雜的效果。<br /><br /> 請參閱 [自訂複製行為](../modeling/customizing-copy-behavior.md)。|
|刪除專案時，刪除、重做或重新連結相關的元素。|設定關聯性角色的 [ **傳播刪除** 值]。 如需更複雜的效果，請在 DomainModel.cs 中定義的類別中覆寫 `ShouldVisitRelationship` 和 `ShouldVisitRolePlayer` 方法 `MyDslDeleteClosure` 。 |
|保留複製和拖放的圖形版面配置和外觀。|將圖形和接點加入至複製的 `ElementGroupPrototype` 。 最方便覆寫的方法為 `ElementOperations.CreateElementGroupPrototype()`<br /><br /> 請參閱 [自訂複製行為](../modeling/customizing-copy-behavior.md)。|
|在選擇的位置貼上圖形，例如目前的游標位置。|覆寫 `ClipboardCommandSet.ProcessOnCopy()` 以使用的位置特定版本， `ElementOperations.Merge().` 請參閱 [自訂複製行為](../modeling/customizing-copy-behavior.md)。|
|在貼上時建立其他連結|覆寫 ClipboardCommandSet. ProcessOnPasteCommand ( # A1|
|啟用此圖表的拖放、其他 Dsl 和 Windows 元素|請參閱 [如何：新增拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|允許將圖形或工具拖曳至子圖形（例如埠），就像是將它拖曳到父系一樣。|在目標物件類別上定義 Element Merge 指示詞，以將卸載的物件轉送至父代。 請參閱 [自訂元素的建立和移動](../modeling/customizing-element-creation-and-movement.md)。|
|允許將圖形或工具拖曳至圖形上，並建立其他連結或物件。 例如，允許將批註放到要連結的專案上。|在目標網域類別上定義元素 Merge 指示詞，並定義要產生的連結。 在複雜的情況下，您可以加入自訂程式碼。 請參閱 [自訂元素的建立和移動](../modeling/customizing-element-creation-and-movement.md)。|
|使用一項工具建立專案群組。 例如，具有一組固定埠的元件。|覆寫 ToolboxHelper.cs 中的 [工具箱] 初始化方法。 建立專案群組原型 (EGP) 包含元素及其關聯性連結。 請參閱 [自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。<br /><br /> 請在 EGP 中包含主體和埠圖形，或在 EGP 具現化時，定義 BoundsRules 來放置埠圖形。|
|使用一個連接工具來具現化數種類型的關聯性。|將連結連接指示詞加入至工具所叫用的連接產生器 (LCD) 。 Lcd 會從兩個專案的類型判斷關聯性的類型。 若要使這取決於專案的狀態，您可以加入自訂程式碼。 請參閱 [自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。|
|[工具]-使用者可以按兩下任何工具，連續建立許多圖形或連接器。|在 [DSL Explorer] 中選取 `Editor` 節點。 在屬性視窗中，set 會 **使用 [粘滯工具箱] 專案**。|
|定義功能表命令|請參閱 [如何：修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|使用驗證規則來限制模型|請參閱 [Domain-Specific 語言的驗證](../modeling/validation-in-a-domain-specific-language.md)|
|從 DSL 產生程式碼、設定檔或檔。|[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)|
|自訂將模型儲存至檔案的方式。|請參閱 [自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|
|將模型儲存至資料庫或其他媒體。|覆寫 *YourLanguage* DocData<br /><br /> 請參閱 [自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|
|整合數個 Dsl，使其可做為一個應用程式的一部分。|請參閱 [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。|
|允許協力廠商擴充您的 DSL，並控制擴充功能。|[使用 MEF 擴充您的 DSL](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [使用 DSL 程式庫共用 DSL 之間的類別](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [定義鎖定原則來建立唯讀區段](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>另請參閱

- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
- [撰寫程式碼以自訂 Domain-Specific 語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
