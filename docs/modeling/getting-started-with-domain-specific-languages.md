---
title: 開始使用網域指定的語言
description: 瞭解定義和使用特定領域語言的基本概念 (DSL) 建立 Visual Studio 的模型 SDK。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eaab198edae66fc334e854ae1f47dae313dce76b
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363480"
---
# <a name="get-started-with-domain-specific-languages"></a>特定領域語言的使用者入門

本主題說明定義和使用特定領域語言的基本概念 (DSL) 建立 Visual Studio 的模型 SDK。

> [!NOTE]
> 當您安裝 Visual Studio 的特定功能時，會自動安裝文字模板轉換 SDK 和 Visual Studio 模型 SDK。 如需詳細資訊，請參閱[此部落格文章](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)。

如果您不熟悉 Dsl，建議您逐步執行 **DSL 工具實驗室**，您可以在此網站中找到： [視覺化和模型 SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>您可以使用 Domain-Specific 語言來做什麼？

特定領域語言是一種標記法，通常是圖形化的，其設計目的是要用於特定用途。 相較之下，UML 等語言是一般用途。 在 DSL 中，您可以定義模型專案和其關聯性的類型，以及它們在螢幕上的呈現方式。

當您設計 DSL 之後，您可以將它發佈為 Visual Studio 整合擴充功能 (VSIX) 封裝的一部分。 使用者可以使用 Visual Studio 中的 DSL：

![家譜圖表、工具箱和總管](../modeling/media/familyt_instance.png)

標記法只是 DSL 的一部分。 除了標記法之外，您的 VSIX 套件還包含使用者可套用的工具，可協助他們從模型編輯和產生材質。

Dsl 的其中一個主要應用程式是產生程式碼、設定檔及其他成品。 尤其是在大型專案和產品線中，將會建立產品的數個變體，從 Dsl 產生許多變化層面，可大幅提升可靠性和需求變更的快速回應。

本總覽的其餘部分是逐步解說，介紹在 Visual Studio 中建立和使用特定領域語言的基本作業。

## <a name="prerequisites"></a>Prerequisites

若要定義 DSL，您必須已安裝下列元件：

| 元件 | 連結 |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Visual Studio 的模型化 SDK | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>建立 DSL 解決方案

若要建立新的特定領域語言，您可以使用 Domain-Specific 語言專案範本來建立新的 Visual Studio 方案。

1. 在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。

2. 在 [ **專案類型**] 底下，展開 [ **其他專案類型** ] 節點， **然後按一下 [** 擴充性]。

3. 按一下 [ **特定領域語言設計工具**]。

     ![[建立 DSL] 對話方塊](../modeling/media/create_dsldialog.png)

4. 在 [ **名稱** ] 方塊中，輸入 **FamilyTree**。 按一下 [確定]。

     **網域指定的語言嚮導** 隨即開啟，並顯示範本 DSL 解決方案的清單。

     按一下每個範本以查看描述。

     範本是很有用的起點。 其中每個都提供完整的工作 DSL，您可以根據自己的需求進行編輯。 一般來說，您會選擇最接近您要建立之範本的範本。

5. 針對此逐步解說，請選擇 **最基本的語言** 範本。

6. 在適當的精靈頁面中輸入 DSL 的副檔名。 這是包含 DSL 將使用之執行個體的檔案的副檔名。

    - 選擇與您的電腦中的任何應用程式或您要安裝 DSL 的任何電腦沒有關聯的延伸模組。 例如， **.docx** 和 **htm** 會是無法接受的副檔名。

    - 如果您已輸入的副檔名正用來做為 DSL，精靈將會警告您。 請考慮使用不同的副檔名。 您也可以重設 Visual Studio SDK Experimental 執行個體以清除舊的實驗設計工具。 按一下 [ **開始**]，按一下 [ **所有程式**]， **Microsoft Visual Studio 2010 SDK**，[ **工具**]，然後 **重設 Microsoft Visual Studio 2010 實驗實例**。

7. 檢查其他頁面，然後按一下 **[完成]**。

     產生包含兩個專案的方案。 它們的名稱是 Dsl 和 DslPackage。 會開啟名為 Dsldefinition.dsl 檔的圖表檔案。

    > [!NOTE]
    > 您可以在這兩個專案的資料夾中看到的大部分程式碼都是從 Dsldefinition.dsl 檔產生。 基於這個理由，對您的 DSL 進行大部分的修改都是在這個檔案中進行。

這時使用者介面類似以下圖片。

![dsl 設計工具](../modeling/media/dsl_designer.png)

此方案定義網域指定的語言。 如需詳細資訊，請參閱 [Domain-Specific 語言工具消費者介面的總覽](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md)。

## <a name="the-important-parts-of-the-dsl-solution"></a>DSL 解決方案的重要部分

請注意新解決方案的下列層面：

- **Dsl\DslDefinition.dsl** 這是您建立 DSL 解決方案時所看到的檔案。 方案中幾乎所有的程式碼都是從這個檔案產生，而您對 DSL 定義所做的大部分變更都是在這裡進行。 如需詳細資訊，請參閱使用與 [DSL 定義圖表](../modeling/working-with-the-dsl-definition-diagram.md)。

- **Dsl 專案** 此專案包含的程式碼會定義網域指定的語言。

- **DslPackage 專案** 此專案包含的程式碼可讓您在 Visual Studio 中開啟和編輯 DSL 的實例。

## <a name="running-the-dsl"></a><a name="Debugging"></a> 執行 DSL

您可以在建立 DSL 解決方案之後立即執行。 稍後，您可以逐漸修改 DSL 定義，然後在每次變更之後再次執行解決方案。

### <a name="to-experiment-with-the-dsl"></a>若要試驗 DSL

1. 在 **方案總管** 工具列中，按一下 [**轉換所有範本**]。 這會從 Dsldefinition.dsl 檔重新產生大部分的原始程式碼。

    > [!NOTE]
    > 每當您變更 *dsldefinition.dsl 檔* 時，您必須先按一下 [ **轉換所有範本** ]，然後再重建解決方案。 您可以自動化此步驟。 如需詳細資訊，請參閱 [如何自動轉換所有範本](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\))。

2. 按 **F5**，或在 [偵錯]  功能表上，按一下 [開始偵錯] 。

     DSL 會建立並安裝在 Visual Studio 的實驗實例中。

     Visual Studio 的實驗實例隨即啟動。 實驗性實例會從登錄的個別子樹取得其設定，其中 Visual Studio 的擴充功能會針對偵錯工具進行註冊。 Visual Studio 的一般實例無法存取在該處註冊的擴充功能。

3. 在 Visual Studio 的實驗實例中，從 **方案總管** 開啟名為 **Test** 的模型檔案。

     \- 或 -

     以滑鼠右鍵按一下 [調試] 專案，指向 [ **加入**]，然後按一下 [ **專案**]。 在 [ **新增專案** ] 對話方塊中，選取 DSL 的檔案類型。

     模型檔案會以空白圖表的形式開啟。

     [工具箱] 隨即開啟，並顯示適用于圖表類型的工具。

4. 使用這些工具，在圖表上建立圖形和連接器。

    1. 若要建立圖形，請從範例圖形工具拖曳至圖表上。

    2. 若要連接兩個圖形，請按一下 [範例連接器] 工具，再按一下第一個圖形，然後按一下第二個圖形。

5. 按一下圖形的標籤來變更它們。

您的實驗 Visual Studio 會類似下列範例：

![Visual Studio 中的網域特定語言範例樹狀結構](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>模型的內容

作為 DSL 實例之檔案的內容稱為 *模型*。 此模型包含元素之間的 *模型*<em>專案和</em>*連結*。 DSL 定義會指定模型中可存在的模型專案和連結類型。 例如，在以最基礎語言範本建立的 DSL 中，有一種類型的模型專案，以及一種類型的連結。

DSL 定義可以指定如何在圖表上顯示模型。 您可以從各種不同的圖形和連接器樣式中選擇。 您可以指定某些圖形出現在其他圖形內。

當您編輯模型時，可以在 **瀏覽器** 視圖中將模型視為樹狀結構。 當您在圖表中加入圖形時，模型專案也會出現在 [explorer] 中。 即使沒有圖表，也可以使用 explorer。

如果您無法在 Visual Studio 的偵錯工具實例中看到 Explorer，請在 [ **視圖** ] 功能表上指向 [ **其他視窗**]，然後按一下 [ *\<Your Language>* **Explorer**]。

### <a name="the-api-of-your-dsl"></a>DSL 的 API

您的 DSL 會產生可讓您讀取和更新屬於 DSL 實例之模型的 API。 API 的其中一個應用程式是從模型產生文字檔。 如需詳細資訊，請參閱 [使用 T4 文字模板的設計階段程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。

在調試方案中，開啟副檔名為 "tt" 的範本檔案。 這些範例會示範如何從模型產生文字，並可讓您測試 DSL 的 API。 其中一個範例是寫入中 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ，另一個則是 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 。

在每個範本檔案下都是它所產生的檔案。 展開方案總管中的範本檔案，然後開啟產生的檔案。

範本檔案包含一小段程式碼，其中會列出模型中的所有元素。

產生的檔案包含結果。

當您變更模型檔案時，在重新產生檔案之後，您會看到產生的檔案中有對應的變更。

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>變更模型檔案之後重新產生文字檔

1. 在 Visual Studio 的實驗實例中，儲存模型檔案。

2. 請確定每個 tt 檔中的檔案名參數都參考您用於實驗的模型檔案。 儲存 tt 檔。

3. 在 **方案總管** 的工具列中，按一下 [**轉換所有範本**]。

     \- 或 -

     以滑鼠右鍵按一下您要重新產生的範本，然後按一下 [ **執行自訂工具**]。

您可以將任何數目的文字模板檔案新增至專案。 每個範本都會產生一個結果檔。

> [!NOTE]
> 當您變更 DSL 定義時，範例文字模板程式碼將無法運作，除非您加以更新。

如需詳細資訊，請參閱 [從 Domain-Specific 語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md) ，以及 [撰寫程式碼以自訂 Domain-Specific 語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)。

## <a name="customizing-the-dsl"></a>自訂 DSL

當您想要修改 DSL 定義時，請關閉實驗實例，並更新主要 Visual Studio 實例中的定義。

> [!NOTE]
> 修改 DSL 定義之後，您可能會遺失使用舊版所建立之測試模型中的資訊。  例如，偵錯工具方案包含名為 Sample 的檔案，其中包含一些圖形和連接器。 在您開始開發 DSL 定義之後，將不會看到它們，而且在您儲存檔案時將會遺失。

您可以對 DSL 進行各種擴充。 下列範例將為您提供可能的印象。

在每次變更之後，儲存 DSL 定義，按一下 [ **轉換所有範本** ] **方案總管**，然後按下 **F5** 以進行變更的 DSL。

### <a name="rename-the-types-and-tools"></a>重新命名類型和工具

重新命名現有的網域類別和關聯性。 例如，從最基礎語言範本建立的 Dsl 定義開始，您可以執行下列重新命名作業，使 DSL 代表家族樹狀結構。

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>若要重新命名網域類別、關聯性和工具

1. 在 Dsldefinition.dsl 檔圖中，將 **examplemodel.store.customer** 重新命名為 **FamilyTreeModel**、 **ExampleElement** 為 **Person**、將 **目標** 設為 **父代**，並將 **來源** 重新命名為 **子** 系。 您可以按一下每個標籤來變更它。

     ![DSL 定義圖 &#45; 系列樹狀結構模型](../modeling/media/familyt_person.png)

2. 重新命名元素和連接器工具。

    1. 按一下 [方案總管] 下方的索引標籤，以開啟 [DSL Explorer] 視窗。 如果您看不到它，請在 [ **View** ] 功能表上指向 [ **其他視窗** ]，然後按一下 [ **DSL Explorer**]。 只有當 DSL 定義圖表是使用中視窗時，才會顯示 DSL Explorer。

    2. 開啟屬性視窗並定位，讓您可以同時查看 DSL Explorer 和屬性。

    3. 在 [DSL Explorer] 中，依序展開 [**編輯器** **]、[工具箱]** 索引標籤、 *\<your DSL>* 和 **工具**

    4. 按一下 [ **ExampleElement**]。 這是用來建立元素的 [工具箱] 專案。

    5. 在屬性視窗中，將 [ **名稱** ] 屬性變更為 **Person**。

         請注意， **Caption** 屬性也會變更。

    6. 以同樣的方式，將 **ExampleConnector** 工具的名稱變更為 **ParentLink**。 改變 **Caption** 屬性，使它不是 Name 屬性的複本。 例如，請輸入 **父連結**。

3. 重建 DSL。

    1. 儲存 DSL 定義檔。

    2. 在方案總管的工具列中，按一下 [ **轉換所有範本** ]。

    3. 按 F5。 等到 Visual Studio 的實驗實例出現為止。

4. 在 Visual Studio 實驗實例的偵錯工具中，開啟測試模型檔案。 從 [工具箱] 將專案拖曳至其上。 請注意，[DSL Explorer] 中的工具字幕和類型名稱已變更。

5. 儲存模型檔案。

6. 開啟一個 tt 檔，並以新名稱取代舊型別和屬性名稱的出現。

7. 請確定在 tt 檔案中指定的檔案名指定了您的測試模型。

8. 儲存 tt 檔。 開啟產生的檔案，以查看在 tt 檔案中執行程式碼的結果。 確認它是正確的。

### <a name="add-domain-properties-to-classes"></a>將網域屬性加入至類別
 將屬性新增至網域類別，例如，代表人員的出生年份和死亡。

 若要在圖表上顯示新屬性，您必須將 *裝飾專案* 新增至顯示模型專案的圖形。 您也必須將屬性對應至裝飾專案。

##### <a name="to-add-properties-and-display-them"></a>若要加入並顯示內容

1. 加入屬性。

   1. 在 DSL 定義圖中，以滑鼠右鍵按一下 **Person** 網域類別，指向 [ **加入**]，然後按一下 [ **網域屬性**]。

   2. 輸入新屬性名稱的清單，例如「 **出生** 」和「 **死亡**」。 在每一個之後按 **enter** 鍵。

2. 加入將在圖形中顯示內容的裝飾專案。

   1. 遵循從 Person 網域類別延伸至圖表另一端的灰色線。 這是圖表元素對應。 它會將網域類別連結至 shape 類別。

   2. 以滑鼠右鍵按一下這個圖形類別，指向 [ **加入**]，然後按一下 [ **文字** 裝飾專案]。

   3. 新增具有名稱的兩個裝飾專案，例如 **BirthDecorator** 和 **DeathDecorator**。

   4. 選取每個新的裝飾專案，然後在屬性視窗中設定 [ **位置** ] 欄位。 這會決定要在圖形上顯示網域屬性值的位置。 例如，設定 **InnerBottomLeft** 和 **InnerBottomRight**。

        ![區間圖案定義](../modeling/media/familyt_compartment.png)

3. 將裝飾專案對應至屬性。

   1. 開啟 [DSL 詳細資料] 視窗。 它通常會在 [輸出] 視窗旁的索引標籤中。 如果您看不到它，請在 [ **View** ] 功能表上指向 [ **其他視窗**]，然後按一下 [ **DSL 詳細資料**]。

   2. 在 DSL 定義圖上，按一下將 **Person** 網域類別連接到 shape 類別的程式程式碼。

   3. 在 [ **DSL 詳細資料**] 的 [裝飾專案 **對應** ] 索引標籤上，按一下未對應之裝飾專案的核取方塊。 在 [ **顯示內容**] 中，選取您要對應的網域屬性。 例如，將 **BirthDecorator** 對應到 **出生**。

4. 儲存 DSL，按一下 [轉換所有範本]，然後按下 F5。

5. 在範例模型圖中，確認您現在可以按一下您選擇的位置，然後在其中輸入值。 此外，當您選取 [ **人員** ] 圖形時，屬性視窗會顯示新的屬性出生和死亡。

6. 在 tt 檔案中，您可以加入程式碼來取得每個人員的屬性。

   ![家譜圖表、工具箱和總管](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>定義新的類別
 您可以將網域類別和關聯性加入至模型。 例如，您可以建立新的類別來代表城鎮，並建立新的關聯性，以表示居住在城鎮的人員。

 若要在模型圖表上使不同的類型不同，您可以將網域類別對應至不同類型的圖形，或對應至具有不同幾何和色彩的圖形。

##### <a name="to-add-and-display-a-new-domain-class"></a>若要加入並顯示新的網域類別

1. 新增網域類別，並將它設為模型根的子系。

    1. 在 DSL 定義圖中，按一下 [內嵌 **關聯** 性] 工具，按一下根類別 **FamilyTreeModel**，然後按一下圖表的空白部分。

         新的網域類別隨即出現，並以內嵌關聯性連接到 FamilyTreeModel。

         設定其名稱，例如 **城鎮**。

        > [!NOTE]
        > 除了模型的根目錄之外，每個網域類別都必須是至少一個內嵌關聯性的目標，或者必須繼承自內嵌的目標類別。 基於這個理由，使用 [內嵌關聯性] 工具來建立網域類別通常很方便。

    2. 將網域屬性加入至新的類別，例如 [ **名稱**]。

2. 新增 Person 和城鎮之間的參考關聯性。

    1. 按一下 [ **參考關聯** 性] 工具，再按一下 [人員]，然後按一下 [城鎮]。

         ![DSL 定義片段：家譜根部](../modeling/media/familyt_root.png)

        > [!NOTE]
        > 參考關聯性代表從模型樹狀結構的一個部分到另一個部分的交互參考。

3. 加入圖形以代表模型圖上的城鎮。

    1. 將 **幾何圖形** 從 [工具箱] 拖曳至圖表，然後將它重新命名，例如 **TownShape**。

    2. 在 [屬性視窗] 中，設定新圖形的外觀欄位，例如 [填滿色彩] 和 [幾何]。

    3. 新增裝飾專案以顯示城鎮的名稱，並將它重新命名為 NameDecorator。 設定其位置屬性。

4. 將城鎮網域類別對應至 TownShape。

    1. 按一下 [ **圖表專案對應** ] 工具，然後按一下 [城鎮網域] 類別，然後按一下 [TownShape] 圖形類別。

    2. 在已選取地圖連接器的 [ **DSL 詳細資料**] 視窗的 [裝飾專案 **對應**] 索引標籤中，核取 [NameDecorator]，並將 [**顯示] 屬性**

5. 建立連接器以顯示 Person 與城鎮之間的關聯性。

    1. 將連接器從 [工具箱] 拖曳至圖表。 將它重新命名，並設定其外觀屬性。

    2. 使用 [ **圖表專案對應** ] 工具，將新的連接器連結到 Person 和城鎮之間的關聯性。

         ![已加入圖案對應的家譜定義](../modeling/media/familyt_shapemap.png)

6. 建立用來建立新城鎮的元素工具。

    1. 在 [ **DSL Explorer**] 中，展開 [ **編輯器** **]** 索引標籤。

    2. 以滑鼠右鍵按一下 *\<your DSL>* ，然後按一下 [ **加入新專案工具**]。

    3. 設定新工具的 [ **名稱** ] 屬性，並將其 [ **類別** ] 屬性設定為 [城鎮]。

    4. 設定 [ **工具箱] 圖示** 屬性。 按一下 **[...]** ，然後在 [ **檔案名** ] 欄位中選取圖示檔。

7. 建立連接器工具，以在城鎮和人員之間建立連結。

    1. 以滑鼠右鍵按一下 *\<your DSL>* ，然後按一下 [ **加入新的連接器工具**]。

    2. 設定新工具的 [名稱] 屬性。

    3. 在 [ **ConnectionBuilder** ] 屬性中，選取包含 Person-Town 關聯性名稱的 builder。

    4. 設定 [ **工具箱] 圖示**。

8. 儲存 DSL 定義，按一下 [ **轉換所有範本**]，然後按下 **F5**。

9. 在 Visual Studio 的實驗實例中，開啟測試模型檔案。 使用新工具來建立城鎮和 person 之間的城鎮和連結。 請注意，您只能在正確類型的元素之間建立連結。

10. 建立程式碼，以列出每個人居住的城市。 文字模板是您可以執行這類程式碼的其中一個位置。 例如，您可以在偵錯工具中修改現有的 Sample.tt 檔案，使其包含下列程式碼：

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

     當您儲存 * tt 檔案時，它會建立一個附屬檔案，其中包含人員及其 residences 的清單。 如需詳細資訊，請參閱 [從 Domain-Specific 語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

## <a name="validation-and-commands"></a>驗證和命令
 您可以藉由新增驗證條件約束來進一步開發此 DSL。 這些條件約束是您可以定義的方法，可確保模型處於正確的狀態。 例如，您可以定義條件約束，以確定子女的出生日期晚于其父代的出生日期。 如果 DSL 使用者嘗試儲存會中斷任何條件約束的模型，驗證功能就會顯示警告。 如需詳細資訊，請參閱 [以 Domain-Specific 語言進行驗證](../modeling/validation-in-a-domain-specific-language.md)。

 您也可以定義使用者可以叫用的功能表命令。 命令可以修改模型。 它們也可以與 Visual Studio 和外部資源的其他模型互動。 如需詳細資訊，請參閱 [如何：修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)。

## <a name="deploying-the-dsl"></a>部署 DSL
 若要讓其他使用者能夠使用特定領域語言，請 (VSIX) 檔散發 Visual Studio 擴充功能。 這是在您建立 DSL 解決方案時所建立的。

 在解決方案的 bin 資料夾中找出 .vsix 檔案。 將它複製到您要安裝它的電腦上。 在該電腦上，按兩下 VSIX 檔案。 DSL 可用於該電腦上 Visual Studio 的所有實例。

 您可以使用相同的程式在自己的電腦上安裝 DSL，如此就不需要使用 Visual Studio 的實驗實例。

 如需詳細資訊，請參閱[部署特定領域語言方案](msi-and-vsix-deployment-of-a-dsl.md)。

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> 移除舊的實驗性 Dsl
 如果您已建立不再需要的實驗性 Dsl，您可以藉由重設 Visual Studio 的實驗性實例，從電腦移除它們。

 這會從您的電腦移除所有實驗性 Dsl 和其他實驗性 Visual Studio 延伸模組。 這些是在偵測模式中執行的延伸模組。

 此程式不會移除已透過執行 VSIX 檔案完整安裝的 Dsl 或其他 Visual Studio 延伸模組。

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>若要重設 Visual Studio 的實驗性實例

1. 按一下 [ **開始**]，按一下 [ **所有程式**]， **Microsoft Visual Studio 2010 SDK**，[ **工具**]，然後 **重設 Microsoft Visual Studio 2010 實驗實例**。

2. 重建任何您仍要使用的實驗性 Dsl 或其他實驗性 Visual Studio 延伸模組。

## <a name="see-also"></a>請參閱

- [了解模型、類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)
- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
