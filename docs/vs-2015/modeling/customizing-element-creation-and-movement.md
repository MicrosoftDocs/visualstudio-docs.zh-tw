---
title: 自訂項目建立和移動 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
ms.assetid: cbd28f15-dfd7-46bd-ab79-5430e3ed83c8
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 589c8c9be01477a2319943b47b329d09a80dc16f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485864"
---
# <a name="customizing-element-creation-and-movement"></a>自訂項目的建立和移動
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[自訂項目的建立和移動](https://docs.microsoft.com/visualstudio/modeling/customizing-element-creation-and-movement)。  
  
您可以允許的項目拖曳至另一個，從工具箱 中，或是在貼上或移動作業。 您可以移動的項目連結至目標項目中，使用您指定的關聯性。  
  
 項目合併指示詞 (EMD) 可讓您指定一個模型項目時，會發生什麼事*合併*到另一個模型項目。 發生這種情況時：  
  
-   使用者將從 [工具箱] 拖曳到圖表或圖形。  
  
-   使用者會使用 [總管] 中或區間圖形中的 [新增] 功能表，以建立項目。  
  
-   使用者會從一個泳道項目移到另一個。  
  
-   使用者貼上項目。  
  
-   您的程式碼會呼叫項目合併指示詞。  
  
 建立作業可能不按照不同的複製操作，雖然它們實際運作方式相同。 當加入項目時，例如從 [工具箱] 中，它的原型會複寫。 原型會合併到模型中，做為模型的另一個組件已複製的項目相同的方式。  
  
 EMD 的責任是決定如何在模型中的特定位置合併物件群組。 特別是，它會決定哪些關聯性應該具現化，將合併的群組連結至模型。 您也可以自訂，以設定屬性，並建立其他物件。  
  
 ![DSL&#45;EMD&#95;Merge](../modeling/media/dsl-emd-merge.png "DSL-EMD_Merge")  
角色的項目合併指示詞  
  
 當您定義一個內嵌關聯性時，會自動產生 EMD。 當使用者將新的子執行個體新增至父代，EMD 此預設會建立關聯性的執行個體。 您可以修改這些預設 EMDs 中，例如藉由加入自訂程式碼。  
  
 您也可以加入自己 EMDs 在 DSL 定義中，若要讓使用者拖放或貼上的合併和接收端類別的不同組合。  
  
## <a name="defining-an-element-merge-directive"></a>定義項目合併指示詞  
 您可以將項目合併指示詞新增至網域類別、 網域關聯性、 圖形、 連接器和圖表。 您可以新增或接收的網域類別下 DSL 總管 中找到它們。 接收的類別是已經在模型中，並拖曳至新的或已複製的項目合併的項目網域類別。  
  
 ![DSL&#45;EMD&#95;Details](../modeling/media/dsl-emd-details.png "DSL-EMD_Details")  
  
 **編製索引類別**的合併接收類別成員的項目網域類別。 編製索引類別的子類別的執行個體將也由這個 EMD，合併，除非您設定**套用至子類別**為 False。  
  
 有兩種類型的合併指示詞：  
  
-   A**程序合併**指示詞會指定到樹狀結構，新的項目應連結的關聯性。  
  
-   A**向前合併**指示詞將新的項目重新導向至另一個接收項目，通常是父代。  
  
 您可以加入自訂程式碼來合併指示詞：  
  
-   設定**使用自訂接受**加入您自己的程式碼，以判斷是否應該在目標項目合併的編製索引的項目之特定執行個體。 當使用者從 [工具箱] 拖曳時，「 無效 」 的指標會顯示是否您的程式碼就不允許合併。  
  
     例如，您可以在接收端的項目處於特定狀態時才允許合併。  
  
-   設定**會使用自訂合併**將提供自己的程式碼，以定義當執行合併，對模型進行的變更。  
  
     比方說，您可以使用模型中的新位置中的資料，合併的項目中設定屬性。  
  
> [!NOTE]
>  如果您撰寫自訂的合併程式碼時，它會影響只使用此 EMD 執行的合併。 如果合併相同類型的物件，其他 EMDs，或如果沒有其他自訂程式碼，而不需使用 EMD 會建立這些物件，然後它們將不會影響您的自訂合併程式碼。  
>   
>  如果您想要確定新的項目或新的關聯性一律處理您的自訂程式碼，請考慮定義`AddRule`上的內嵌關聯性和`DeleteRule`項目的網域類別上。 如需詳細資訊，請參閱 <<c0> [ 規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
## <a name="example-defining-an-emd-without-custom-code"></a>範例： 定義 EMD 不需要自訂程式碼  
 下列範例可讓使用者在同一時間建立項目和連接器，從工具箱拖曳至 「 現有 」 圖形拖曳。 此範例會將 EMD 加入至 DSL 定義中。 之前這項修改，使用者可以將工具拖曳至圖表，但不是到現有的圖形。  
  
 使用者也可以貼到其他項目上的項目。  
  
#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>若要讓使用者在同一時間建立一個項目和連接器  
  
1.  使用建立新的 DSL**最小語言**解決方案範本。  
  
     當您執行此 DSL 時，它可讓您建立的圖形及圖形之間的連接器。 您無法將新**ExampleElement**圖形從工具箱拖曳到現有的圖形。  
  
2.  若要讓使用者合併項目`ExampleElement`圖形，建立新的 EMD 中`ExampleElement`網域類別：  
  
    1.  在  **DSL Explorer**，展開**網域類別**。 以滑鼠右鍵按一下`ExampleElement`，然後按一下 **加入新項目合併指示詞**。  
  
    2.  請確定**DSL 詳細資料**視窗已開啟，以便您可以看到新的 EMD 的詳細資料。 (功能表：**檢視**，**其他 Windows**， **DSL 詳細資料**。)  
  
3.  設定**編製索引類別**在 DSL 詳細資料視窗中，若要定義的項目 」 可合併`ExampleElement`物件。  
  
     此範例中，選取`ExampleElements`，如此一來，使用者可以將新的項目拖曳至現有的項目。  
  
     請注意編製索引類別會變成 EMD DSL 總管 中的名稱。  
  
4.  底下**藉由建立連結的程序合併**，新增兩個路徑：  
  
    1.  一個路徑會連結新項目連結至父模型。 您必須輸入的路徑運算式巡覽從現有的項目，向上的內嵌關聯性的父模型。 最後，它會在新的連結，將會指派新的項目中指定的角色。 路徑如下所示：  
  
         `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`  
  
    2.  在另一個路徑會連結新項目至現有的項目。 路徑運算式會指定參考關聯性和新的項目指派給角色。 此路徑如下所示：  
  
         `ExampleElementReferencesTargets.Sources`  
  
     您可以使用路徑瀏覽工具來建立每個路徑：  
  
    1.  底下**藉由在路徑中建立連結的程序合併**，按一下**\<新增路徑 >**。  
  
    2.  按一下清單項目右邊的下拉式箭號。 樹狀結構檢視隨即顯示。  
  
    3.  展開的節點在樹狀目錄中，以形成您想要指定的路徑。  
  
5.  測試 DSL:  
  
    1.  按 F5 以重新建置並執行方案。  
  
         重建將需要比平時更長，因為產生的程式碼將會從文字範本，以符合新的 DSL 定義中更新。  
  
    2.  當實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]已啟動，開啟您的 DSL 的模型檔案。 建立一些範例項目。  
  
    3.  從拖曳**範例項目**拖曳到現有的圖形工具。  
  
         新圖形隨即出現，並連結至現有的圖形與連接器。  
  
    4.  複製現有的圖形。 選取另一個圖形，並貼上。  
  
         會建立一份的第一個圖形。  它具有新名稱，它會連結至第二個的圖形與連接器。  
  
 請注意下列幾點，從這個程序：  
  
-   藉由建立項目合併指示詞，您可以允許任何要接受任何其他項目的類別。 EMD 建立在接收的網域類別中，而且公認的網域類別是在**編製索引類別**欄位。  
  
-   藉由定義路徑，您可以指定哪些連結應該用來將新的項目連接到現有的模型。  
  
     您指定的連結應包含一個內嵌關聯性。  
  
-   EMD 會影響用於建立從 [工具箱] 以及貼上作業。  
  
     如果您撰寫自訂程式碼，會建立新的項目時，您可以明確地使用叫用 EMD`ElementOperations.Merge`方法。 這可確保，您的程式碼連結新項目到模型中的其他作業相同的方式。 如需詳細資訊，請參閱 <<c0> [ 自訂複製行為](../modeling/customizing-copy-behavior.md)。  
  
## <a name="example-adding-custom-accept-code-to-an-emd"></a>範例： 將自訂接受的程式碼加入至 EMD  
 EMD 中加入自訂程式碼，您可以定義更複雜的合併行為。 這個簡單的範例可防止使用者將在超過固定數目的項目加入至圖表。 下列範例會修改預設 EMD 隨附一個內嵌關聯性。  
  
#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>撰寫自訂接受以限制使用者可以新增的程式碼  
  
1.  使用建立的 DSL**最小語言**解決方案範本。 開啟 DSL 定義圖。  
  
2.  在 [DSL 總管] 中，展開**網域類別**， `ExampleModel`，**項目合併指示詞**。 選取名為項目合併指示詞`ExampleElement`。  
  
     此 EMD 可讓您控制使用者如何建立新`ExampleElement`在模型中，例如藉由從 [工具箱] 拖曳的物件。  
  
3.  在  **DSL 詳細資料**視窗中，選取**使用自訂接受**。  
  
4.  重建方案。 這會使比平時更長，因為產生的程式碼將會從模型中更新。  
  
     建置錯誤會報告，類似於: 「 Company.ElementMergeSample.ExampleElement 不會包含定義的 CanMergeExampleElement...」  
  
     您必須實作方法`CanMergeExampleElement`。  
  
5.  建立新的程式碼檔案中**Dsl**專案。 其內容取代為下列程式碼，並將您專案的命名空間中的命名空間。  
  
    ```csharp  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace Company.ElementMergeSample // EDIT.  
    {  
      partial class ExampleModel  
      {  
        /// <summary>  
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.  
        /// This happens when the user pastes an ExampleElement  
        /// or drags from the toolbox.  
        /// Determines whether the merge is allowed.  
        /// </summary>  
        /// <param name="rootElement">The root element in the merging EGP.</param>  
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>  
        /// <returns>True if the merge is allowed</returns>  
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)  
        {  
          // Allow no more than 4 elements to be added:  
          return this.Elements.Count < 4;  
        }  
      }  
    }  
  
    ```  
  
     這個簡單的範例中，會限制可以合併至父模型的項目數。 更有趣的情況，此方法可以檢查任何屬性，以及接收物件的連結。 它也可以檢查的屬性合併的項目，位於<xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>。 如需詳細資訊`ElementGroupPrototypes`，請參閱 <<c2> [ 自訂複製行為](../modeling/customizing-copy-behavior.md)。 如需如何撰寫程式碼，讀取模型的詳細資訊，請參閱[巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
6.  測試 DSL:  
  
    1.  按 F5 以重新建置方案。 當實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]隨即開啟，並開啟您的 DSL 執行個體。  
  
    2.  以數種方式建立新的項目：  
  
        1.  從拖曳**範例項目**工具拖曳至圖表。  
  
        2.  在 **範例模型總管**，以滑鼠右鍵按一下根節點，然後按一下**新增新的範例項目**。  
  
        3.  複製並貼在圖表上的項目。  
  
    3.  請確認您無法使用任何一種方式，將四個以上的項目新增至模型。 這是因為它們都使用項目合併指示詞。  
  
## <a name="example-adding-custom-merge-code-to-an-emd"></a>範例： 將自訂合併程式碼加入至 EMD  
 在自訂的合併程式碼，您可以定義在使用者拖曳的工具，或貼上到項目時，會發生什麼事。 有兩種方式可定義自訂的合併：  
  
1.  設定**會使用自訂合併**並提供必要的程式碼。 您的程式碼取代產生的合併程式碼。 如果您想要完全重新定義合併的用途，請使用此選項。  
  
2.  覆寫`MergeRelate`方法，並選擇性地`MergeDisconnect`方法。 若要這樣做，您必須設定**產生雙衍生**網域類別的屬性。 您的程式碼可以呼叫產生的合併程式碼基底類別中。 如果您想要執行其他作業，在執行合併之後，請使用此選項。  
  
 這些方法只會影響使用此 EMD 執行的合併。 如果您想要影響所有的方式，可以在其中建立合併的項目，是定義替代`AddRule`上的內嵌關聯性和`DeleteRule`合併的網域類別上。 如需詳細資訊，請參閱 <<c0> [ 規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
#### <a name="to-override-mergerelate"></a>若要覆寫 MergeRelate  
  
1.  在 DSL 定義中，請確定您已定義您要加入的程式碼的 EMD。 如果您想，您可以新增路徑，並定義自訂接受程式碼，如先前各節中所述。  
  
2.  在 DslDefinition 圖表中，選取合併的接收的類別。 通常，它會是一個內嵌關聯性來源端的類別。  
  
     例如，在 DSL 產生之最小語言解決方案中，選取`ExampleModel`。  
  
3.  在 **屬性**視窗中，將**產生雙衍生**來**true**。  
  
4.  重建方案。  
  
5.  檢查的內容**Dsl\Generated Files\DomainClasses.cs**。 搜尋方法，名為`MergeRelate`並檢查其內容。 這將協助您撰寫您自己的版本。  
  
6.  在新的程式碼檔案中，請撰寫部分類別，為接收的類別並覆寫`MergeRelate`方法。 請務必呼叫基底方法。 例如:   
  
    ```csharp  
    partial class ExampleModel  
    {  
      /// <summary>  
      /// Called when the user drags or pastes an ExampleElement onto the diagram.  
      /// Sets the time of day as the name.  
      /// </summary>  
      /// <param name="sourceElement">Element to be added</param>  
      /// <param name="elementGroup">Elements to be merged</param>  
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)  
      {  
        // Connect the element according to the EMD:  
        base.MergeRelate(sourceElement, elementGroup);  
  
        // Custom actions:   
        ExampleElement mergingElement = sourceElement as ExampleElement;  
        if (mergingElement != null)  
        {  
          mergingElement.Name = DateTime.Now.ToLongTimeString();  
        }  
      }  
    }  
  
    ```  
  
#### <a name="to-write-custom-merge-code"></a>撰寫自訂合併程式碼  
  
1.  在  **Dsl\Generated Code\DomainClasses.cs**，檢查方法，名為`MergeRelate`。 這些方法會建立新的項目與現有的模型之間的連結。  
  
     此外，檢查方法，名為`MergeDisconnect`。 這些方法在被刪除時，取消連結從模型項目。  
  
2.  在 [ **DSL explorer]**，選取或建立項目合併指示詞，您想要自訂。 在  **DSL 詳細資料**視窗中，將**會使用自訂合併**。  
  
     當您設定此選項時，**程序合併**並**向前合併**則會忽略選項。 改為使用您的程式碼。  
  
3.  重建方案。 因為產生的程式碼檔案將會從模型中更新，它會比平時更長。  
  
     會出現錯誤訊息。 按兩下錯誤訊息，以查看產生的程式碼中的指示。 這些指示會要求您提供兩個方法： `MergeRelate` *YourDomainClass*並`MergeDisconnect` *YourDomainClass*  
  
4.  撰寫個別程式碼檔案中的部分類別定義的方法。 您在稍早所檢查的範例應建議您的需要。  
  
 自訂的合併程式碼不會影響程式碼會直接建立物件和關聯性，它不會影響其他 EMDs。 若要確定不論建立的項目是如何實作，您的其他變更，請考慮撰寫`AddRule`和`DeleteRule`改。 如需詳細資訊，請參閱 <<c0> [ 規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
## <a name="redirecting-a-merge-operation"></a>合併作業將重新導向  
 正向合併指示詞會重新導向為合併作業的目標。 一般而言，新的目標是內嵌的父代的初始目標。  
  
 例如，在使用元件圖範本建立 DSL 中，連接埠會內嵌在元件。 連接埠會顯示為 「 元件 」 圖形的邊緣上的小圖形。 使用者建立的連接埠，通訊埠工具拖曳到 「 元件 」 圖形。 但有時候，使用者不小心拖曳通訊埠工具拖曳至現有的連接埠，而不是元件，而導致作業失敗。 有數個現有的連接埠時，這是簡單的錯誤。 若要協助使用者避免這個麻煩，您可以讓連接埠，以將它們拖曳至現有的連接埠，但已重新導向至父元件的動作。 如同目標項目是元件，作業即可運作。  
  
 您可以建立正向合併指示詞的元件模型方案中。 如果您編譯並執行原始的方案，您應該會看到使用者可以將任意數目的**輸入連接埠**或是**輸出連接埠**中的項目**工具箱**至**元件**項目。 不過，他們也無法將連接埠拖曳到現有的連接埠。 無法使用的指標會警示他們未啟用這項移動。 不過，您可以建立正向合併指示詞，使連接埠，不小心卸除的現有**輸入連接埠**轉送給**元件**項目。  
  
#### <a name="to-create-a-forward-merge-directive"></a>若要建立正向合併指示詞  
  
1.  建立[!INCLUDE[dsl](../includes/dsl-md.md)]解決方案使用元件模型範本。  
  
2.  顯示**DSL explorer**開啟 DslDefinition.dsl。  
  
3.  在  **DSL Explorer**，展開**網域類別**。  
  
4.  **ComponentPort**抽象網域類別是基底類別同時**InPort**並**OutPort**。 以滑鼠右鍵按一下**ComponentPort** ，然後按一下**加入新項目合併指示詞**。  
  
     新**項目合併指示詞**下方的節點會出現**項目合併指示詞**節點。  
  
5.  選取 **項目合併指示詞**節點並開啟**DSL 詳細資料**視窗。  
  
6.  在索引類別清單中，選取**ComponentPort**。  
  
7.  選取 **將合併轉送至不同的網域類別**。  
  
8.  在 [路徑] 選取項目清單中，依序展開**ComponentPort**，展開**ComponentHasPorts**，然後選取**元件**。  
  
     新的路徑應該像這樣：  
  
     **ComponentHasPorts.Component/!Component**  
  
9. 儲存方案，並按一下最右邊的按鈕，以轉換範本**方案總管 中**工具列。  
  
10. 建置並執行方案。 新執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]隨即出現。  
  
11. 在 [**方案總管] 中**，開啟 Sample.mydsl。 圖表和**ComponentLanguage 工具箱**出現。  
  
12. 拖曳**輸入連接埠**從**工具箱**到另一個**輸入連接埠。** 下一步，拖曳**OutputPort**要**InputPort** ，再到另一個**OutputPort**。  
  
     您應該不會看到無法使用的指標，以及您應該能夠將新**輸入連接埠**上現有的憑證。 選取新**輸入連接埠**並將它拖曳至另一個點**元件**。  
  
## <a name="see-also"></a>另請參閱  
 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)   
 [電路圖表範例 DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)



