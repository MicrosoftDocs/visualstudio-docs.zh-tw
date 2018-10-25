---
title: 開始使用特定領域語言 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 29699609ee095c7e95434492afc531869453da4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877762"
---
# <a name="getting-started-with-domain-specific-languages"></a>開始使用網域指定的語言
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題說明在定義和使用適用於 Visual Studio 中使用 Modeling SDK 建立特定領域語言 (DSL) 的基本概念。  
  
 如果您不熟悉 dsl，建議您逐步**DSL 工具實驗室**，您可以找到此站台中： [Visualizaton and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
## <a name="what-can-you-do-with-a-domain-specific-language"></a>您可以使用特定領域語言來做什麼？  
 使用標記法，通常是圖形，是設計用來針對特定用途使用定義域專屬語言。 相較之下，例如 UML 的語言是一般用途。 在 DSL 中，您可以定義類型的模型項目和其關聯性，以及在螢幕上的呈現方式。  
  
 當您設計 DSL 時，您可以將它當做 Visual Studio 整合擴充功能 (VSIX) 封裝的一部分散發。 使用者在使用中的 DSL [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
 ![家譜圖表、 工具箱和總管](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
 標記法只是一部分的 DSL。 以及標記法中，您的 VSIX 套件會包含使用者可以套用，幫助他們編輯，並從他們的模型產生資料的工具。  
  
 其中一個 Dsl 的主體的應用程式會產生程式碼、 組態檔和其他成品。 尤其是在大型專案 」 和 「 產品線，其中將建立數個變化的產品，從 Dsl 中產生許多變動層面可以提供大幅增加可靠性和非常快速的回應需求變更。  
  
 本概觀的其餘部分會介紹建立和使用中的定義域專屬語言的基本操作的逐步解說[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
 若要定義 DSL，您必須已安裝下列元件：  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Modeling SDK for Visual Studio|[下載 MSDK](http://www.microsoft.com/download/details.aspx?id=40754)|  
  
## <a name="creating-a-dsl-solution"></a>建立 DSL 方案  
 若要建立新的定義域專屬語言，您建立新[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]使用定義域專屬語言專案範本的方案。  
  
#### <a name="to-create-a-dsl-solution"></a>建立 DSL 方案  
  
1. 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
2. 底下**專案類型**，展開**其他專案類型**節點，然後按一下**擴充性**。  
  
3. 按一下  **Domain-specific Language Designer**。  
  
    ![建立 DSL 對話方塊](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
4. 在 **名稱**方塊中，輸入**列舉 FamilyTree**。 按一下 [確定 **Deploying Office Solutions**]。  
  
    **定義域專屬語言精靈**隨即開啟，並顯示範本 DSL 方案清單。  
  
    按一下以查看描述，每個範本  
  
    此範本是很有用起始點。 每個提供完整運作的 DSL，您可以編輯以符合您的需求。 一般情況下，您會選擇最接近您要建立範本。  
  
5. 此逐步解說中，選擇**最小語言**範本。  
  
6. 在適當的精靈頁面中輸入 DSL 的副檔名。 這是包含 DSL 將使用之執行個體的檔案的副檔名。  
  
   -   選擇不在您的電腦，或您要安裝 DSL 的任何電腦中的任何應用程式相關聯的擴充功能。 例如， **docx**並**htm**是無法接受的檔案名稱副檔名。  
  
   -   如果您已輸入的副檔名正用來做為 DSL，精靈將會警告您。 請考慮使用不同的副檔名。 您也可以重設 Visual Studio SDK Experimental 執行個體以清除舊的實驗設計工具。 按一下 **開始**，按一下**所有程式**， **Microsoft Visual Studio 2010 SDK**，**工具**，然後**重設 MicrosoftVisual Studio 2010 實驗執行個體**。  
  
7. 檢查其他頁面，然後按一下 **完成**。  
  
    產生的方案包含兩個專案。 它們會命名為 Dsl 和 DslPackage。 圖表檔，也就是開啟具名的 DslDefinition.dsl。  
  
   > [!NOTE]
   >  大部分的程式碼，您可以看到兩個專案中的資料夾中會產生從 DslDefinition.dsl。 基於這個理由，大部分您的 dsl 修改此檔案中。  
  
   這時使用者介面類似以下圖片。  
  
   ![dsl 設計工具](../modeling/media/dsl-designer.png "dsl_designer")  
  
   此方案定義網域指定的語言。 如需詳細資訊，請參閱 < [Domain-specific Language Tools 使用者介面概觀](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md)。  
  
## <a name="the-important-parts-of-the-dsl-solution"></a>DSL 方案的重要部分  
 請注意新的方案的下列層面。  
  
-   **Dsl\DslDefinition.dsl**這是您會看到當您建立 DSL 方案的檔案。 在方案中的幾乎所有程式碼會產生這個檔案中，從與此處所做的大部分變更，您對 DSL 定義。 如需詳細資訊，請參閱 < 使用[使用 DSL 定義圖表](../modeling/working-with-the-dsl-definition-diagram.md)。  
  
-   **Dsl 專案**此專案包含會定義特定領域語言的程式碼。  
  
-   **在 DslPackage 專案**此專案包含允許開啟及編輯在 DSL 的執行個體的程式碼[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
##  <a name="Debugging"></a> 執行 DSL  
 一旦您已建立它，您可以執行 DSL 方案。 稍後，您可以修改 DSL 定義中逐漸，在每次變更之後，再次執行解決方案。  
  
#### <a name="to-experiment-with-the-dsl"></a>若要試驗 DSL  
  
1. 按一下 **轉換所有範本**在 方案總管 工具列中。 這樣會重新產生大部分的 DslDefinition.dsl 中的原始程式碼。  
  
   > [!NOTE]
   >  每當您變更 DslDefinition.dsl 時，您必須按一下 **轉換所有範本**重新建置方案之前。 您可以自動化此步驟。 如需詳細資訊，請參閱 <<c0> [ 如何自動執行轉換的所有範本](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a)。  
  
2. 按 f5 鍵，或在**偵錯**功能表上，按一下**開始偵錯**。  
  
    建置 DSL，並已安裝在實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗執行個體隨即啟動。 實驗執行個體需要個別的子樹的登錄中，從其設定位置[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]延伸模組已註冊要進行偵錯之用。 一般的執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]不能那里註冊擴充功能的存取。  
  
3. 在實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，開啟名為模型檔案**測試**從**方案總管 中**。  
  
    \-或-  
  
    以滑鼠右鍵按一下 偵錯專案，指向**新增**，然後按一下**項目**。 在 **加入項目**對話方塊方塊中，選取檔案類型的 DSL。  
  
    模型檔案開啟為空白的圖表。  
  
    工具箱 中開啟，並顯示適用於圖表類型的工具。  
  
4. 使用工具來建立圖形和連接器，在圖表上。  
  
   1.  若要建立圖形，請從範例圖形工具拖曳至圖表拖曳。  
  
   2.  若要連接兩個圖形，按一下 範例連接器工具、 按一下第一個圖形，，然後按一下第二個圖形。  
  
5. 按一下 變更形狀的標籤。  
  
   您的實驗性[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]將類似下列的範例：  
  
   ![](../modeling/media/dsl-min.png "DSL_min")  
  
### <a name="the-content-of-a-model"></a>模型的內容  
 DSL 的執行個體檔案的內容會呼叫*模型*。 模型包含*模型項目*並*連結*項目之間。 DSL 定義中指定的模型項目類型，可以存在於模型中的連結。 例如，在最小語言範本所建立的 DSL 中，沒有一種類型的模型項目和一種類型的連結。  
  
 DSL 定義中可以指定在模型圖上的顯示方式。 您可以選擇各種圖案和接點的樣式。 您可以指定某些圖形出現在其他圖形。  
  
 您可以在樹狀結構檢視模型**總管**檢視編輯模型時。 將圖形新增至圖表時，模型項目也會出現在 [總管] 中。 可以使用 [總管] 中，即使沒有任何圖表。  
  
 如果您無法看到 [總管] 中的偵錯的執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，請在**檢視**功能表中的指向**其他 Windows**，然後按一下*\<您的語言 >***總管**。  
  
### <a name="the-api-of-your-dsl"></a>您的 DSL 的 API  
 您的 DSL 會產生一個 API，讓您讀取和更新模型的 DSL 執行個體。 一個應用程式的 api 是從模型產生文字檔案。 如需詳細資訊，請參閱 <<c0> [ 使用 T4 文字範本在設計階段的程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
 在偵錯方案中，開啟範本檔案以副檔名".tt 」。 這些範例示範如何從模型中，產生的文字，並讓您測試您的 DSL 的 API。 其中一個範例以[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]，則在其他[!INCLUDE[csprcs](../includes/csprcs-md.md)]。  
  
 在每個範本檔案會是它會產生的檔案。 展開 [方案總管] 中的範本檔案，開啟產生的檔案。  
  
 範本檔案會包含在模型中的所有項目列出的程式碼的簡短區段。  
  
 產生的檔案包含的結果。  
  
 當您變更模型檔案時，您會看到產生的檔案中的對應變更之後重新產生的檔案。  
  
##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>若要重新產生文字檔案之後變更的模型檔案  
  
1. 在實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，儲存模型檔案。  
  
2. 請確定檔案名稱參數，每個.tt 檔案中的是指您要用於實驗的模型檔案。 儲存.tt 檔案。  
  
3. 按一下 [**轉換所有範本**中的工具列**方案總管] 中**。  
  
    \-或-  
  
    以滑鼠右鍵按一下您想要重新產生，然後按一下 範本**執行自訂工具**。  
  
   您可以將任意數目的文字範本檔案新增至專案。 每個範本會產生一個結果檔案。  
  
> [!NOTE]
>  當您變更 DSL 定義中時，範例文字範本程式碼將無法運作，除非您更新它。  
  
 如需詳細資訊，請參閱 <<c0> [ 特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)並[來自訂特定領域語言撰寫的程式碼](../modeling/writing-code-to-customise-a-domain-specific-language.md)。  
  
## <a name="customizing-the-dsl"></a>自訂 DSL  
 當您想要修改 DSL 定義中時，關閉實驗執行個體，並更新主要定義[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]執行個體。  
  
> [!NOTE]
>  您已修改 DSL 定義之後，您可能會遺失您已使用舊版建立的測試模型中的資訊。  例如，偵錯方案包含名為範例，其中包含一些圖形和連接器的檔案。 開始開發您的 DSL 定義之後，將不會顯示，以及它們時將會遺失您儲存檔案。  
  
 您可以將各種不同的擴充功能對您的 DSL。 下列範例可讓您印象的可能性。  
  
 每項變更之後，儲存 DSL 定義中，按一下**轉換所有範本**中**方案總管**，然後按**F5**試驗變更 DSL。  
  
### <a name="rename-the-types-and-tools"></a>重新命名類型和工具  
 重新命名現有的網域類別和關聯性。 例如，從最小語言範本所建立的 Dsl 定義開始，您就可以執行下列重新命名作業，才能在代表家庭樹狀結構的 DSL。  
  
##### <a name="to-rename-domain-classes-relationships-and-tools"></a>若要重新命名網域類別、 關聯性和工具  
  
1.  在 DslDefinition 圖表中，重新命名**ExampleModel**要**FamilyTreeModel**， **ExampleElement**至**人員**， **目標**要**父系**，以及**來源**來**子系**。 您可以按一下要變更它的每個標籤。  
  
     ![DSL 定義圖&#45;家譜模型](../modeling/media/familyt-person.png "FamilyT_Person")  
  
2.  重新命名的項目和連接器工具。  
  
    1.  按一下 [方案總管] 的索引標籤中開啟 [DSL 總管] 視窗。 如果您看，在**檢視**功能表中的指向**其他 Windows** ，然後按一下 [ **DSL explorer]**。 DSL 總管 DSL 定義圖是使用中視窗時，才是可見。  
  
    2.  開啟 [屬性] 視窗和它定位好，您可以看到 [DSL 總管] 和屬性在相同的時間。  
  
    3.  在 [DSL 總管] 中，展開**編輯器**，**工具箱索引標籤**，  *\<DSL >*，然後**工具**。  
  
    4.  按一下  **ExampleElement**。 這是用來建立元素的工具箱項目。  
  
    5.  在 [屬性] 視窗中，變更**名稱**屬性設**人員**。  
  
         請注意，**標題**屬性也會變更。  
  
    6.  同樣地，在變更名稱**ExampleConnector**工具**ParentLink**。 Alter**標題**屬性，因此它不是一份名稱屬性。 例如，輸入**父連結**。  
  
3.  重建 DSL。  
  
    1.  將 DSL 定義檔案。  
  
    2.  按一下 [**轉換所有範本**在方案總管] 的工具列  
  
    3.  按 F5。 等到實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]隨即出現。  
  
4.  偵錯方案中的實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，開啟測試模型檔案。 從工具箱拖曳至其本身的項目。 請注意，已變更的工具標題和 DSL 總管 中的型別名稱。  
  
5.  儲存模型檔案。  
  
6.  開啟.tt 檔案，並以新的名稱取代舊的型別和屬性名稱。  
  
7.  請確定.tt 檔案中指定的檔案名稱指定測試模型。  
  
8.  儲存.tt 檔案。 開啟產生的檔案，請參閱.tt 檔案中執行的程式碼的結果。 請確認它正確。  
  
### <a name="add-domain-properties-to-classes"></a>將網域屬性加入類別  
 將屬性加入網域類別，例如若要表示的出生年份和死亡的人員。  
  
 若要讓新的屬性顯示在圖表上，您必須新增*裝飾項目*圖形顯示的模型項目。 此外，您也必須將屬性對應到裝飾項目。  
  
##### <a name="to-add-properties-and-display-them"></a>若要加入屬性，並加以顯示  
  
1. 將屬性加入。  
  
   1.  在 DSL 定義圖表中，以滑鼠右鍵按一下**Person**網域類別，指向**新增**，然後按一下**網域屬性**。  
  
   2.  輸入一份新的屬性名稱，例如**出生**並**死亡**。 按下**Enter**之後每一個。  
  
2. 新增會在圖形中顯示的屬性的裝飾項目。  
  
   1.  請遵循從 Person 網域類別延伸到圖表的另一端的灰線。 這是圖表項目對應。 它會連結到 shape 類別的網域類別。  
  
   2.  此圖形類別上按一下滑鼠右鍵，指向**新增**，然後按一下**文字裝飾項目**。  
  
   3.  加入兩個的裝飾項目名稱，例如**BirthDecorator**並**DeathDecorator**。  
  
   4.  選取每個新的裝飾項目，然後在 [屬性] 視窗中，將**位置**欄位。 這會決定會在圖形上顯示網域屬性值。 例如，設定**InnerBottomLeft**並**InnerBottomRight**。  
  
        ![區間圖形定義](../modeling/media/familyt-compartment.png "FamilyT_Compartment")  
  
3. 將裝飾項目對應到屬性。  
  
   1.  開啟 [DSL 詳細資料] 視窗。 這通常是在 [輸出] 視窗旁邊的索引標籤。 如果您看，在**檢視**功能表上，指向**其他 Windows**，然後按一下**DSL 詳細資料**。  
  
   2.  在 DSL 定義圖表中，按一下 連接的線條**人員**圖形類別的網域類別。  
  
   3.  在  **DSL 詳細資料**上**裝飾項目對應**索引標籤上，按一下 未對應的裝飾項目 核取方塊。 在  **Display 屬性**，選取您要它對應的網域屬性。 例如，對應**BirthDecorator**要**出生**。  
  
4. 儲存 DSL 中，按一下 轉換所有範本，然後按 F5。  
  
5. 在範例模型圖中，確認，您現在可以按一下您所選擇的位置，並在其輸入值。 此外，當您選取**人員**圖形中，[屬性] 視窗會顯示生日及死亡的新屬性。  
  
6. 在.tt 檔案中，您可以加入會取得每個人的內容的程式碼。  
  
   ![家譜圖表、 工具箱和總管](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
### <a name="define-new-classes"></a>定義新的類別  
 您可以將網域類別和關聯性加入模型。 例如，您可以建立新的類別來代表鄉鎮，以及新的關聯性，來代表人員存留現身。  
  
 若要在模型圖上進行不同的類型不同，您可以在不同種類的圖形，或使用不同的幾何和色彩的圖案對應的網域類別。  
  
##### <a name="to-add-and-display-a-new-domain-class"></a>若要新增和顯示新的網域類別  
  
1.  加入網域類別，而讓模型根的子系。  
  
    1.  在 DSL 定義圖表中，按一下**內嵌關聯性**工具，請按一下 根類別**FamilyTreeModel**，然後按一下圖表的空白部分。  
  
         新的網域類別隨即出現，連線到 FamilyTreeModel 與內嵌關聯性。  
  
         設定其名稱，例如**城鎮**。  
  
        > [!NOTE]
        >  模型的根目錄以外的每個網域類別必須是至少一個內嵌關聯性的目標，或必須繼承自的類別，做為目標的內嵌。 基於這個理由，並經常方便使用的內嵌關聯性工具，建立網域類別。  
  
    2.  將網域屬性新增至新的類別，例如**名稱**。  
  
2.  新增參考之間的關聯性 Person 和 Town。  
  
    1.  按一下 **參考關聯性**工具中，按一下 人員，然後按一下 Town。  
  
         ![DSL 定義片段： 家譜根部](../modeling/media/familyt-root.png "FamilyT_Root")  
  
        > [!NOTE]
        >  參考關聯性代表到另一個模型樹狀結構的某一部分的交互參考。  
  
3.  新增圖形以代表鄉鎮的模型圖表上。  
  
    1.  拖曳**幾何圖形**從工具箱拖曳至圖表，並重新命名，例如**TownShape**。  
  
    2.  在 屬性 視窗中，會將新的形狀，例如 填滿色彩和 Geometry 的外觀欄位。  
  
    3.  加入顯示的城鎮名稱的裝飾項目，並將它重新命名 NameDecorator。 設定其位置屬性。  
  
4.  Town 網域類別對應至 TownShape。  
  
    1.  按一下 **圖表項目對應**工具，然後按一下 Town 網域類別，然後按一下 TownShape 圖形類別。  
  
    2.  在 [**裝飾項目對應**] 索引標籤**DSL 詳細資料**選取視窗與對應的連接器、 檢查 NameDecorator 和設定**顯示屬性**名稱。  
  
5.  建立連接器，以顯示人與鄉鎮之間的關聯性。  
  
    1.  將連接器從 [工具箱] 拖曳至圖表。 將它重新命名並設定其外觀屬性。  
  
    2.  使用**圖表項目對應**工具 Person 和 Town 之間的關聯性連結新的連接器。  
  
         ![加入的圖案對應的家譜定義](../modeling/media/familyt-shapemap.png "FamilyT_ShapeMap")  
  
6.  建立項目工具來進行新市鎮。  
  
    1.  在 [ **DSL 總管]**，展開**編輯器**然後**工具箱索引標籤**。  
  
    2.  以滑鼠右鍵按一下 *\<DSL >* ，然後按一下**加入新項目工具**。  
  
    3.  設定**名稱**屬性，新的工具，並設定其**類別**鄉鎮的屬性。  
  
    4.  設定**工具箱圖示**屬性。 按一下  **[...]** 然後在**檔案名稱**欄位中，選取圖示檔。  
  
7.  建立連接器工具進行鄉鎮與人之間的連結。  
  
    1.  以滑鼠右鍵按一下 *\<DSL >* ，然後按一下**加入新的連接器工具**。  
  
    2.  設定新的工具的名稱屬性。  
  
    3.  在  **ConnectionBuilder**屬性中，選取包含人與鄉鎮的關聯性的名稱產生器。  
  
    4.  設定**工具箱圖示**。  
  
8.  儲存 DSL 定義中，按一下**轉換所有範本**，然後按**F5**。  
  
9. 在實驗執行個體[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，開啟測試模型檔案。 使用新的工具來建立鄉鎮和鄉鎮與人員之間的連結。 請注意，您可以只建立正確類型的項目之間的連結。  
  
10. 建立會列出每一個人存留在其中的城鎮的程式碼。 文字範本是其中一個您可以在其中執行這類程式碼的地方。 比方說，您可以修改現有的 Sample.tt 檔案，在偵錯方案中，使其包含下列程式碼：  
  
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
  
     當您儲存的 *.tt 檔案時，它會建立包含清單的人員和其 residences 的附帶檔案。 如需詳細資訊，請參閱 <<c0> [ 特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。  
  
## <a name="validation-and-commands"></a>驗證和命令  
 您可以開發進一步此 DSL 加入驗證條件約束。 這些條件約束是方法，您可以定義，請確認模型處於正確狀態。 例如，您可以定義條件約束，確保孩子的出生日期晚於其父代的。 如果 DSL 使用者嘗試儲存模型，會中斷任何條件約束，驗證的功能就會顯示警告。 如需詳細資訊，請參閱 <<c0> [ 定義域專屬語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)。  
  
 您也可以定義使用者可以叫用的功能表命令。 命令可以修改模型。 也可以與其他模型中互動[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]與外部資源。 如需詳細資訊，請參閱 <<c0> [ 如何： 修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)。  
  
## <a name="deploying-the-dsl"></a>部署 DSL  
 若要允許其他使用者使用特定領域語言，您將散發[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]擴充功能 (VSIX) 檔案。 建置 DSL 方案時，會建立此項目。  
  
 方案 [bin] 資料夾中，找出.vsix 檔案。 請將它複製到您想要將它安裝所在的電腦。 在該電腦中，按兩下 VSIX 檔案。 DSL 可用的所有執行個體在[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]在該電腦上。  
  
 您可以使用相同的程序，讓您不必使用實驗性執行個體，在您自己的電腦上安裝 DSL [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
 如需詳細資訊，請參閱 <<c0> [ 部署特定領域語言方案](../modeling/deploying-domain-specific-language-solutions.md)。  
  
##  <a name="Reset"></a> 移除舊的實驗性 Dsl  
 如果您建立實驗性的 Dsl，您不想再，您可以從您的電腦中移除它們，藉由重設[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]實驗執行個體。  
  
 這會從您的電腦移除所有的實驗性 Dsl 和其他實驗性[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]延伸模組。 這些是已在偵錯模式執行的擴充功能。  
  
 此程序不會移除 Dsl 或其他[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]已藉由執行 VSIX 檔案完整安裝的延伸模組。  
  
#### <a name="to-reset-the-visual-studio-experimental-instance"></a>若要重設 Visual Studio 實驗執行個體  
  
1.  按一下 **開始**，按一下**所有程式**， **Microsoft Visual Studio 2010 SDK**，**工具**，然後**重設 MicrosoftVisual Studio 2010 實驗執行個體**。  
  
2.  重建任何實驗的 Dsl 或其他實驗性[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]仍然想要使用的擴充功能。  
  
## <a name="see-also"></a>另請參閱  
 [了解模型、 類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)   
 [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)   
 [Visualizaton 與模型 SDK](http://go.microsoft.com/fwlink/?LinkID=186128)



