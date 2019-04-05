---
title: 編輯 UML 模型和圖表 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3cc16133911cf4b49af983aabb4b7b60405c956c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942328"
---
# <a name="edit-uml-models-and-diagrams"></a>編輯 UML 模型和圖表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以透過數種不同類型之圖表所提供的檢視來建立和編輯 UML 模型。 這些圖表在您的系統上提供不同的觀點，協助您了解並討論其設計和需求的不同層面。 Visual Studio 提供其中五個最常用的 UML 圖表類型的範本。  
  
 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 本主題描述用於編輯不同圖表類型通用之模型的技巧。 如為適合圖表的特定類型的詳細資訊，請參閱[建立應用程式模型](../modeling/create-models-for-your-app.md)。  
  
## <a name="in-this-topic"></a>本主題內容  
  
-   [UML 圖表是 UML 模型的檢視](#Views)  
  
-   [建立 UML 模型圖](#Creating)  
  
-   [繪製 UML 模型圖](#Drawing)  
  
-   [編輯圖形和接點](#Editing)  
  
-   [正在復原模型變更](#Undo)  
  
-   [圖表之間共用項目](#Sharing)  
  
-   [複製項目和相關的項目群組](#Copying)  
  
-   [刪除模型項目或它的檢視](#Deleting)  
  
-   [在圖表中搜尋文字](#Searching)  
  
-   [準備圖表進行簡報](#presentation)  
  
-   [擴充 UML 設計工具](#extensions)  
  
##  <a name="Views"></a> UML 圖表是 UML 模型的檢視  
 您只能在模型專案中建立和使用 UML 圖表。 如需如何建立圖表和專案的詳細資訊，請參閱[建立 UML 模型專案和圖表](../modeling/create-uml-modeling-projects-and-diagrams.md)。  
  
-   模型專案包含單一 UML 模型。 專案中的每個 UML 圖表都是 UML 模型的檢視。  
  
-   您可以看到中的模型**UML 模型總管**。 在 [**架構**功能表上，指向**Windows**，然後按一下**UML 模型總管]**。  
  
-   圖表上的每個圖形都是模型中項目的檢視。 在圖表上放置新圖形時，就會在模型中建立新項目。  
  
-   當您儲存任何圖表，Visual Studio 會儲存整個模型時，其所有圖表，以及模型專案檔。  
  
##  <a name="Creating"></a> 建立 UML 模型圖  
  
1. 在 **架構**功能表，在 Visual Studio 中，按一下 **新增 UML 或分層圖**。  
  
2. 選取並命名您的圖表。  
  
3. 在 **加入至模型專案**中，選取現有的模型專案，或選取**建立新的模型專案**。  
  
   > [!NOTE]
   >  模型圖必須存在於模型專案內。  
  
   您也可以在 [方案總管] 中將圖表加入現有的模型專案。 以滑鼠右鍵按一下模型專案，指向**新增**，然後按一下**新項目**。  
  
#### <a name="to-create-an-empty-uml-modeling-project"></a>建立空白 UML 模型專案  
  
- 上**檔案**功能表上，指向**新增**，按一下 **專案**，然後在**新專案**對話方塊中，按兩下**模型化專案**。  
  
  如需如何管理模型專案的詳細資訊，請參閱[建立 UML 模型專案和圖表](../modeling/create-uml-modeling-projects-and-diagrams.md)。  
  
##  <a name="Drawing"></a> 繪製 UML 模型圖  
 模型圖會顯示透過關聯性連結之模型項目的集合。 每個項目都會顯示為圖形，而每個關聯性都會顯示為兩個圖形的接點。  
  
 有兩種工具，一個適用於項目，另一個則適用於關聯性。 例如，在 UML 類別圖 [工具箱] 中，**類別**是項目工具，以及**關聯**是關聯性工具。  
  
> [!NOTE]
>  如果您想要特定圖表類型特有的資訊，請參閱[建立應用程式模型](../modeling/create-models-for-your-app.md)。  
  
#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>在 UML 模型圖中建立項目和關聯性  
  
1. 若要建立模型項目，請按一下 [工具箱] 中的項目工具，然後按一下您想要顯示它的圖表。 建立項目之後，請拖曳其控點來調整大小和形狀。  
  
    在某些情況下，您可以將新項目放到另一個項目內。 例如，在 UML 類別圖上，您可以將類別放到套件內。  
  
   > [!NOTE]
   >  如果看不到工具箱 中，按一下**工具箱**上**檢視**功能表。  
  
2. 若要建立關聯性，請按一下關聯性工具，並按一下您想要開始關聯性的項目，然後按一下您想要結束關聯性的項目。  
  
    不同類型的關聯性可以開始或結束於不同類型的項目。 例如，在 UML 類別圖上，[關聯] 關聯性不能開始或結束於 [註解] 項目上。  
  
   > [!NOTE]
   >  若要使用相同的工具數次，請按兩下工具。 當您完成時，按一下**指標**工具。  
  
   在某些類型的圖表中，您也可以繪製簡單圖形。 這些圖形不是模型的一部分，但是您可以使用它們來強調圖表的各部分，或將圖表分成不同的區域。  
  
##  <a name="Editing"></a> 編輯圖形和接點  
 如果調整圖形的大小或顏色，或是重新路由傳送接頭，並不會影響基礎模型。 不過，如果在圖表上或 [UML 模型總管] 中重新命名圖形，則也會在 [UML 模型總管] 以及呈現該項目的任何其他圖表中重新命名對應的項目。  
  
> [!NOTE]
>  具有簡單的方式可製作新的工具箱項目，以從中建立多組項目或具有所選擇屬性的項目。 如需詳細資訊，請參閱 <<c0> [ 定義自訂模型工具箱項目](../modeling/define-a-custom-modeling-toolbox-item.md)。  
  
 下圖顯示如何變更圖形大小或其名稱。  
  
 ![調整模型項目](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")  
  
> [!TIP]
>  內建命令不包括用於整齊地對齊圖形的命令。 不過，您可以輕鬆地建立您自己的對齊命令藉由複製程式碼範例中[在圖表上顯示 UML 模型](../modeling/display-a-uml-model-on-diagrams.md)。  
  
 下圖顯示如何調整接點或其標籤的路由和位置。  
  
 ![調整連接器](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")  
  
#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>將接頭的一端移至另一個圖形  
  
1. 執行下列任一步驟：  
  
   - 按下**CTRL**並移動該端。  
  
     \-或-  
  
   - 以滑鼠右鍵按一下連接器，然後按一下**重新連接**。  
  
2. 按一下您想要移動的接頭端。  
  
3. 按一下您想要將接頭移至其中的圖形。  
  
#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>變更項目、關聯性或圖表的色彩或其他屬性  
  
-   按一下項目，並設定的欄位**屬性**視窗。  
  
     如果您看**屬性** 視窗中，以滑鼠右鍵按一下項目，然後**屬性。**  
  
#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>在模型圖上放大和縮小  
  
-   按住不放**CTRL**鍵不放同時轉動滑鼠滾輪。  
  
     \-或-  
  
-   按住不放**CTRL + SHIFT**，然後按一下向左或右滑鼠按鈕。  
  
     \-或-  
  
-   在上**架構設計人員**工具列上，按一下加號 (**+**) 或減號 (**-**)，或選擇縮放層級。  
  
##  <a name="Searching"></a> 在圖表中搜尋  
 [快速尋找] 函式會尋找圖表上的項目。 您必須設定**查詢：** 要**目前文件**。  
  
#### <a name="to-search-for-text-in-a-modeling-diagram"></a>在模型圖中搜尋文字  
  
1.  按下**CTRL + F**。  
  
     \-或-  
  
     在 **編輯**功能表上，指向**尋找和取代**，然後按一下**快速尋找**。  
  
    > [!NOTE]
    >  在 [**尋找和取代**] 對話方塊中，您必須保留**查看**欄位設定為**目前文件**。 不支援其他選項。  
  
2.  輸入您想要尋找，然後按一下文字**尋找下一個**。  
  
    > [!NOTE]
    >  如果您想要尋找的文字是在已摺疊的圖形內部，則會反白顯示圖形。 展開圖形，，然後按一下**尋找下一個**一次。  
  
##  <a name="Undo"></a> 正在復原模型變更  
 您可以復原和取消復原您對模型和圖表所使用的變更**恢復**並**重做**上的命令**編輯**功能表。  
  
 **每個模型專案具有單一變更堆疊。** 所有您對模型和圖表所做的變更都會保留在此堆疊上。 此堆疊也包括從某個圖表到另一個圖表的焦點變更。 [復原] 命令會反轉此堆疊的變更。  
  
 例如，假設您執行這些作業：變更 Diagram1;將焦點變更至圖表 2;變更圖表 2。 復原變更時，第一個復原會反轉最後一個變更、下一個復原會將焦點移回圖表 1，而第三個復原會反轉對圖表 1 的變更。  
  
 **關閉圖表會截斷變更堆疊。** 如果您關閉圖表，則無法復原您已在該圖表中執行的變更，而且無法復原對模型或其任何圖表所做的較早變更。  
  
 **您無法恢復您正在編輯的屬性。** 在 [屬性] 視窗或圖表標籤中編輯屬性時，只能復原您已在該屬性中所做的變更。 按 ENTER 完成您在屬性中的變更，或按 ESC 予以取消。 您接著可以復原模型和圖表中的變更。  
  
 **關閉圖表而不儲存可能沒有預期的效果。** 如果您進行一些變更，然後關閉圖表而不加以儲存，則變更還是會保留在模型中。 如果您想要這樣做而不加以儲存，則建議關閉整個模型。  
  
##  <a name="Sharing"></a> 圖表之間共用項目  
 您可以讓模型項目的特定執行個體多次出現在圖表中。 這套用至類別、介面、元件、使用案例和行動。  
  
 如果您想要在不同的圖表中顯示不同群組的關聯性，則這十分有用。 例如，在某個圖表上，您可以顯示 Customer 與 Address 類別之間的關聯。 在另一個圖表上，您可以再顯示 Address 類別，而其關聯為 Postal Area。  
  
 選取模型項目在任何圖表上的任何檢視，或在 [UML 模型總管] 中選取它，即可變更其屬性 (例如名稱)。  
  
 每種圖表都只能顯示某種模型項目。 例如，您無法在元件圖上顯示使用案例。 因此，下列程序只適用於某些模型項目與圖表組合。  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>使用 UML 模型總管加入模型項目的新檢視  
  
1.  若要開啟  **UML 模型總管**上**架構**功能表上，指向**Windows**，然後按一下**UML 模型總管**。  
  
2.  拖曳的模型項目**UML 模型總管**到相容的圖表相同專案中。  
  
     即會出現提供模型項目檢視的圖形，也可能會有其他圖表或相同圖表上的檢視。  
  
    > [!NOTE]
    >  將類別或元件拖曳至循序圖時，效果會不同。 在該情況下，會建立其類型是該類別或元件的新生命線。 如需詳細資訊，請參閱[UML 循序圖：指導方針](../modeling/uml-sequence-diagrams-guidelines.md)。  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>使用貼上參考加入模型項目的新檢視  
  
1.  以滑鼠右鍵按一下 現有項目，然後按一下**複製**。  
  
    -   您可以同時複製數個項目。 按住 CTRL 鍵同時按一下每個項目，其中一項，以滑鼠右鍵按一下，然後按一下**複製**。  
  
2.  以滑鼠右鍵按一下相容圖表的空白部分，然後按一下**貼上參考**。  
  
     相同項目的另一個檢視隨即出現。  
  
    > [!NOTE]
    >  這不同於**貼上**命令，以在模型中建立新的項目。 如需詳細資訊，請參閱 <<c0> [ 複製項目和相關項目群組](#Copying)。  
  
> [!NOTE]
>  如果您將已透過關聯性連接之兩個模型項目的檢視加入圖表，則關聯性檢視也會出現在圖表上。 只有從圖表中移除其中一個項目，或從模型中刪除關聯性，才能刪除此檢視。  
  
##  <a name="Copying"></a> 複製項目和相關的項目群組  
 您可以複製並貼上模型項目，而且可以複製並貼上項目群組以及其間的關聯性。  
  
> [!NOTE]
>  **貼上**並**貼上參考**命令的效果不同。 **貼上**會建立新項目，其屬性就像這些複製的項目。 **貼上參考**會建立新的檢視表的相同項目。  
  
#### <a name="to-copy-elements-and-their-relationships"></a>複製項目和其關聯性  
  
1.  在具有您想要複製之項目的圖表中，選取一或多個項目。  
  
    > [!NOTE]
    >  您無法複製關聯性，但為項目群組一部分的關聯性除外。  
  
2.  在 **編輯**功能表上，按一下**複製**。  
  
3.  如果您想要將項目複製至另一個圖表，請建立新的圖表，或開啟現有圖表。  
  
4.  在 **編輯**功能表上，按一下**貼上**。  
  
    -   項目的複本以及在其間連結之任何關聯性的複本隨即出現。  
  
    -   每個新項目都會有新的自動產生名稱。  
  
5.  調整新項目與關聯性的位置、名稱和其他屬性。  
  
> [!NOTE]
>  您無法將模型項目從某個模型複製至另一個模型 (例如，如果您的相同方案中有兩個模型)。 但是，您可以將項目從某個圖表複製至另一個圖表。  
  
#### <a name="to-copy-an-entire-diagram"></a>複製整個圖表  
  
1. 建立新的圖表。  
  
2. 選取現有圖表中的所有項目、複製它們，並將它們貼入新的圖表。  
  
   在 [方案總管] 中進行複製和貼上，並無法複寫圖表。  
  
##  <a name="Deleting"></a> 刪除模型項目或它的檢視  
 某些種類的項目 (特別是分類器) 可以從圖表中移除，而不從模型中刪除它們。 分類器是在類別圖、元件圖和使用案例圖上顯示的主要項目。 它們會出現在多個圖表上。 這些類型的項目中，有兩個不同的命令：**從圖表移除**並**從模型刪除**。  
  
 反之，從圖表刪除關聯性時，一律會從模型予以刪除。  
  
> [!NOTE]
>  UML 圖表上特定種類的項目會有標籤。 透過在周圍繪製矩形來選取這類項目時，就可以選取標籤，但不是擁有這些標籤的項目。 不支援刪除透過這種方式選取的項目子集。 若要選取這些項目的子集，請按住**CTRL**鍵同時按一下每個項目。  
  
#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>從圖表移除分類器的檢視  
  
- 以滑鼠右鍵按一下圖表上的項目，然後按一下**從圖表移除**。  
  
  \-或-  
  
- 按一下圖表上的項目，然後按**刪除**索引鍵。  
  
  -   項目的這個檢視隨即消失。 項目會維持在模型中，但您仍然可以找到它**UML 模型總管**。 也會維持相同項目的任何其他檢視。  
  
  -   每個終止於此圖形的接頭都會從圖表中予以移除，但是它代表的關聯性會維持在模型中。 您所見的關聯性**UML 模型總管**下方**關聯性**，連接每個項目底下。  
  
#### <a name="to-delete-an-element-from-the-model"></a>從模型刪除項目  
  
-   請以滑鼠右鍵按一下項目中**UML 模型總管**或在上圖中，然後再按一下**從模型刪除**。  
  
    -   項目隨即會從其出現的每個圖表中刪除。  
  
    -   也會從模型中刪除每個終止於這個項目的關聯性。  
  
#### <a name="to-delete-a-relationship-from-the-model"></a>從模型刪除關聯性  
  
-   以滑鼠右鍵按一下 關聯性圖表或在**UML 模型總管**，然後按一下**從模型刪除**。  
  
    > [!CAUTION]
    >  您必須從模型移除關聯性，才能從圖表移除關聯性。  
  
     關聯性隨即會從模型中刪除，並從其出現的每個圖表中刪除。  
  
##  <a name="presentation"></a> 準備圖表進行簡報  
 下列功能可協助您將注意力放在圖表的特定部分、新增說明，或將圖表分成不同的興趣區域。  
  
-   您可以將圖表的任何部分複製至 Word、PowerPoint 或其他文件。 選取的圖形和連接器，您想要以滑鼠右鍵按一下，然後按一下**複製**。  
  
-   任何圖形或接頭的色彩隨即變更。 選取一個或多個圖形，並變更**色彩**屬性。 如果看不到 [屬性] 視窗，請按 **F4** 鍵。  
  
-   在某些種類的圖表，您可以繪製線條、 矩形和從省略符號**簡單的圖形**工具箱的區段。 這些圖形不會形成 UML 模型的一部分。  
  
-   加上標籤的區域，您可以從 工具箱 拖曳 註解，並將其**Transparent**屬性設 **，則為 True**。 與 [簡單圖形] 相同，註解不會形成 UML 模型的一部分，而且不會出現在 [UML 模型總管] 中。  
  
-   若要將附註和說明加入模型項目，您可以建立註解，然後將它們連結至項目。  
  
-   若要整齊地對齊圖表上的資料行或資料列圖形，您可以安裝 [對齊圖形] 命令。 這可做為範例 UML 擴充功能：[UML:若要對齊圖形的命令](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)  
  
### <a name="to-export-a-diagram-as-an-image"></a>將圖表匯出為影像  
 如需詳細資訊，請參閱 <<c0> [ 將圖表匯出為影像](../modeling/export-diagrams-as-images.md)。  
  
##  <a name="extensions"></a> 擴充 UML 設計工具  
 您可以將新功能加入 UML 工具，以及調整圖表標記法使其符合您自己的需求。 如需詳細資訊，請參閱 <<c0> [ 擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)。  
  
 有數個範例擴充功能可用。 您可以只安裝並使用它們，也可以使用它們的原始程式碼做為您專屬擴充功能的基礎。 範例包括：  
  
|||  
|-|-|  
|[對齊圖形](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)|可協助您清理圖表的功能表命令。|  
|[連結至 docs](http://code.msdn.microsoft.com/Link-UML-elements-to-0adbf5a8)|將任何 UML 項目連結至 Word 標題、PowerPoint 投影片、任何類型的檔案、UML 圖表或其他 UML 項目。 透過拖曳，即可輕鬆地建立連結。 稍後，您可以按兩下項目來查看已連結的項目。 例如，您可以將使用案例連結至 Word 規格或詳細活動圖，以及分鏡腳本投影片的動作。|  
|[快速輸入](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)|使用文字項目，快速建立模型。 用於擷取會議中的想法。|  
|[依據造型上色](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|根據造型將類別上色。 您可以輕鬆地擴充程式碼，使其適用於您自己的造型。|  
|[領域模型的簡介](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4)|方便商業模型的預設值。 預設會顯示不帶箭頭的關聯，而且作業不會出現在類別中。|  
  
## <a name="see-also"></a>另請參閱  
 [建立 UML 模型專案和圖表](../modeling/create-uml-modeling-projects-and-diagrams.md)   
 [分析並製作架構模型](../modeling/analyze-and-model-your-architecture.md)   
 [建立應用程式模型](../modeling/create-models-for-your-app.md)
