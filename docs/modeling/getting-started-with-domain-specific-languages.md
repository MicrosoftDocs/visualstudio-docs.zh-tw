---
title: 開始使用網域指定的語言
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 61fdb4b652b7fe74f3baf80c6e9d6332914a9a1e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="getting-started-with-domain-specific-languages"></a>開始使用網域指定的語言
本主題說明在定義和使用 Visual studio 使用 Modeling SDK 建立特定領域語言 (DSL) 的基本概念。

> [!NOTE]
> 在 Visual Studio 2017，文字範本轉換 SDK 及 Visual Studio Modeling SDK 會自動安裝時安裝 Visual Studio 的特定功能。 如需詳細資訊，請參閱[此部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/2016/12/12/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)。

如果您是 Dsl 的新手，我們建議您逐步**DSL 工具實驗室**，您可以找到此站台中： [Visualizaton and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>您可以使用網域特定語言來做什麼？
 特定領域語言是標記法，通常是圖形，用於特定用途而設計。 相反地，例如 UML 語言是一般用途。 在 DSL，您可以定義類型的模型項目和其關聯性，以及在螢幕上的呈現方式。

 當您設計 DSL 時，您可以將它做為 Visual Studio 整合擴充功能 (VSIX) 封裝的一部分散發。 使用 Visual Studio 中 DSL 使用者：

 ![家譜圖表、 工具箱和總管](../modeling/media/familyt_instance.png "FamilyT_Instance")

 表示法是非負數的 DSL 的組件。 這個標記法，VSIX 封裝會包含使用者可以套用至協助他們編輯並從他們的模型產生資料的工具。

 其中一個主要的應用程式的 Dsl 為產生程式碼、 組態檔和其他成品。 特別是在大型專案和產品線，其中將會建立數個變化的產品，從 Dsl 產生許多層面變數可以提供大幅增加可靠性和非常快速的回應需求變更。

 本概觀的其餘部分是導入了建立和使用 Visual Studio 中的特定領域語言的基本作業的逐步解說。

## <a name="prerequisites"></a>必要條件
 若要定義 DSL，您必須已安裝下列元件：

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Modeling SDK for Visual Studio||


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


## <a name="creating-a-dsl-solution"></a>建立 DSL 方案
 若要建立新的特定領域語言，您會使用網域特定語言專案範本建立新的 Visual Studio 方案。

#### <a name="to-create-a-dsl-solution"></a>建立 DSL 方案

1.  在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。

2.  在下**專案類型**，依序展開**其他專案類型**節點，然後按一下**擴充性**。

3.  按一下**網域特定語言設計工具**。

     ![[建立 DSL] 對話方塊](../modeling/media/create_dsldialog.png "Create_DSLDialog")

4.  在**名稱**方塊中，輸入**FamilyTree**。 按一下 [確定 **Deploying Office Solutions**]。

     **特定領域語言精靈**隨即開啟，並顯示一份範本 DSL 解決方案。

     按一下以查看描述，每個範本

     此範本是很有用起始點。 每個提供了完整的有效 DSL，您可以編輯以符合您的需求。 一般情況下，您會選擇最接近您要建立的範本。

5.  這個逐步解說中，選擇 **基本語言**範本。

6.  在適當的精靈頁面中輸入 DSL 的副檔名。 這是包含 DSL 將使用之執行個體的檔案的副檔名。

    -   選擇不在您的電腦，或您要安裝 DSL 任何電腦中的任何應用程式相關聯的擴充功能。 例如， **docx**和**htm**是無法接受檔案名稱的副檔名。

    -   如果您已輸入的副檔名正用來做為 DSL，精靈將會警告您。 請考慮使用不同的副檔名。 您也可以重設 Visual Studio SDK Experimental 執行個體以清除舊的實驗設計工具。 按一下**啟動**，按一下 **所有程式**， **Microsoft Visual Studio 2010 SDK**，**工具**，然後**重設 MicrosoftVisual Studio 2010 實驗性執行個體**。

7.  檢查其他頁面，然後按一下 **完成**。

     方案會產生包含兩個專案。 Dsl 和 DslPackage 的名稱。 圖表檔案，也就是開啟具名的 DslDefinition.dsl。

    > [!NOTE]
    >  大部分的程式碼，您可以在兩個專案中的資料夾中看到的是從 DslDefinition.dsl 產生。 基於這個理由，大部分 DSL 來修改此檔案中。

 這時使用者介面類似以下圖片。

 ![dsl 設計工具](../modeling/media/dsl_designer.png "dsl_designer")

 此方案定義網域指定的語言。 如需詳細資訊，請參閱[的特定領域語言工具使用者介面概觀](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md)。

## <a name="the-important-parts-of-the-dsl-solution"></a>DSL 解決方案的重要部分
 請注意新的方案的下列層面。

-   **Dsl\DslDefinition.dsl**這是您會看到當您建立 DSL 方案檔案。 在方案中幾乎所有的程式碼會產生這個檔案中，從大部分的變更，您對 DSL 定義不進行以下。 如需詳細資訊，請參閱使用[DSL 定義圖表使用](../modeling/working-with-the-dsl-definition-diagram.md)。

-   **Dsl 專案**此專案包含定義網域特定語言的程式碼。

-   **DslPackage 專案**此專案包含程式碼，讓 DSL 來開啟和編輯 Visual Studio 中的執行個體。

##  <a name="Debugging"></a> 執行 DSL
 一旦您已建立它，您可以執行 DSL 方案。 稍後，您可以修改 DSL 定義逐漸，每次變更之後，再次執行方案。

#### <a name="to-experiment-with-the-dsl"></a>若要試驗 DSL

1.  按一下**轉換所有範本**[方案總管] 工具列。 這會重新產生大部分的 DslDefinition.dsl 中的原始程式碼。

    > [!NOTE]
    >  每當您變更 DslDefinition.dsl，您必須按一下**轉換所有範本**重建方案之前。 您可以自動化此步驟。 如需詳細資訊，請參閱[如何自動化轉換的所有範本](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a)。

2.  按 F5，或在**偵錯**功能表上，按一下 **開始偵錯**。

     DSL 建置，並已安裝 Visual Studio 的實驗執行個體中。

     啟動 Visual studio 的實驗執行個體。 實驗執行個體會從個別的子樹的登錄，以進行偵錯註冊 Visual Studio 擴充功能的位置及其設定。 標準 Visual Studio 執行個體並沒有存取那里註冊的擴充功能。

3.  在 Visual Studio 的實驗執行個體，開啟模型檔名為**測試**從**方案總管 中**。

     \-或-

     以滑鼠右鍵按一下 偵錯專案，指向**新增**，然後按一下 **項目**。 在**加入項目**對話方塊方塊中，選取該檔案 DSL 的類型。

     模型檔案開啟為空白的圖表。

     工具箱 中開啟，並顯示適用於圖表類型的工具。

4.  若要在圖表上建立圖形和連接器使用的工具。

    1.  若要建立圖形，拖曳到圖表的範例圖形工具。

    2.  若要連接兩個圖形，按一下 範例連接器工具，按一下第一個圖形，，然後按一下第二個圖形。

5.  按一下 變更形狀的標籤。

 您的實驗性 Visual Studio 會類似下列的範例：

 ![](../modeling/media/dsl_min.png "DSL_min")

### <a name="the-content-of-a-model"></a>模型的內容
 DSL 的執行個體檔案的內容會呼叫*模型*。 模型包含*模型 * * 元素*和*連結*的項目之間。 DSL 定義指定的模型項目類型，可以存在於模型中的連結。 例如，在 DSL 基本語言範本所建立的沒有一種類型的模型項目和一種連結類型。

 DSL 定義可以指定在模型圖表上顯示的方式。 您可以選擇各種不同的圖形和連接器的樣式。 您可以指定某些圖形出現在其他圖形。

 您可以在樹狀結構檢視模型**總管**檢視您正在編輯的模型。 當您新增圖形至圖表時，模型項目也會出現在 [總管] 中。 即使沒有圖表，就可以使用 [總管] 中。

 如果您無法看到 總管 中的 Visual Studio 偵錯的執行個體上**檢視**功能表中的指向**其他視窗**，然後按一下  *\<您的語言 >***總管**。

### <a name="the-api-of-your-dsl"></a>DSL 的應用程式開發介面
 DSL 會產生一個 API，讓您讀取和更新模型的 DSL 執行個體。 一個應用程式的 api 是從模型產生文字檔案。 如需詳細資訊，請參閱[設計階段透過使用 T4 文字範本的程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。

 在偵錯方案中，開啟範本檔案以副檔名".tt"。 這些範例會示範如何從模型中，產生的文字，並可讓您測試 DSL 的 API。 其中一個範例以撰寫[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]、 在其他[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]。

 在每個範本檔案會是它會產生的檔案。 展開 [方案總管] 中的範本檔案並開啟產生的檔案。

 範本檔案包含簡短程式碼區段，列出模型中的所有項目。

 產生的檔案包含的結果。

 當您變更模型檔案時，您會看到對應中產生檔案的變更之後重新產生的檔案。

##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>若要重新產生文字檔案之後您, 變更模型檔案

1.  在 Visual Studio 的實驗執行個體，儲存模型檔案。

2.  請確定每個.tt 檔案中的檔案名稱參數，是指您用於實驗的模型檔案。 儲存.tt 檔案。

3.  按一下**轉換所有範本**的工具列中的**方案總管 中**。

     \-或-

     以滑鼠右鍵按一下您想要重新產生，然後按一下 範本**執行自訂工具**。

 您可以將任意數目的文字範本檔加入專案。 每個範本會產生一個結果檔案。

> [!NOTE]
>  當您變更 DSL 定義時，範例文字範本程式碼將無法運作，除非您更新它。

 如需詳細資訊，請參閱[特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)和[以自訂特定領域語言撰寫的程式碼](../modeling/writing-code-to-customise-a-domain-specific-language.md)。

## <a name="customizing-the-dsl"></a>自訂 DSL
 當您想要修改 DSL 定義時，關閉此實驗性執行個體，並更新主要 Visual Studio 執行個體中的定義。

> [!NOTE]
>  修改 DSL 定義之後，您可能會遺失您使用舊版建立的測試模型中的資訊。  例如，偵錯方案中包含名為範例，其中包含一些圖形和連接器的檔案。 您開始開發 DSL 定義之後，將不會顯示，及它們時將會遺失您儲存檔案。

 您可以對 DSL 的各種不同的擴充功能。 下列範例可讓您以為的可能性。

 DSL 定義中，儲存的每次變更後按一下**轉換所有範本**中**方案總管 中**，然後按下**F5**試驗變更 DSL。

### <a name="rename-the-types-and-tools"></a>重新命名類型和工具
 重新命名現有的網域類別和關聯性。 例如，最少的語言範本所建立的 Dsl 定義從開始，您就可以執行下列重新命名作業，以便代表系列樹 DSL。

##### <a name="to-rename-domain-classes-relationships-and-tools"></a>若要重新命名網域類別、 關聯和工具

1.  在 DslDefinition 圖表中，重新命名**ExampleModel**至**FamilyTreeModel**， **ExampleElement**至**人員**， **目標**至**父系**，和**來源**至**子系**。 您可以按一下每一個標籤加以變更。

     ![DSL 定義圖表&#45;王朝家譜模型](../modeling/media/familyt_person.png "FamilyT_Person")

2.  重新命名的項目和連接器工具。

    1.  在 [方案總管] 中，按一下索引標籤開啟 [DSL 總管] 視窗。 如果您看，在**檢視**功能表中的指向**其他視窗**，然後按一下  **DSL 總管**。 DSL 定義圖表是使用中視窗時，才看見 DSL 總管。

    2.  開啟 [屬性] 視窗並將它，讓您可以同時查看 DSL 總管和屬性。

    3.  在 DSL 總管 中，依序展開**編輯器**，**工具箱索引標籤**，  *\<DSL >*，然後**工具**。

    4.  按一下**ExampleElement**。 這是用來建立項目工具箱項目。

    5.  在 [屬性] 視窗中，變更**名稱**屬性**人員**。

         請注意，**標題**屬性也會變更。

    6.  同樣地，在變更名稱的**ExampleConnector**工具**ParentLink**。 Alter**標題**屬性，因此它不是一份名稱屬性。 例如，輸入**父連結**。

3.  重建 DSL。

    1.  儲存 DSL 定義檔案。

    2.  按一下**轉換所有範本**在方案總管 的工具列

    3.  按 F5。 請等到 Visual Studio 的實驗執行個體隨即出現。

4.  在偵錯方案中的 Visual Studio 實驗執行個體中，開啟測試模型檔。 從工具箱拖曳至其本身的項目。 請注意工具標題和 DSL 總管 中的型別名稱已經變更。

5.  儲存模型檔案。

6.  開啟.tt 檔案，並以新名稱取代舊的型別和屬性名稱的項目。

7.  請確定.tt 檔案中指定的檔案名稱指定測試模型。

8.  儲存.tt 檔案。 開啟產生的檔案，請參閱.tt 檔案中執行程式碼的結果。 請確認它正確。

### <a name="add-domain-properties-to-classes"></a>將網域屬性加入至類別
 將屬性加入至網域類別，例如若要代表的出生年份和死亡的個人。

 若要讓新的屬性顯示在圖表上，您必須新增*裝飾項目*圖形顯示的模型項目。 您也必須對應屬性來裝飾項目。

##### <a name="to-add-properties-and-display-them"></a>加入屬性並加以顯示

1.  加入屬性。

    1.  DSL 定義圖表中，以滑鼠右鍵按一下**人員**網域類別，指向**新增**，然後按一下 **網域屬性**。

    2.  輸入新的屬性名稱的清單，例如**出生**和**死亡**。 按**Enter**每一個之後。

2.  將裝飾項目，會顯示在圖形中的屬性。

    1.  請遵循灰線從個人網域類別延伸至圖表的另一端。 這是圖表項目對應。 它會連結網域類別圖形類別。

    2.  這個圖形類別上按一下滑鼠右鍵，指向**新增**，然後按一下 **文字裝飾項目的**。

    3.  將裝飾名稱的兩個項目，例如**BirthDecorator**和**DeathDecorator**。

    4.  選取每個新的裝飾項目，然後在 [屬性] 視窗中，設定**位置**欄位。 這會決定網域屬性值在圖形上的顯示位置。 例如，設定**InnerBottomLeft**和**InnerBottomRight**。

         ![區間圖案定義](../modeling/media/familyt_compartment.png "FamilyT_Compartment")

3.  將裝飾項目對應到屬性。

    1.  開啟 DSL 詳細資料視窗。 它通常是在 [輸出] 視窗旁邊的索引標籤。 如果您看，在**檢視**功能表上，指向**其他視窗**，然後按一下  **DSL 詳細資料**。

    2.  DSL 定義圖表中，按一下 連接的線條，**人員**網域圖形類別的類別。

    3.  在**DSL 詳細資料**上**裝飾項目的對應**索引標籤上，按一下 未對應的裝飾項目的核取方塊。 在**顯示屬性**，選取您想要其對應的網域屬性。 例如，對應**BirthDecorator**至**出生**。

4.  儲存 DSL、 按一下 轉換所有範本，然後按 F5。

5.  在範例模型中，確認，您現在可以按一下您所選擇的位置，並在其輸入的值。 此外，當您選取**人員**圖形，[屬性] 視窗會顯示生日及死亡的新屬性。

6.  .Tt 檔，在您可以加入程式碼會取得每個人員的屬性。

 ![家譜圖表、 工具箱和總管](../modeling/media/familyt_instance.png "FamilyT_Instance")

### <a name="define-new-classes"></a>定義新類別
 您可以加入網域類別和關聯性模型。 例如，您可以建立新的類別來代表城鎮，以及代表人員存在城鎮中新的關聯性。

 若要在模型圖表上進行不同的類型不同，您可以在不同的圖形，或使用不同的幾何和色彩對應網域類別。

##### <a name="to-add-and-display-a-new-domain-class"></a>新增及顯示新的網域類別

1.  加入網域類別，並將其模型根的子系。

    1.  DSL 定義圖表中，在按一下**內嵌關聯性**工具，請按一下根類別**FamilyTreeModel**，然後按一下圖表的空白部分。

         新的網域類別隨即出現，以及內嵌關聯性 FamilyTreeModel 連接。

         設定它的名稱，例如**城鎮**。

        > [!NOTE]
        >  每個目的領域類別除了根模型必須至少一個內嵌關聯性的目標或其一定會繼承自類別的內嵌目標。 基於這個原因，並經常方便使用的內嵌關聯性工具來建立網域類別。

    2.  將網域屬性加入到新的類別，例如**名稱**。

2.  新增人員與城市之間的參考關聯性。

    1.  按一下**參考關聯性**工具，按一下 人員，然後按一下 城鎮。

         ![DSL 定義片段： 家譜根部](../modeling/media/familyt_root.png "FamilyT_Root")

        > [!NOTE]
        >  參考關聯性可交互參照模型樹狀結構的一個部分從另一個。

3.  新增圖形以代表城鎮模型圖表上。

    1.  拖曳**幾何形狀**從工具箱拖曳到圖表中，並重新命名，例如**TownShape**。

    2.  在 [屬性] 視窗中設定外觀欄位的新圖形，例如填滿色彩和幾何。

    3.  加入顯示的城市名稱的裝飾項目，並將它重新命名 NameDecorator。 設定其位置屬性。

4.  對應 TownShape 城鎮網域類別。

    1.  按一下**圖表元素會對應**工具，然後按一下 城鎮領域類別，然後再 TownShape 圖形類別。

    2.  在**裝飾項目的對應** 索引標籤**DSL 詳細資料**選取具有對應連接器的視窗，請檢查 NameDecorator 並設定**顯示屬性**名稱。

5.  建立連接器，以顯示擁有人之間的關聯性。

    1.  將連接器從 [工具箱] 拖曳至圖表。 重新命名，並且設定其外觀屬性。

    2.  使用**圖表元素會對應**工具，以將新的連接器連結至人員城鎮之間的關聯性。

         ![已加入的圖案對應的家譜定義](../modeling/media/familyt_shapemap.png "FamilyT_ShapeMap")

6.  建立供新市區項目的工具。

    1.  在**DSL 總管**，依序展開**編輯器**然後**工具箱索引標籤**。

    2.  以滑鼠右鍵按一下 *\<DSL >* ，然後按一下 **加入新項目工具**。

    3.  設定**名稱**新工具與設定的屬性其**類別**城鎮的屬性。

    4.  設定**工具箱圖示**屬性。 按一下 **[…]** 和**檔案名稱**欄位中，選取 圖示檔。

7.  建立連接器工具，讓擁有人之間的連結。

    1.  以滑鼠右鍵按一下 *\<DSL >* ，然後按一下 **加入新的連接器工具**。

    2.  設定新工具的名稱屬性。

    3.  在**ConnectionBuilder**屬性中，選取 包含人員城鎮關聯性的名稱產生器。

    4.  設定**工具箱圖示**。

8.  儲存 DSL 定義，請按一下**轉換所有範本**，然後按下**F5**。

9. 在 Visual Studio 的實驗執行個體，開啟測試模型檔。 使用新的工具來建立城鎮和城鎮和人員之間的連結。 請注意，您可以只建立正確類型的項目之間的連結。

10. 建立列出的城鎮每個人存放所在的程式碼。 文字範本是其中一種您可以在其中執行這類程式碼的地方。 例如，您可以修改現有 Sample.tt 檔案偵錯方案中的，使其包含下列程式碼：

    ```
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>
    <#@ output extension=".txt" #>
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>

    <#
      foreach (Person person in this.FamilyTreeModel.People)
      {
    #>
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>

    <#
          foreach (Person child in person.Children)
      {
    #>
                <#= child.Name #>
    <#
      }
      }
    #>

    ```

     當您儲存 *.tt 檔案時，就會建立包含清單的人員，以及其 residences 的附帶檔案。 如需詳細資訊，請參閱[特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

## <a name="validation-and-commands"></a>驗證與命令
 若要開發此 DSL 進一步，無法加入驗證條件約束。 這些條件約束是方法，您可以定義，請確認模型處於正確狀態。 例如，您可以定義條件約束，確保的子系的出生日期晚於其父代的。 如果 DSL 使用者嘗試儲存會中斷任何條件約束的模型驗證功能會顯示警告。 如需詳細資訊，請參閱[中特定領域語言驗證](../modeling/validation-in-a-domain-specific-language.md)。

 您也可以定義使用者可以叫用的功能表命令。 命令可以修改模型。 Visual Studio 中的其他模型與外部資源時，它們也可以互動。 如需詳細資訊，請參閱[如何： 修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)。

## <a name="deploying-the-dsl"></a>部署 DSL
 若要讓其他使用者使用網域特定領域語言，您可以將 Visual Studio 擴充功能 (VSIX) 檔案來分配。 這會建立當您建置 DSL 解決方案。

 您的方案的 bin 資料夾中，找出.vsix 檔案。 請將它複製到您要安裝的電腦。 該電腦上，按兩下 VSIX 檔案。 DSL 可以用於 Visual Studio，在該電腦上的所有執行個體。

 您可以使用相同的程序，在您自己電腦上安裝 DSL，如此您不需要使用 Visual Studio 的實驗執行個體。

 如需詳細資訊，請參閱[部署特定領域語言方案](../modeling/deploying-domain-specific-language-solutions.md)。

##  <a name="Reset"></a> 移除舊的實驗 Dsl
 如果您已經建立，您不想再實驗 Dsl，則您可以重設 Visual Studio 實驗執行個體從電腦移除它們。

 會從電腦移除所有實驗性 Dsl 與其他實驗性 Visual Studio 擴充功能。 這些是已處於偵錯模式執行的擴充功能。

 Dsl 或其他已由執行 VSIX 檔案完整安裝的 Visual Studio 擴充功能，並不會移除此程序。

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>若要重設 Visual Studio 實驗執行個體

1.  按一下**啟動**，按一下 **所有程式**， **Microsoft Visual Studio 2010 SDK**，**工具**，然後**重設 MicrosoftVisual Studio 2010 實驗性執行個體**。

2.  重建任何實驗 Dsl 或您仍然想要使用其他實驗性 Visual Studio 擴充功能。

## <a name="see-also"></a>另請參閱

- [了解模型、類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)
- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)