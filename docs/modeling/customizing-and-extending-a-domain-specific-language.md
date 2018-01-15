---
title: "自訂和擴充的網域特定定義域語言 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7c0ecd953a0a4cb744f726fc6a62bee564d15579
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>自訂及擴充網域指定的語言
Visual Studio 模型和視覺效果 SDK (VMSDK) 提供數個層級，您可以定義模型工具：  
  
1.  定義使用 DSL 定義圖表的特定領域語言 (DSL)。 您可以快速建立 DSL，其中包含要標記法，可讀取的 XML 格式，產生程式碼與其他成品所需的基本工具。  
  
     如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。  
  
2.  微調 DSL 使用 DSL 定義的更進階的功能。 例如，您可以進行其他使用者建立的項目時顯示的連結。 DSL 定義中，大部分達成這些技術，且部分需要幾行程式碼。  
  
3.  使用程式碼，以擴充模型化工具。 VMSDK 是為了能讓您輕鬆整合擴充功能與從 DSL 定義產生的程式碼而專門設計的。  如需詳細資訊，請參閱[以自訂特定領域語言撰寫的程式碼](../modeling/writing-code-to-customise-a-domain-specific-language.md)。  
  
> [!NOTE]
>  當您有更新的 DSL 定義檔時，請務必按一下**轉換所有範本**後再重建您的方案的 [方案總管] 工具列中。  
  
##  <a name="customShapes"></a>本章節內容  
  
|若要達成這個效果|請參閱本主題|  
|----------------------------|-------------------------|  
|可讓使用者設定圖形的色彩和樣式屬性。|以滑鼠右鍵按一下圖形或連接器的類別，並指向**新增公開**，按的項目。<br /><br /> 請參閱[自訂圖表上的簡報](../modeling/customizing-presentation-on-the-diagram.md)。|  
|請在圖表上的共用內容，例如初始高度和寬度、 色彩、 工具提示不同類別的模型項目類似。|使用圖形或連接器類別之間的繼承。 在衍生的圖形與網域在衍生的類別之間的對應繼承父系的對應詳細資料。<br /><br /> 或者，您也可以將不同的網域類別對應至相同的 「 圖形 」 類別。|  
|模型項目的類別會顯示不同的圖形內容。|將多個圖形類別對應至相同的網域類別。 當您建置方案時，請遵循錯誤報告，並提供要求的程式碼，以決定要使用哪些圖形。|  
|圖形色彩或其他功能，例如字型表示目前的狀態。|請參閱[更新圖形和連接器，以反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 建立規則，以更新公開的屬性。 請參閱[規則將在模型中的變更傳播](../modeling/rules-propagate-changes-within-the-model.md)。<br /><br /> 或者，使用 OnAssociatedPropertyChanged() 更新非公開的功能，例如連結箭號或字型。|  
|指出狀態的變更圖形上的圖示。|DSL 詳細資料視窗中設定的裝飾項目對應的可見性。 找出相同的位置上的數個映像裝飾項目。 請參閱[更新圖形和連接器，以反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)。<br /><br /> 或者，您也可以覆寫`ImageField.GetDisplayImage()`。 請參閱範例<xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>。|  
|設定在圖形的背景影像|若要加入錨定的 ImageField InitializeInstanceResources() 會覆寫。 請參閱[自訂圖表上的簡報](../modeling/customizing-presentation-on-the-diagram.md)。|  
|任意深度的巢狀圖形|設定內嵌樹狀目錄中遞迴。 定義包含圖形 BoundsRules。 請參閱[自訂圖表上的簡報](../modeling/customizing-presentation-on-the-diagram.md)。|  
|附加在固定的點上的項目界限的連接器。|定義內嵌的終端機項目，由圖表上的小型連接埠。 若要修正之連接埠就地使用 BoundsRules。 請參閱的循環圖表範例[Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)。|  
|文字欄位會顯示衍生自其他值的值。|將文字裝飾項目對應至計算或自訂儲存體的網域屬性。 如需詳細資訊，請參閱[計算和儲存體的自訂屬性](../modeling/calculated-and-custom-storage-properties.md)。|  
|將圖形或模型項目之間的變更傳播|請參閱[中的特定領域語言驗證](../modeling/validation-in-a-domain-specific-language.md)。|  
|將變更傳播至資源，例如其他[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]外部存放區的延伸模組。|請參閱[事件處理常式傳播變更模型外部之](../modeling/event-handlers-propagate-changes-outside-the-model.md)。|  
|屬性視窗會顯示相關項目的屬性。|設定屬性轉送。 請參閱[自訂屬性 視窗](../modeling/customizing-the-properties-window.md)。|  
|屬性類別|[屬性] 視窗分割為區段稱為分類。 設定**類別**的網域屬性。 具有相同的類別目錄名稱的屬性會出現在相同的區段。 您也可以設定**類別**的關聯性角色。|  
|網域內容控制項使用者存取|設定**是可瀏覽**為 false，則防止網域屬性在執行階段出現在 [屬性] 視窗中。 您仍然可以對應至文字裝飾項目。<br /><br /> **為 UI 唯讀**防止使用者變更定義域屬性。<br /><br /> 不會影響程式的 domain 內容的存取。|  
|變更名稱、 圖示和可見性的 DSL 模型總管 中的節點。|請參閱[自訂模型總管](../modeling/customizing-the-model-explorer.md)。|  
|啟用複製、 剪下和貼上|設定**啟用複製貼上**屬性**編輯器**DSL 總管中的節點。|  
|只要項目會複製其目標與複製參考的連結。 例如，複製附加至項目註解。|設定**傳播複製**來源角色 （位於網域中的關聯性 DSL 定義圖表的一端之行以表示） 的屬性。<br /><br /> 撰寫程式碼來覆寫 ProcessOnCopy 以達到更複雜的影響。<br /><br /> 請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)。|  
|刪除、 重設父代，或刪除項目時，請重新連結相關的項目。|設定**傳播刪除**關係角色的值。 對於更複雜的影響，覆寫`ShouldVisitRelationship`和`ShouldVisitRolePlayer`方法`MyDslDeleteClosure`中定義的類別**DomainModel.cs**<br /><br /> 請參閱[自訂刪除行為](../modeling/customizing-deletion-behavior.md)|  
|保留圖形版面配置和外觀上複製和拖放。|將圖形和連接器新增至複製`ElementGroupPrototype`。 若要覆寫最方便的方法是`ElementOperations.CreateElementGroupPrototype()`<br /><br /> 請參閱[自訂複製行為](../modeling/customizing-copy-behavior.md)。|  
|在選擇的位置貼上圖形，例如目前的游標位置。|覆寫`ClipboardCommandSet.ProcessOnCopy()`要使用的特定位置的新版`ElementOperations.Merge().`看到[自訂複製行為](../modeling/customizing-copy-behavior.md)。|  
|貼上建立其他連結|覆寫 ClipboardCommandSet.ProcessOnPasteCommand()|  
|啟用從拖放此圖中，其他 Dsl 和 Windows 項目|請參閱[如何： 加入拖放的處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|允許圖形或工具，以將它們拖曳至 「 子 」 圖形，例如連接埠，如同它已拖曳至父代。|定義目標物件類別，已卸除的物件轉送給父項目合併指示詞。 請參閱[自訂項目建立和移動](../modeling/customizing-element-creation-and-movement.md)。|  
|允許圖形或將它們拖曳至圖形，並讓其他連結的工具或建立的物件。 例如，若要允許註解可以放到它為連結的項目。|項目合併指示詞在類別上定義目標網域，並定義要產生連結。 在複雜的情況下，您可以加入自訂程式碼。 請參閱[自訂項目建立和移動](../modeling/customizing-element-creation-and-movement.md)。|  
|使用其中一個工具，建立一組項目。 例如，具有一組固定的通訊埠的元件。|覆寫中 ToolboxHelper.cs 工具箱初始設定方法。 建立項目群組原型 (EGP) 包含的項目和其關聯性的連結。 請參閱[自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。<br /><br /> 請納入 EGP 的主體和連接埠圖形，或定義 BoundsRules EGP 具現化時連接埠圖案的位置。 請參閱[BoundsRules 限制圖形的位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)。|  
|您可以使用 一個連線工具來具現化的幾種類型的關聯性。|加入連接產生器工具所叫用連結連線指示詞 (LCD)。 LCDs 決定從兩個項目類型的關聯性的類型。 若要讓這項目的狀態而定，您可以加入自訂程式碼。 請參閱[自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)。|  
|自黏工具-使用者可以按兩下任何工具來建立許多圖形或連接器連續。|在 DSL 總管 中，選取 `Editor`節點。 在 [屬性] 視窗中，設定**使用自黏便箋的工具箱項目**。|  
|定義功能表命令|請參閱[如何： 修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|限制之模型的驗證規則|請參閱[中的網域特定定義域語言的驗證](../modeling/validation-in-a-domain-specific-language.md)|  
|DSL 從產生的程式碼、 組態檔或文件。|[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)|  
|自訂如何儲存模型檔案。|請參閱[自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|將模型儲存至資料庫或其他媒體。|覆寫*YourLanguage*DocData<br /><br /> 請參閱[自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|將數個 Dsl 整合，讓它們能夠做為一個應用程式的一部分。|請參閱[整合的模型，使用 Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。|  
|可讓您擴充第三方的 DSL 和控制擴充功能。|[使用 MEF 擴充您的 DSL](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [使用 DSL 程式庫共用 DSL 之間的類別](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [定義鎖定原則來建立唯讀區段](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|
  
## <a name="see-also"></a>請參閱  
 [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)   
 [撰寫程式碼以自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

