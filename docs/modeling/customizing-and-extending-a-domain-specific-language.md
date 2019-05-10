---
title: 自訂及擴充網域指定的語言
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebbb18e37356c1ef6ccc47f18afe4736a418c0c3
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476584"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>自訂及擴充特定領域語言

Visual Studio 模型和視覺效果 SDK (VMSDK) 提供在中，您可以定義模型化工具的數個層級：

1. 定義特定領域語言 (DSL) 使用 DSL 定義圖。 您可以使用圖表標記法、 可讀取的 XML 格式和產生程式碼和其他成品所需的基本工具，快速建立 DSL。 如需詳細資訊，請參閱 <<c0> [ 如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。

2. 使用 DSL 定義的更進階的功能來微調 DSL。 比方說，您可以建立其他連結，使用者建立的項目時，會出現。 這些技巧大部分裡 DSL 定義中，而某些需要幾行程式碼。

3. 使用程式碼，以擴充您的模型化工具。 VMSDK 是為了能讓您輕鬆整合擴充功能與從 DSL 定義產生的程式碼而專門設計的。 如需詳細資訊，請參閱 <<c0> [ 來自訂特定領域語言撰寫的程式碼](../modeling/writing-code-to-customise-a-domain-specific-language.md)。

> [!NOTE]
> 更新在 DSL 定義檔之後，別忘了按一下**轉換所有範本**中的工具列**方案總管 中**後再重建您的解決方案。

## <a name="article-reference"></a>文件參考

|若要達成此效果|請參閱本主題|
|-|-|
|允許使用者設定圖形的色彩和樣式屬性。|以滑鼠右鍵按一下圖形或連接器的類別，指向**加入已公開**，並按一下的項目。|
|不同類別的模型項目看起來類似上圖中，共用的屬性，例如初始的高度和寬度、 色彩、 工具提示的。|使用圖形或連接器類別之間的繼承。 在衍生的圖形與衍生的網域類別之間的對應會繼承父代的對應詳細資料。<br /><br /> 或者，您也可以將不同的網域類別對應至相同的圖形類別。|
|不同的圖形內容會顯示模型項目的類別。|將一個以上的 shape 類別對應至相同的網域類別。 當您建置方案時，請遵循錯誤報表，並提供要求的程式碼，來決定要使用何種圖形。|
|圖形色彩或字型等其他功能表示目前的狀態。|請參閱[更新圖案和接點來反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 建立規則，以更新公開的屬性。 請參閱[規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。<br /><br /> 或者，您也可以使用 OnAssociatedPropertyChanged() 更新非公開的功能，例如連結箭號或字型。|
|表示狀態的圖形變更圖示。|在 DSL 詳細資料視窗中，設定裝飾項目對應的可見性。 找出相同的位置上的數個映像裝飾項目。 請參閱[更新圖案和接點來反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 或者，您也可以覆寫`ImageField.GetDisplayImage()`。 中的範例，請參閱<xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>。|
|在圖形中設定背景影像|若要新增的錨定的 ImageField InitializeInstanceResources() 會覆寫。|
|任何深度的巢狀處理圖案|設定內嵌樹狀目錄中遞迴。 定義包含圖形的 BoundsRules。|
|附加在固定時間點上的項目界限的連接器。|定義內嵌的終端機元素，表示圖表上的小連接埠。 若要修正的連接埠就地使用 BoundsRules。 電路圖表範例，請參閱 < [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)。|
|文字欄位會顯示衍生自其他值的值。|將文字裝飾項目對應至 Calculated 或自訂儲存網域屬性。 如需詳細資訊，請參閱 <<c0> [ 計算和儲存體的自訂屬性](../modeling/calculated-and-custom-storage-properties.md)。|
|將模型項目，或圖形之間的變更傳播|請參閱[定義域專屬語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)。|
|將變更傳播到外部存放區的其他 Visual Studio 擴充功能等資源。|請參閱[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。|
|屬性視窗會顯示相關項目的屬性。|設定屬性轉送。 請參閱[自訂屬性視窗](../modeling/customizing-the-properties-window.md)。|
|屬性類別|[屬性] 視窗分為稱 [分類] 的區段。 設定**分類**的網域屬性。 具有相同的類別目錄名稱的屬性會出現在相同的區段。 您也可以設定**分類**的關聯性角色。|
|控制使用者網域屬性的存取|設定**Is Browsable**為 false，則出現在 [屬性] 視窗中，在執行階段時，防止網域屬性。 您仍然可以將它對應至文字裝飾項目。<br /><br /> **是 UI Read Only**防止使用者變更網域屬性。<br /><br /> 不會影響程式存取的網域屬性。|
|變更名稱、 圖示和可見性，您的 DSL 模型總管 中的節點。|請參閱[自訂模型總管](../modeling/customizing-the-model-explorer.md)。|
|啟用複製、 剪下和貼上|設定**啟用複製貼上**屬性**編輯器**DSL 總管 中的節點。|
|請將複製參考連結和其目標，每當複製的項目。 例如，將複製的項目附加註解。|設定**Propagates Copy** （由位於在 DSL 定義圖表中的網域關聯性的一端） 的來源角色的內容。<br /><br /> 撰寫程式碼來覆寫 ProcessOnCopy 來達成更複雜的效果。<br /><br /> 請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)。|
|刪除、 重設父代，或刪除項目時，請重新連結相關的項目。|設定**傳播刪除**關聯性角色的值。 針對更複雜的影響，會覆寫`ShouldVisitRelationship`並`ShouldVisitRolePlayer`中的方法`MyDslDeleteClosure`中所定義的類別**DomainModel.cs**。|
|保留圖形版面配置和外觀上複製和拖放。|將圖形和連接器新增至所複製`ElementGroupPrototype`。 若要覆寫最方便的方法是 `ElementOperations.CreateElementGroupPrototype()`<br /><br /> 請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)。|
|在選擇的位置貼上圖形，例如目前的游標位置。|覆寫`ClipboardCommandSet.ProcessOnCopy()`若要使用的特定位置的新版`ElementOperations.Merge().`請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)。|
|貼上建立其他連結|Override ClipboardCommandSet.ProcessOnPasteCommand()|
|啟用從拖放此圖中，其他的 Dsl 和 Windows 項目|請參閱[如何：新增拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|讓圖形或工具拖曳至 「 子 」 圖形，例如連接埠，如同它已拖曳至父代。|定義目標物件類別，來卸除的物件轉送給父項目合併指示詞。 請參閱[自訂項目建立和移動](../modeling/customizing-element-creation-and-movement.md)。|
|讓圖形或將它們拖曳至圖形，並讓其他連結的工具或建立的物件。 例如，若要允許的註解可以放到它為連結的項目。|在目標網域類別，定義項目合併指示詞，並定義要產生的連結。 在複雜的情況下，您可以加入自訂程式碼。 請參閱[自訂項目建立和移動](../modeling/customizing-element-creation-and-movement.md)。|
|利用單一工具中建立一組項目。 例如，具有一組固定的連接埠的元件。|覆寫 ToolboxHelper.cs 中的 [工具箱] 初始化方法。 建立項目群組原型 (EGP) 包含的項目和其關聯性連結。 請參閱[自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。<br /><br /> 包含主體和連接埠圖形中的 EGP，或是定義 BoundsRules EGP 具現化時通訊埠圖案的位置。|
|您可以使用一個連接工具來產生數種類型的關聯性。|加入連接產生器工具所叫用連結連線指示詞 (LCD)。 Lcd 判斷兩個項目類型的關聯性的類型。 若要讓這項目的狀態而定，您可以加入自訂程式碼。 請參閱[自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。|
|自黏便箋的工具-使用者可以按兩下任何工具來建立連續的許多圖形或連接器。|在 DSL 總管 中，選取 `Editor`節點。 在 [屬性] 視窗中，設定**使用黏性工具箱項目**。|
|定義功能表命令|請參閱[如何：修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|限制使用驗證規則的模型|請參閱[定義域專屬語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)|
|從 DSL 中產生程式碼、 組態檔或文件。|[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)|
|自訂如何儲存模型檔案。|請參閱[自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|
|將模型儲存至資料庫或其他媒體。|覆寫*YourLanguage*DocData<br /><br /> 請參閱[自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|
|將數個 Dsl 的整合，讓它們能夠做為一個應用程式的一部分。|請參閱[使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。|
|允許由協力廠商擴充 DSL 和控制擴充功能。|[使用 MEF 擴充您的 DSL](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [使用 DSL 程式庫共用 DSL 之間的類別](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [定義鎖定原則來建立唯讀區段](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>另請參閱

- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
