---
title: 使用特定領域語言的消費者入門 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a2757201f482682b8fdf26275f510984629204f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300913"
---
# <a name="getting-started-with-domain-specific-languages"></a>開始使用網域指定的語言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題說明定義和使用以模型 SDK for Visual Studio 建立的特定領域語言（DSL）的基本概念。

 如果您不熟悉 Dsl，建議您透過**DSL 工具實驗室**來進行，您可以在此網站中找到： [Visualizaton 和模型化 SDK](https://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>您可以使用特定領域語言來做什麼？
 網域指定的語言是一種標記法，通常是圖形化，專門設計用於特定用途。 相反地，UML 這類語言就是一般用途。 在 DSL 中，您可以定義模型專案和其關聯性的類型，以及它們在畫面上的呈現方式。

 當您已設計 DSL 時，您可以將它散發為 Visual Studio 整合擴充功能（VSIX）封裝的一部分。 使用者可以在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中使用 DSL：

 ![系列樹圖表、工具箱和 explorer](../modeling/media/familyt-instance.png "FamilyT_Instance")

 標記法只是 DSL 的一部分。 除了標記法，您的 VSIX 封裝還包含使用者可以套用的工具，以協助他們從其模型編輯和產生材質。

 Dsl 的其中一個主要應用程式是產生程式碼、設定檔和其他成品。 特別是在大型專案和產品線中，將會建立產品的數種變化，從 Dsl 產生許多變動層面可以提供較大的可靠性，以及對需求變更的快速回應。

 本總覽的其餘部分是逐步解說，介紹在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中建立和使用特定領域語言的基本作業。

## <a name="prerequisites"></a>先決條件
 若要定義 DSL，您必須已安裝下列元件：

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](https://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio 的模型化 SDK|[下載 MSDK](https://www.microsoft.com/download/details.aspx?id=48148)|

## <a name="creating-a-dsl-solution"></a>建立 DSL 解決方案
 若要建立新的特定領域語言，請使用 [網域指定的語言] 專案範本建立新的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案。

#### <a name="to-create-a-dsl-solution"></a>建立 DSL 方案

1. 在 [檔案] **Deploying Office Solutions** 功能表中，指向 [新增]，然後按一下 [專案]。

2. 在 [**專案類型**] 底下，展開 [**其他專案類型**] 節點，**然後按一下 [** 擴充性]。

3. 按一下 [**網域指定的語言設計**工具]。

    ![建立 DSL 對話方塊](../modeling/media/create-dsldialog.png "Create_DSLDialog")

4. 在 [**名稱**] 方塊中，輸入**FamilyTree**。 按一下 [**確定**]。

    [**網域指定的語言嚮導]** 隨即開啟，並顯示範本 DSL 解決方案的清單。

    按一下每個範本以查看描述，

    這些範本是很有用的起點。 其中每個都提供完整的可運作 DSL，您可以視需要進行編輯以符合您的需求。 通常，您會選擇最接近您要建立之內容的範本。

5. 在此逐步解說中，選擇 [**最小語言**] 範本。

6. 在適當的精靈頁面中輸入 DSL 的副檔名。 這是包含 DSL 將使用之執行個體的檔案的副檔名。

   - 選擇與您電腦中的任何應用程式無關的延伸模組，或是在您要安裝 DSL 的任何電腦上。 例如， **.docx**和**htm**會是無法接受的副檔名。

   - 如果您已輸入的副檔名正用來做為 DSL，精靈將會警告您。 請考慮使用不同的副檔名。 您也可以重設 Visual Studio SDK Experimental 執行個體以清除舊的實驗設計工具。 請依序按一下 [開始]、[所有程式]、[Microsoft Visual Studio 2010 SDK]、[工具]，然後按一下 [重設 Microsoft Visual Studio 2010 Experimental 執行個體]。

7. 檢查其他頁面，然後按一下 **[完成]** 。

    會產生包含兩個專案的方案。 其命名為 Dsl 和 DslPackage。 隨即會開啟名為 Dsldefinition.dsl 檔的圖表檔案。

   > [!NOTE]
   > 您可以在這兩個專案的資料夾中看到的大部分程式碼都是從 Dsldefinition.dsl 檔產生的。 基於這個理由，對您的 DSL 進行的大部分修改都是在此檔案中進行。

   這時使用者介面類似以下圖片。

   ![DSL 設計工具](../modeling/media/dsl-designer.png "dsl_designer")

   此方案定義網域指定的語言。 如需詳細資訊，請參閱[特定領域語言工具使用者介面的總覽](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md)。

## <a name="the-important-parts-of-the-dsl-solution"></a>DSL 解決方案的重要部分
 請注意新解決方案的下列層面。

- **Dsl\DslDefinition.dsl**這是您在建立 DSL 解決方案時所看到的檔案。 幾乎解決方案中的所有程式碼都是從這個檔案產生的，而您對 DSL 定義所做的大部分變更都是在這裡進行。 如需詳細資訊，請參閱使用[DSL 定義圖](../modeling/working-with-the-dsl-definition-diagram.md)。

- **Dsl 專案**此專案包含可定義特定領域語言的程式碼。

- **DslPackage 專案**此專案包含的程式碼可讓您在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中開啟和編輯 DSL 的實例。

## <a name="Debugging"></a>執行 DSL
 您可以在建立 DSL 解決方案後立即執行。 之後，您可以逐步修改 DSL 定義，在每次變更之後再次執行解決方案。

#### <a name="to-experiment-with-the-dsl"></a>若要使用 DSL 進行實驗

1. 在 [方案總管] 工具列中，按一下 [轉換所有範本]。 這會從 Dsldefinition.dsl 檔重新產生大部分的原始程式碼。

   > [!NOTE]
   > 每當您變更 Dsldefinition.dsl 檔時，必須先按一下 [**轉換所有範本**]，然後再重建方案。 您可以自動化此步驟。 如需詳細資訊，請參閱[如何自動化轉換所有範本](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a)。

2. 按 F5 鍵，或在 [**調試**] 功能表上，按一下 [**開始調試**]。

    DSL 會建立並安裝在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的實驗實例中。

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗執行個體隨即啟動。 實驗實例會從登錄的個別子樹中取得其設定，其中 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組會針對進行調試而註冊。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的一般實例無法存取已在該處註冊的延伸模組。

3. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的實驗實例中，從**方案總管**開啟名為**Test**的模型檔案。

    \-或-

    以滑鼠右鍵按一下 [調試] 專案，指向 [**加入**]，然後按一下 [**專案**]。 在 [**新增專案**] 對話方塊中，選取 DSL 的檔案類型。

    模型檔案會以空白圖表的形式開啟。

    [工具箱] 隨即開啟，並顯示適用于圖表類型的工具。

4. 使用工具，在圖表上建立圖形和連接器。

   1. 若要建立圖形，請從範例圖形工具拖曳至圖表。

   2. 若要連接兩個圖形，請按一下 [範例連接器] 工具，按一下第一個圖形，然後按一下第二個圖形。

5. 按一下圖形的標籤來變更它們。

   您的實驗性 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 如下列範例所示：

   ![](../modeling/media/dsl-min.png "DSL_min")

### <a name="the-content-of-a-model"></a>模型的內容
 屬於 DSL 實例的檔案內容稱為「模型」（ *model*）。 模型包含專案之間的*模型元素*和*連結*。 DSL 定義會指定模型專案和連結可以存在哪些類型。 例如，在從最小語言範本建立的 DSL 中，有一種類型的模型專案，以及一種連結類型。

 DSL 定義可以指定模型在圖表上的顯示方式。 您可以從各種不同的圖案和連接器樣式中進行選擇。 您可以指定某些圖形出現在其他圖形內。

 當您編輯模型時，您可以將模型視為**瀏覽器**視圖中的樹狀結構。 當您將圖形加入至圖表時，模型元素也會出現在 explorer 中。 即使沒有圖表，也可以使用 explorer。

 如果您在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的偵錯工具實例中看不到 Explorer，請在 [ **View** ] 功能表上指向 [**其他視窗**]，然後按一下 [ *\<您的語言 >* **Explorer**]。

### <a name="the-api-of-your-dsl"></a>DSL 的 API
 您的 DSL 會產生 API，可讓您讀取和更新屬於 DSL 實例的模型。 API 的其中一個應用程式是從模型產生文字檔。 如需詳細資訊，請參閱[使用 T4 文字模板產生設計階段程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。

 在調試方案中，開啟副檔名為 ". tt" 的範本檔案。 這些範例會示範如何從模型產生文字，並可讓您測試 DSL 的 API。 其中一個範例是以 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]的方式撰寫，另一個則 [!INCLUDE[csprcs](../includes/csprcs-md.md)]。

 在每個範本檔案下，都是它所產生的檔案。 在方案總管中展開範本檔案，然後開啟產生的檔案。

 範本檔案包含簡短的程式碼區段，其中列出模型中的所有元素。

 產生的檔案包含結果。

 當您變更模型檔案時，您會在重新產生檔案之後，看到產生的檔案中有對應的變更。

##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>變更模型檔案之後重新產生文字檔

1. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的實驗實例中，儲存模型檔案。

2. 請確定每個 tt 檔案中的檔案名參數都是指您用於實驗的模型檔案。 儲存 tt 檔案。

3. 按一下**方案總管**工具列中的 [**轉換所有範本**]。

    \-或-

    以滑鼠右鍵按一下您要重新產生的範本，然後按一下 [**執行自訂工具**]。

   您可以將任意數目的文字模板檔案加入至專案。 每個範本都會產生一個結果檔案。

> [!NOTE]
> 當您變更 DSL 定義時，除非您將其更新，否則範例文字模板程式碼將無法正常執行。

 如需詳細資訊，請參閱[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)和[撰寫程式碼，以自訂域特定語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)。

## <a name="customizing-the-dsl"></a>自訂 DSL
 當您想要修改 DSL 定義時，請關閉實驗性實例，並更新主要 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 實例中的定義。

> [!NOTE]
> 修改 DSL 定義之後，您可能會遺失使用舊版所建立之測試模型中的資訊。  例如，偵錯工具包含名為 Sample 的檔案，其中包含一些圖形和連接器。 在您開始開發 DSL 定義之後，它們將不會顯示，而且當您儲存檔案時將會遺失。

 您可以為您的 DSL 建立各種延伸模組。 下列範例將為您提供可能的印象。

 在每次變更之後，請儲存 DSL 定義，按一下 [轉換**方案總管**中的**所有範本**]，然後按**F5**來試驗已變更的 DSL。

### <a name="rename-the-types-and-tools"></a>重新命名類型和工具
 重新命名現有的網域類別和關聯性。 例如，從最小語言範本建立的 Dsl 定義開始，您可以執行下列重新命名作業，讓 DSL 代表家族樹狀結構。

##### <a name="to-rename-domain-classes-relationships-and-tools"></a>若要重新命名網域類別、關聯性和工具

1. 在 Dsldefinition.dsl 檔圖中，將**examplemodel.store.customer**重新命名為**FamilyTreeModel**、 **ExampleElement**為**Person**、將**目標**設為**父代**，以及將**來源**設為**子**系。 您可以按一下每個標籤來變更它。

     ![DSL 定義圖表&#45;系列樹狀結構模型](../modeling/media/familyt-person.png "FamilyT_Person")

2. 重新命名元素和連接器工具。

    1. 按一下 [方案總管] 底下的索引標籤，以開啟 [DSL Explorer] 視窗。 如果您看不到它，請在 [ **View** ] 功能表上指向 [**其他視窗**]，然後按一下 [ **DSL Explorer**]。 只有當 DSL 定義圖表是使用中視窗時，才會顯示 [DSL Explorer]。

    2. 開啟屬性視窗並定位，讓您可以同時查看 [DSL Explorer] 和 [屬性]。

    3. 在 [DSL Explorer] 中，展開 [**編輯器** **]、[工具箱]** 索引標籤、 *\<DSL >* ，然後按 [**工具**]

    4. 按一下 [ **ExampleElement**]。 這是用來建立元素的 [工具箱] 專案。

    5. 在 屬性視窗中，將 **名稱** 屬性變更為**Person**。

         請注意， **Caption**屬性也會變更。

    6. 以同樣的方式，將**ExampleConnector**工具的名稱變更為**ParentLink**。 改變**Caption**屬性，使它不是 Name 屬性的複本。 例如，輸入**父系連結**。

3. 重建 DSL。

    1. 儲存 DSL 定義檔。

    2. 在方案總管的工具列中，按一下 [**轉換所有範本**]。

    3. 按 F5。 等到 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗實例出現為止。

4. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的實驗實例中的調試方案中，開啟測試模型檔案。 從 [工具箱] 將專案拖曳至其上。 請注意，[DSL Explorer] 中的工具標題和類型名稱已變更。

5. 儲存模型檔案。

6. 開啟 tt 檔案，並以新的名稱取代舊型別和屬性名稱的出現次數。

7. 請確定在 tt 檔案中指定的檔案名指定了您的測試模型。

8. 儲存 tt 檔案。 開啟產生的檔案，以查看在 tt 檔案中執行程式碼的結果。 請確認它是否正確。

### <a name="add-domain-properties-to-classes"></a>將網域屬性加入至類別
 將屬性加入至網域類別，例如代表個人的出生年份和死亡。

 若要讓新的屬性顯示在圖表上，您必須將*裝飾專案*加入至顯示模型專案的圖形中。 您也必須將屬性對應至裝飾專案。

##### <a name="to-add-properties-and-display-them"></a>新增屬性並加以顯示

1. 新增屬性。

   1. 在 DSL 定義圖中，以滑鼠右鍵按一下 [ **Person** ] 網域類別，指向 [**加入**]，然後按一下 [**網域屬性**]。

   2. 輸入新屬性名稱的清單，例如「**出生**」和「**死亡**」。 逐一按**enter**鍵。

2. 新增會在圖形中顯示內容的裝飾專案。

   1. 遵循從 Person 網域類別延伸到圖表另一端的灰色線條。 這是圖表元素對應。 它會將網域類別連結至 shape 類別。

   2. 以滑鼠右鍵按一下這個圖形類別，指向 [**加入**]，然後按一下 [**文字**裝飾專案]。

   3. 新增兩個名稱為**BirthDecorator**和**DeathDecorator**的裝飾專案。

   4. 選取每個新的裝飾專案，然後在 屬性視窗中設定 **位置** 欄位。 這會決定要在圖形上顯示網域屬性值的位置。 例如，設定**InnerBottomLeft**和**InnerBottomRight**。

        ![區間圖形定義](../modeling/media/familyt-compartment.png "FamilyT_Compartment")

3. 將裝飾專案對應至屬性。

   1. 開啟 [DSL 詳細資料] 視窗。 它通常會在 [輸出] 視窗旁的索引標籤中。 如果您看不到它，請在 [ **View** ] 功能表上指向 [**其他視窗**]，然後按一下 [ **DSL 詳細資料**]。

   2. 在 DSL 定義圖上，按一下將**Person**網域類別連接至 shape 類別的線條。

   3. 在 [ **DSL 詳細資料**] 的 [裝飾專案**對應**] 索引標籤上，按一下未對應之裝飾專案上的核取方塊。 在 [**顯示**內容] 中，選取您想要對應的網域屬性。 例如，將**BirthDecorator**對應到**出生**。

4. 儲存 DSL，按一下 [轉換所有範本]，然後按 F5。

5. 在範例模型圖中，確認您現在可以按一下所選擇的位置，並在其中輸入值。 此外，當您選取 [**人員**] 圖形時，屬性視窗會顯示新屬性 [出生] 和 [死亡]。

6. 在 tt 檔案中，您可以加入程式碼來取得每個人的屬性。

   ![系列樹圖表、工具箱和 explorer](../modeling/media/familyt-instance.png "FamilyT_Instance")

### <a name="define-new-classes"></a>定義新的類別
 您可以將網域類別和關聯性加入至模型。 例如，您可以建立新的類別來代表城鎮，並使用新的關聯性來表示居住在城鎮的人。

 若要讓模型圖表上的不同類型與眾不同，您可以將網域類別對應至不同類型的圖形，或對應至具有不同幾何和色彩的圖形。

##### <a name="to-add-and-display-a-new-domain-class"></a>加入和顯示新的網域類別

1. 新增網域類別，並將它設為模型根的子系。

    1. 在 DSL 定義圖中，按一下 [內嵌**關聯**性] 工具，按一下 [根類別] **FamilyTreeModel**，然後按一下圖表的空白部分。

         此時會出現新的網域類別，它會連接到具有內嵌關聯性的 FamilyTreeModel。

         設定其名稱，例如**城鎮**。

        > [!NOTE]
        > 除了模型的根以外，每個網域類別都必須是至少一個內嵌關聯性的目標，或者必須繼承自做為內嵌目標的類別。 基於這個理由，使用內嵌關聯性工具建立網域類別通常會很方便。

    2. 將網域屬性加入至新的類別，例如 [**名稱**]。

2. 新增 Person 和城鎮之間的參考關聯性。

    1. 按一下 [**參考關聯**性] 工具，按一下 [人員]，然後按一下 [城鎮]。

         ![DSL 定義片段：家族樹狀結構根目錄](../modeling/media/familyt-root.png "FamilyT_Root")

        > [!NOTE]
        > 參考關聯性代表從模型樹狀結構的某個部分到另一個部分的交互參考。

3. 在模型圖表上加入圖形以代表城鎮。

    1. 將 [ **Geometry] 圖形**從 [工具箱] 拖曳至圖表，然後將它重新命名，例如**TownShape**。

    2. 在 屬性視窗中，設定新圖形的外觀欄位，例如 填滿色彩 和 幾何。

    3. 新增裝飾專案以顯示城鎮的名稱，並將它重新命名為 NameDecorator。 設定其 Position 屬性。

4. 將城鎮網域類別對應至 TownShape。

    1. 按一下 [**圖表專案對應**] 工具，然後依序按一下 [城鎮] 領域類別和 [TownShape] 圖形類別。

    2. 在 [ **DSL 詳細資料**] 視窗的 [裝飾專案**對應**] 索引標籤中，選取地圖連接器，並核取 [NameDecorator]，並將 [**顯示內容**]

5. 建立連接器以顯示 Person 和城鎮之間的關聯性。

    1. 將連接器從 [工具箱] 拖曳至圖表。 將它重新命名，並設定其 [外觀] 屬性。

    2. 使用 [**圖表專案對應**] 工具，將新的連接器連結到 Person 和城鎮之間的關聯性。

         ![已加入圖形地圖的家族樹狀定義](../modeling/media/familyt-shapemap.png "FamilyT_ShapeMap")

6. 建立一個用於建立新城鎮的元素工具。

    1. 在**DSL Explorer**中，展開 [**編輯器** **] 和 [工具箱]** 索引標籤。

    2. 以滑鼠右鍵按一下 *\<您的 DSL >* 然後按一下 [**新增專案工具**]。

    3. 設定新工具的 [**名稱**] 屬性，並將其 [**類別**] 屬性設為 [城鎮]。

    4. 設定 [**工具箱] 圖示**屬性。 按一下 **[...]** ，然後在 [**檔案名**] 欄位中選取圖示檔。

7. 建立連接器工具來建立城鎮與人員之間的連結。

    1. 以滑鼠右鍵按一下 *\<您的 DSL >* 然後按一下 [新增**連接器工具**]。

    2. 設定新工具的 Name 屬性。

    3. 在 [ **ConnectionBuilder** ] 屬性中，選取包含人員城鎮關聯性名稱的產生器。

    4. 設定 [**工具箱] 圖示**。

8. 儲存 DSL 定義，按一下 [**轉換所有範本**]，然後按**F5**。

9. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的實驗實例中，開啟測試模型檔案。 使用新的工具來建立城鎮和城鎮和 person 之間的連結。 請注意，您只能在正確類型的元素之間建立連結。

10. 建立程式碼，以列出每個人居住的城市。 文字模板是您可以執行這類程式碼的其中一個地方。 例如，您可以修改偵錯工具中的現有 Sample.tt 檔，使其包含下列程式碼：

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

     當您儲存 * tt 檔案時，它會建立一個包含人員及其 residences 清單的子公司檔案。 如需詳細資訊，請參閱[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

## <a name="validation-and-commands"></a>驗證和命令
 您可以藉由加入驗證條件約束，進一步開發此 DSL。 這些條件約束是您可以定義的方法，確保模型處於正確的狀態。 例如，您可以定義一個條件約束，以確保子系的出生日期晚于其父系。 如果 DSL 使用者嘗試儲存會中斷任何條件約束的模型，驗證功能就會顯示警告。 如需詳細資訊，請參閱[使用特定領域語言進行驗證](../modeling/validation-in-a-domain-specific-language.md)。

 您也可以定義使用者可以叫用的功能表命令。 命令可以修改模型。 他們也可以在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 和外部資源中與其他模型互動。 如需詳細資訊，請參閱[如何：修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)。

## <a name="deploying-the-dsl"></a>部署 DSL
 若要讓其他使用者能夠使用特定領域語言，您可以散發 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組（VSIX）。 當您建立 DSL 方案時，會建立此元件。

 找出方案的 bin 資料夾中的 .vsix 檔案。 將它複製到您要安裝它的電腦上。 在該電腦上，按兩下 VSIX 檔案。 DSL 可以用於該電腦上的所有 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 實例。

 您可以使用相同的程式在自己的電腦上安裝 DSL，這樣就不需要使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的實驗實例。

 如需詳細資訊，請參閱[部署特定領域語言方案](../modeling/deploying-domain-specific-language-solutions.md)。

## <a name="Reset"></a>移除舊的實驗性 Dsl
 如果您已建立不再需要的實驗性 Dsl，可以藉由重設 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 實驗實例，將它們從電腦中移除。

 這會從您的電腦移除所有實驗性 Dsl 和其他實驗性 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組。 這些是在偵錯工具模式中執行的延伸模組。

 此程式不會移除已透過執行 VSIX 檔案完整安裝的 Dsl 或其他 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組。

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>若要重設 Visual Studio 實驗實例

1. 請依序按一下 [開始]、[所有程式]、[Microsoft Visual Studio 2010 SDK]、[工具]，然後按一下 [重設 Microsoft Visual Studio 2010 Experimental 執行個體]。

2. 重建您仍想要使用的任何實驗性 Dsl 或其他實驗性 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組。

## <a name="see-also"></a>另請參閱
 [瞭解模型、類別和關聯](../modeling/understanding-models-classes-and-relationships.md)性[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md) [Visualizaton 和模型化 SDK](https://go.microsoft.com/fwlink/?LinkID=186128)
