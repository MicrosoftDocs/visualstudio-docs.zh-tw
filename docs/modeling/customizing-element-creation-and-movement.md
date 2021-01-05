---
title: 自訂項目的建立和移動
description: 瞭解如何從 [工具箱] 或在 [貼上] 或 [移動] 作業中，允許將專案拖曳至另一個專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b84f638876270658be2f08a7e375540f0329a1d6
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729336"
---
# <a name="customizing-element-creation-and-movement"></a>自訂項目的建立和移動

您可以從 [工具箱] 或在 [貼上] 或 [移動] 作業中，允許將專案拖曳至另一個專案。 您可以使用您指定的關聯性，將已移動的元素連結至目標元素。

元素 merge 指示詞 (EMD) 指定當某個模型專案 *合併* 至另一個模型專案時，會發生什麼事。 發生這種情況的時機：

- 使用者從 [工具箱] 拖曳到圖表或圖形上。

- 使用者可以使用 [explorer] 或 [區間] 圖形中的 [新增] 功能表來建立元素。

- 使用者將專案從一個泳道移至另一個。

- 使用者貼上元素。

- 您的程式碼會呼叫 element merge 指示詞。

雖然建立作業似乎與複製作業不同，但實際上是以相同的方式運作。 當加入專案時（例如，從 [工具箱]），會複寫它的原型。 原型會合並到模型中，方法與從模型的另一個部分複製的元素相同。

EMD 的責任是決定物件或物件群組如何合併到模型中的特定位置。 尤其是，它會決定應該具現化哪些關聯性，以將合併的群組連結到模型。 您也可以自訂它來設定屬性，以及建立其他物件。

![當 E M D 決定新專案的加入方式時，圖表會顯示專案的樹狀結構和其參考關聯性。](../modeling/media/dsl-emd_merge.png)

當您定義內嵌關聯性時，會自動產生 EMD。 當使用者將新的子實例加入至父系時，此預設 EMD 會建立關聯性的實例。 您可以修改這些預設 EMDs，例如藉由新增自訂程式碼。

您也可以在 DSL 定義中新增自己的 EMDs，讓使用者可以拖曳或貼上合併和接收類別的不同組合。

## <a name="defining-an-element-merge-directive"></a>定義 Element Merge 指示詞

您可以將專案合併指示詞加入至網域類別、網域關聯性、圖形、連接器和圖表。 您可以在 [DSL Explorer] 中的 [接收網域] 類別底下新增或尋找它們。 接收類別是已在模型中之專案的網域類別，而新的或複製的元素將會合並到該類別。

![[DSL Explorer] 的螢幕擷取畫面，其中顯示已選取 [ExampleElement] 做為索引類別且已核取 [套用至子類別] 選項的 E M D。](../modeling/media/dsl-emd_details.png)

**索引類別** 是專案的網域類別，可以合併到接收類別的成員。 此 EMD 也會合並索引類別的子類別實例，除非您將 [ **套用至子類別** ] 設定為 [False]。

Merge 指示詞有兩種類型：

- **Process Merge** 指示詞會指定新元素應連結至樹狀結構的關聯性。

- **向前合併** 指示詞會將新的專案重新導向至另一個接收元素，通常是父元素。

您可以將自訂程式碼加入至 merge 指示詞：

- Set **使用自訂接受** 來新增您自己的程式碼，以判斷是否應該將索引項目目的特定實例合併到目標專案中。 當使用者從 [工具箱] 拖曳時，「無效」指標會顯示您的程式碼是否不允許合併。

   例如，您可以只在接收元素處於特定狀態時，才允許合併。

- Set **使用自訂合併** 來加入提供自己的程式碼，以定義執行合併時對模型所做的變更。

   例如，您可以使用模型中的新位置資料，在合併的元素中設定屬性。

> [!NOTE]
> 如果您撰寫自訂的合併程式碼，它只會影響使用此 EMD 執行的合併。 如果有其他 EMDs 合併相同類型的物件，或有其他自訂程式碼在不使用 EMD 的情況下建立這些物件，則它們不會受到自訂合併程式碼的影響。
>
> 如果您想要確定新元素或新的關聯性一律由自訂程式碼處理，請考慮在內嵌 `AddRule` 關聯性上定義，並 `DeleteRule` 在專案的網域類別上定義。 如需詳細資訊，請參閱 [規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。

## <a name="example-defining-an-emd-without-custom-code"></a>範例：定義沒有自訂程式碼的 EMD

下列範例可讓使用者從 [工具箱] 拖曳至現有的圖形，同時建立元素和連接器。 此範例會將 EMD 新增至 DSL 定義。 在進行這種修改之前，使用者可以將工具拖曳至圖表上，而不是在現有的圖形上。

使用者也可以將專案貼到其他元素。

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>讓使用者同時建立元素和連接器

1. 使用 **最基本的語言** 解決方案範本來建立新的 DSL。

    當您執行此 DSL 時，可讓您在圖形之間建立圖案和接點。 您無法將新的 [ **ExampleElement** ] 圖形從 [工具箱] 拖曳至現有的圖形。

2. 若要讓使用者將元素合併到 `ExampleElement` 圖形上，請在網域類別中建立新的 EMD `ExampleElement` ：

   1. 在 [ **DSL Explorer**] 中，展開 [ **網域類別**]。 以滑鼠右鍵按一下 `ExampleElement` ，然後按一下 [ **加入新元素合併** 指示詞]。

   2. 請確定 [ **DSL 詳細資料** ] 視窗已開啟，讓您可以查看新 EMD 的詳細資料。  (功能表： **查看**、 **其他視窗**、 **DSL 詳細資料**。 ) 

3. 在 [DSL 詳細資料] 視窗中設定 [ **索引] 類別** ，以定義哪些類別的專案可以合併至 `ExampleElement` 物件。

    在此範例中，請選取 `ExampleElements` ，讓使用者可以將新的專案拖曳到現有的元素。

    請注意，索引類別會變成 [DSL Explorer] 中的 EMD 名稱。

4. 在 [ **建立連結的進程合併**] 下，新增兩個路徑：

   - 其中一個路徑會將新元素連結至父模型。 您需要輸入的路徑運算式會從現有的專案中流覽，直到父模型的內嵌關聯性。 最後，它會在新的連結中指定要指派新元素的角色。 路徑如下所示：

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - 另一個路徑會將新元素連結至現有的專案。 路徑運算式會指定參考關聯性，以及將指派新元素的角色。 此路徑如下所示：

      `ExampleElementReferencesTargets.Sources`

      您可以使用路徑流覽工具來建立每個路徑：

      1. 在 [在 **路徑上建立連結的進程合併**] 下，按一下 **\<add path>** 。

      2. 按一下清單專案右邊的下拉箭號。 樹狀檢視隨即出現。

      3. 展開樹狀結構中的節點，以形成您要指定的路徑。

5. 測試 DSL：

   1. 按 **F5** 以重建並執行方案。

        重建所花費的時間比平常長，因為產生的程式碼會從文字模板中更新，以符合新的 DSL 定義。

   2. 當 Visual Studio 的實驗實例啟動時，開啟 DSL 的模型檔案。 建立一些範例元素。

   3. 從 [ **範例元素** ] 工具拖曳至現有的圖形。

        新的圖形隨即出現，並連結至具有連接器的現有圖形。

   4. 複製現有的圖形。 選取另一個圖形並貼上。

        建立第一個圖形的複本。  它有新的名稱，而且它會連結到具有連接器的第二個圖形。

請注意此程式中的下列幾點：

- 藉由建立元素合併指示詞，您可以允許任何專案類別接受任何其他類別。 EMD 是在接收的網域類別中建立，而 [ **索引類別** ] 欄位中指定了 [可接受的網域] 類別。

- 藉由定義路徑，您可以指定哪些連結應該用來將新元素連接至現有的模型。

     您指定的連結應該包含一個內嵌關聯性。

- EMD 會影響 [工具箱] 中的建立作業，也會貼上作業。

     如果您撰寫自訂程式碼來建立新的元素，您可以使用方法明確地叫用 EMD `ElementOperations.Merge` 。 這可確保您的程式碼會以與其他作業相同的方式，將新元素連結到模型。 如需詳細資訊，請參閱 [自訂複製行為](../modeling/customizing-copy-behavior.md)。

## <a name="example-adding-custom-accept-code-to-an-emd"></a>範例：將自訂接受程式碼新增至 EMD

藉由將自訂程式碼加入至 EMD，您可以定義更複雜的合併行為。 這個簡單的範例會防止使用者在圖表中新增超過固定數目的元素。 此範例會修改隨附內嵌關聯性的預設 EMD。

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>撰寫自訂接受程式碼以限制使用者可以新增的內容

1. 使用 **最基本的語言** 解決方案範本來建立 DSL。 開啟 DSL 定義圖表。

2. 在 [DSL Explorer] 中，展開 [ **網域類別**]、[ `ExampleModel` **元素合併** 指示詞]。 選取名為的 element merge 指示詞 `ExampleElement` 。

     此 EMD 可控制使用者如何 `ExampleElement` 在模型中建立新的物件，例如從 [工具箱] 拖曳。

3. 在 [ **DSL 詳細資料** ] 視窗中，選取 [ **使用自訂接受**]。

4. 重建方案。 這需要比平常更長的時間，因為產生的程式碼將會從模型更新。

     將會報告組建錯誤，類似于：「ElementMergeSample. ExampleElement 不包含 CanMergeExampleElement 的定義 ...」

     您必須執行方法 `CanMergeExampleElement` 。

5. 在 **Dsl** 專案中建立新的程式碼檔案。 將其內容取代為下列程式碼，並將命名空間變更為您專案的命名空間。

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

    這個簡單的範例會限制可合併到父模型的專案數目。 如需更有趣的條件，方法可以檢查接收物件的任何屬性和連結。 它也可以檢查合併專案的屬性，這些屬性會在中執行 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> 。 如需的詳細資訊 `ElementGroupPrototypes` ，請參閱 [自訂複製行為](../modeling/customizing-copy-behavior.md)。 如需如何撰寫可讀取模型之程式碼的詳細資訊，請參閱 [在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

6. 測試 DSL：

    1. 按 **F5** 以重建解決方案。 當 Visual Studio 的實驗實例開啟時，開啟您的 DSL 實例。

    2. 以數種方式建立新元素：

        - 從 [ **範例元素** ] 工具拖曳至圖表上。

        - 在 **範例模型瀏覽器** 中，以滑鼠右鍵按一下根節點，然後按一下 [ **加入新的範例元素**]。

        - 複製並貼上圖表上的元素。

    3. 確認您無法使用上述任何一種方式，將四個以上的元素加入至模型。 這是因為它們都使用 Element Merge 指示詞。

## <a name="example-adding-custom-merge-code-to-an-emd"></a>範例：將自訂合併程式碼新增至 EMD

在自訂合併程式碼中，您可以定義當使用者拖曳工具或貼上專案時，會發生什麼事。 有兩種方式可定義自訂合併：

1. Set **使用自訂合併** ，並提供必要的程式碼。 您的程式碼會取代產生的合併程式碼。 如果您想要完整重新定義合併的用途，請使用此選項。

2. 覆寫 `MergeRelate` 方法，並選擇性地覆寫 `MergeDisconnect` 方法。 若要這樣做，您必須設定網域類別的 [ **產生雙重衍生** ] 屬性。 您的程式碼可以呼叫基底類別中產生的合併程式碼。 如果您想要在執行合併之後執行其他作業，請使用此選項。

   這些方法只會影響使用此 EMD 執行的合併。 如果您想要影響可建立合併專案的所有方法，替代方式是在內嵌關聯性上定義， `AddRule` 並 `DeleteRule` 在合併的網域類別上定義。 如需詳細資訊，請參閱 [規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。

### <a name="to-override-mergerelate"></a>覆寫 MergeRelate

1. 在 DSL 定義中，請確定您已定義要新增程式碼的 EMD。 如有需要，您可以加入路徑，並定義自訂接受程式碼，如先前幾節中所述。

2. 在 Dsldefinition.dsl 檔圖中，選取 [合併] 的 [接收] 類別。 一般而言，它是內嵌關聯性之來源端的類別。

     例如，在以最基礎語言方案產生的 DSL 中，選取 `ExampleModel` 。

3. 在 [**屬性**] 視窗中，Set 會產生衍生為 **True** 的 **雙精度浮點數**。

4. 重建方案。

5. 檢查 **Dsl\Generated Files\DomainClasses.cs** 的內容。 搜尋名為的方法 `MergeRelate` ，並檢查其內容。 這將協助您撰寫自己的版本。

6. 在新的程式碼檔案中，撰寫接收類別的部分類別，並覆寫 `MergeRelate` 方法。 請記得呼叫基底方法。 例如：

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

### <a name="to-write-custom-merge-code"></a>撰寫自訂的合併程式碼

1. 在 **Dsl\Generated Code\DomainClasses.cs** 中，檢查名為 `MergeRelate` 的方法。 這些方法會建立新元素與現有模型之間的連結。

    此外，請檢查名為 `MergeDisconnect` 的方法。 這些方法會在刪除專案時，將其與模型取消連結。

2. 在 [ **DSL Explorer**] 中，選取或建立您想要自訂的 Element Merge 指示詞。 在 [ **DSL 詳細資料** ] 視窗中，設定 [ **使用自訂合併**]。

    當您設定此選項時，會忽略 **處理合併** 和 **轉寄合併** 選項。 改為使用您的程式碼。

3. 重建方案。 因為產生的程式碼檔案將會從模型更新，所以需要比平常更長的時間。

    將會出現錯誤訊息。 按兩下錯誤訊息，以查看產生的程式碼中的指示。 這些指示會要求您提供兩種方法： `MergeRelate` *YourDomainClass* 和 `MergeDisconnect` *YourDomainClass*

4. 以個別的程式碼檔案，在部分類別定義中撰寫方法。 您先前檢查的範例應該會建議您需要的內容。

   自訂合併程式碼不會影響直接建立物件和關聯性的程式碼，而且不會影響其他 EMDs。 若要確保不論專案的建立方式為何都會執行您的其他變更，請考慮改為撰寫 `AddRule` 和 `DeleteRule` 。 如需詳細資訊，請參閱 [規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。

## <a name="redirecting-a-merge-operation"></a>重新導向合併作業

向前合併指令程式會重新導向合併作業的目標。 一般來說，新的目標是初始目標的內嵌父系。

例如，在使用「元件圖」範本建立的 DSL 中，埠會內嵌在元件中。 埠會顯示為元件圖形邊緣上的小圖形。 使用者藉由將 [埠] 工具拖曳至元件圖形來建立埠。 但是，使用者有時會錯誤地將埠工具拖曳到現有的埠，而不是元件，而作業會失敗。 當有數個現有的埠時，這是個很簡單的錯誤。 若要協助使用者避免這種麻煩，您可以允許將埠拖曳到現有的埠，但將動作重新導向至父元件。 此作業的運作方式就像是將目標元素設為元件一樣。

您可以在元件模型方案中建立向前合併指示詞。 如果您編譯並執行原始解決方案，您應該會看到使用者可以從 [**工具箱**] 將任何數目的 **輸入埠** 或 **輸出埠** 專案拖曳至 **元件** 元素。 不過，他們無法將埠拖曳到現有的埠。 無法使用的指標會在未啟用這項移動時發出警示。 不過，您可以建立向前合併指示詞，讓在現有 **輸入埠** 上不小心卸載的埠轉送至 **元件** 專案。

### <a name="to-create-a-forward-merge-directive"></a>若要建立向前合併指令詞

1. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]使用元件模型範本建立方案。

2. 開啟 Dsldefinition.dsl 檔以顯示 [ **Dsl Explorer** ]。

3. 在 [ **DSL Explorer**] 中，展開 [ **網域類別**]。

4. **ComponentPort** 抽象網域類別是 **InPort** 和 **OutPort** 的基類。 以滑鼠右鍵按一下 [ **ComponentPort** ]，然後按一下 [ **加入新元素合併** 指示詞]。

    新的 [專案 **合併** 指示詞] 節點會出現在 [ **元素合併** 指示詞] 節點底下。

5. 選取 [ **Element Merge** 指示詞] 節點，然後開啟 [ **DSL 詳細資料** ] 視窗。

6. 在 [索引類別] 清單中，選取 [ **ComponentPort**]。

7. 選取 [ **向前合併至不同的網域類別**]。

8. 在 [路徑選取範圍] 清單中，展開 [ **ComponentPort**]，展開 [ **ComponentHasPorts**]，然後選取 [ **元件**]。

    新路徑看起來應該像這樣：

    **ComponentHasPorts 元件/！元件**

9. 儲存方案，然後按一下 [ **方案總管** ] 工具列上最右邊的按鈕來轉換範本。

10. 建置並執行解決方案。 Visual Studio 的新實例隨即出現。

11. 在 **方案總管** 中，開啟 mydsl。 [圖表] 和 [ **ComponentLanguage 工具箱** ] 隨即出現。

12. 將 **輸入埠** 從 [ **工具箱** ] 拖曳到另一個 **輸入埠。** 接下來，將 **OutputPort** 拖曳至 **InputPort** ，然後拖曳到另一個 **OutputPort**。

     您應該不會看到無法使用的指標，而且應該能夠將新的輸入埠放在現有的 **輸入埠** 上。 選取新的 **輸入埠** ，然後將它拖曳到 **元件** 上的另一個點。

## <a name="see-also"></a>請參閱

- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [自訂工具和工具箱](../modeling/customizing-tools-and-the-toolbox.md)
- [電路圖範例 DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
