---
title: 對應方案之間的相依性 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
ms.assetid: e04850a2-17c5-459b-93ec-6c74143b3292
caps.latest.revision: 245
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 06dc2d18ab6641847e2f0edb0d34cb671bca28a0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486819"
---
# <a name="map-dependencies-across-your-solutions"></a>對應方案之間的相依性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[對應方案之間的相依性](https://docs.microsoft.com/visualstudio/modeling/map-dependencies-across-your-solutions)。  
  
當您想要了解程式碼之間的相依性時，請建立 Code Map 來將其視覺化。 這可協助您查看程式碼如何搭配運用，而無須閱讀所有檔案和程式碼行。  
  
 ![檢視方案之間的相依性](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
 **部分影片如下**：  
  
-   [透過視覺化了解程式碼相依性](http://go.microsoft.com/fwlink/?LinkID=252065)  
  
-   [以圖形呈現變更的影響](http://go.microsoft.com/fwlink/?LinkID=252068)  
  
-   [使用 Code Map 了解複雜的程式碼](http://go.microsoft.com/fwlink/?LinkID=259869)  
  
##  <a name="GetStarted"></a> 開始使用 Code Map  
 **若要使用 Code Map，您將需要**：  
  
-   Visual Studio Enterprise：從程式碼編輯器、方案總管、類別檢視或物件瀏覽器建立 Code Map。  
  
-   Visual Studio Professional：開啟 Code Map、進行有限的編輯，以及巡覽程式碼。  
  
> [!WARNING]
>  在您與使用 Visual Studio Professional 的其他人共用在 Visual Studio Enterprise 中建立的對應時，請確定對應中的所有項目都已成為可見的，例如隱藏項目、展開的群組和跨群組連結。  
  
 **您可以針對這些語言的程式碼對應相依性**：  
  
-   方案或組件 (.dll 或 .exe) 中的 Visual C# .NET 或 Visual Basic .NET  
  
-   Visual C++ 專案、標頭檔 (.h 或 `#include`) 或二進位檔案中的原生或 Managed C 或 C++ 程式碼  
  
-   由 .NET 模組製作的 Microsoft Dynamics AX X++ 專案和組件  
  
 **附註：** 針對 C# 或 Visual Basic.NET 以外的專案，啟動 Code Map 或是將項目加入現有的 Code Map 之選項較少。 例如，您無法以滑鼠右鍵按一下 C++ 專案中 [文字編輯器] 的物件並將它加入 Code Map。 不過，您可以從方案總管、類別檢視和物件瀏覽器拖放個別程式碼項目或檔案。  
  
#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>查看方案之間的整體相依性  
  
1.  開啟 [架構]  功能表。  
  
2.  如果您剛開啟方案，還沒建置它，或是您的程式碼在您前次建置它之後已變更，請選擇 [產生方案的 Code Map] 。  
  
3.  如果程式碼在前次建置之後未變更，請選擇 [產生方案的 Code Map 而不建置]  ，以在建立對應時得到更快的效能。  
  
4.  [查看整體相依性](#SeeOverviewSource) 來了解如何使用 Code Map，以檢視方案之間的整體相依性。  
  
#### <a name="to-see-specific-dependencies-within-your-solution"></a>查看方案中的特定相依性  
  
1.  載入方案之後，開啟 [方案總管] 。  
  
2.  選取您要對應的所有專案、組件參考、資料夾、檔案、類型或成員。  
  
3.  在 [**方案總管**工具列上，選擇**Code Map 上顯示**![建立新圖形從選取節點] 按鈕](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton"). 或開啟捷徑功能表並選擇 [在 Code Map 上顯示] 。 您也可以從 [類別檢視] 或 [物件瀏覽器] 將項目拖曳至新的或現有的 Code Map。  
  
4.  [查看特定相依性](#SeeSpecificSource) 來了解如何使用 Code Map，以檢視方案中的特定相依性。  
  
###  <a name="CreateEmptyMap"></a> 將新的空白 Code Map 加入您的方案  
  
1.  在 [方案總管] 中，開啟最上層方案節點的捷徑功能表。 選擇 [新增]  然後選擇 [新增項目] 。  
  
2.  在 [已安裝的] 底下，選擇 [一般] 。  
  
3.  在右窗格中，依序選擇 [有向圖形文件]  和 [新增] 。  
  
     現在即有一個空白對應，出現在您方案的 [方案項目]  資料夾中。  
  
#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>建立新的空 Code Map，而不將它加入您的方案  
  
1.  開啟 [架構]  功能表，然後選擇 [新增 Code Map] 。  
  
     \-或-  
  
2.  開啟 [檔案]  功能表，依序選擇 [新增]  和 [檔案] 。  
  
3.  在 [已安裝的] 底下，選擇 [一般] 。  
  
4.  在右窗格中，依序選擇 [有向圖形文件]  和 [開啟] 。  
  
     現在即有一個空白對應，它不會出現在您方案的資料夾中。  
  
##  <a name="SeeOverviewSource"></a> 查看整體相依性  
  
###  <a name="OverviewSource"></a> 查看方案中的相依性  
  
1.  在 [架構]  功能表上，選擇 [產生方案的 Code Map] 。  
  
     ![產生 code map 命令](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")  
  
     即可取得顯示最上層組件和其彙總連結的對應。 彙總連結愈廣，代表的相依性就愈高。  
  
2.  使用 Code Map 工具列上的 [圖例]  按鈕以顯示或隱藏專案類型圖示清單 (例如測試、Web 和 Phone 專案)，程式碼項目 (例如類別、方法和屬性)，和關聯性類型 (例如「繼承自」、「實作」，和「呼叫」)。  
  
     ![前&#45;的組件層級的相依性圖形](../modeling/media/dependencygraph-toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")  
  
     此範例方案包含方案資料夾 ([測試] 和 [元件] )、測試專案、Web 專案和組件。 所有內含項目關聯性預設會顯示為 *「群組」*(group)，您可將其展開及摺疊。 [外部]  群組中含有在您的方案之外的任何項目，包括平台相依性。 外部組件只會顯示所使用的項目。 根據預設，系統基底類型在對應中會隱藏，以減少雜亂。  
  
3.  若要向下切入到對應，請展開代表專案和組件的群組。 您可以藉由按下 **CTRL + A** 選取所有節點，然後從捷徑功能表選擇 [群組] 、[展開]  ，展開所有項目。  
  
     ![展開所有群組中的 code map](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")  
  
4.  不過，這可能不適用於大型的方案。 事實上，對於複雜的方案而言，記憶體限制可能會導致您無法展開所有群組。 相反地，若要查看個別節點的內部，請展開它。 將滑鼠指標移至節點上方，然後按一下出現的＞形箭號 (向下箭號)。  
  
     ![展開節點，以在 code map](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
     或使用鍵盤選取項目，然後按下加號鍵 (**+**)。 若要瀏覽更深層的程式碼，請為命名空間、類型和成員執行相同的作業。  
  
    > [!TIP]
    >  如需詳細資訊，使用程式碼的對應使用滑鼠、 鍵盤及觸控裝置，請參閱[瀏覽和重新整理 code map](../modeling/browse-and-rearrange-code-maps.md)。  
  
5.  若要簡化對應，並將焦點放在個別部分，請選擇 Code Map 工具列上的 [篩選]  ，然後只選取您感興趣的節點和連結類型。 例如，您可以隱藏所有的方案資料夾和組件容器。  
  
     ![篩選容器以精簡對應](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")  
  
     您也可以隱藏或移除對應上的個別群組和項目來簡化對應，而不會影響基礎的方案程式碼。  
  
6.  若要查看項目之間的關聯性，請在對應中加以選取。 連結的色彩表示關聯性的類型，如 [圖例]  窗格中所示。  
  
     ![檢視方案之間的相依性](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
     在此範例中，紫色連結是呼叫、虛線的連結是參考，而淺藍色連結則是欄位存取。 綠色的連結可以是繼承，或者可以是 *「彙總連結」* (aggregate link)，表示多個關聯性類型 (或 *「分類」*(category))。  
  
    > [!TIP]
    >  如果看到綠色連結，可能不表示只有繼承關聯性。 也有可能是方法呼叫，但是繼承關聯性將其隱藏。 若要查看特定類型的連結，請使用 [篩選]  窗格中的核取方塊，隱藏您不感興趣的類型。  
  
7.  若要取得項目或連結的詳細資訊，請將指標移到頂端，直到出現工具提示。 這會顯示程式碼項目或連結代表的類別分類的詳細資料。  
  
     ![顯示關聯性的類別](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")  
  
8.  若要檢查彙總連結代表的項目和相依性，請先選取連結，然後開啟其捷徑功能表。 選擇 [顯示參與連結]  (或 [在新 Code Map 上顯示參與連結] )。 這會展開在連結兩端的群組，並只顯示參與此連結的項目和相依性。  
  
9. 若要將焦點放在對應的特定部分，您可以繼續移除您不感興趣的項目。 例如，若要向下鑽研到類別和成員檢視，只要篩選 [篩選]  窗格中的所有命名空間節點。  
  
     ![鑽研到類別和成員層級](../modeling/media/dependencygraph-expandedselectedgroups-2012.png "DependencyGraph_ExpandedSelectedGroups_2012")  
  
10. 專注於複雜方案對應的另一個方法是產生新的對應，其中包含來自現有對應的選取項目。 選取您想要專注的項目時按住 **CTRL** ，開啟捷徑功能表，然後選擇 [從選取範圍新增圖形] 。  
  
     ![新的 code map 上顯示選取的項目](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")  
  
11. 包含的內容會轉至新的對應。 使用 [篩選]  窗格隱藏方案資料夾和您不想查看的其他容器。  
  
     ![篩選容器以精簡檢視](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")  
  
12. 展開群組，然後選取對應中的項目以檢視關聯性。  
  
     ![選取要檢視的關聯性項目](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")  
  
 另請參閱：  
  
-   [瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [藉由編輯 DGML 檔案自訂 Code Map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)  
  
-   [執行分析器](../modeling/find-potential-problems-using-code-map-analyzers.md)找出程式碼中的潛在問題。  
  
###  <a name="OverviewCompiled"></a> 查看跨組件或二進位檔案的相依性  
  
1.  [建立空的 Code Map](#GetStarted)，或開啟現有的 Code Map (.dgml 檔案)。  
  
2.  將您想要對應的組件或二進位檔從 Visual Studio 外部拖曳到對應上。 例如，從 Windows 檔案總管或檔案總管拖曳組件或二進位檔。  
  
> [!NOTE]
>  只要您是以相同的使用者存取控制 (UAC) 權限等級執行它與 Visual Studio，就可以從 Windows 檔案總管或檔案總管拖曳組件或二進位檔。 例如，如果 UAC 已開啟，而您是以系統管理員身分執行 Visual Studio，那麼 Windows 檔案總管或檔案總管將會封鎖拖曳作業。 若要解決這個問題，請確定兩者都執行相同的權限等級，或關閉 UAC。  
  
##  <a name="SeeSpecificSource"></a> 查看特定相依性  
 例如，假設您有要在出現暫止變更的某些檔案中，執行程式碼檢閱。 若要查看這些變更中的相依性，您可以從那些檔案建立 Code Map。  
  
 ![在 code map 上顯示的特定相依性](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
### <a name="see-specific-dependencies-in-your-solution"></a>查看方案中的特定相依性  
  
1.  開啟 [方案總管] 。 選取您感興趣的專案、組件參考、資料夾、檔案、類型和成員。 若要尋找與類型或成員相依的項目，請在 [方案總管] 中開啟類型或成員的捷徑功能表。 選擇相依性類型，並選取結果。  
  
2.  對應您的項目及其成員。 在 [**方案總管**工具列上，按一下**Code Map 上顯示**![建立新圖形從選取節點] 按鈕](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").  
  
     ![選取您想要對應的項目](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")  
  
3.  對應會在其包含的組件內顯示選取的項目。  
  
     ![選取的項目顯示為地圖上的群組](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")  
  
     您也可以從 [方案總管]、[類別檢視] 或 [物件瀏覽器] 將項目拖曳至空白的或現有的 Code Map。 若要建立空白的對應，請參閱 [建立空白的 Code Map](#GetStarted)。 若要包含項目的父階層，請按住 **CTRL** 鍵不放同時拖曳項目，或使用 Code Map 工具列上的 [包含父代]  按鈕，指定預設動作。  
  
    > [!NOTE]
    >  當您從跨多個應用程式 (如 Windows Phone 或 Windows 市集) 共用的專案中加入項目時，這些項目會與目前作用中的應用程式專案出現在對應上。 如果您將內容變更為其他應用程式專案，並且從共用專案加入更多項目，這些項目現在會與新的作用中應用程式專案一起顯示。 您使用對應中項目執行的作業僅適用於共用相同內容的項目。  
  
4.  若要瀏覽項目，請將其展開。 將滑鼠指標移至項目上方，然後按一下出現的＞形箭號 (向下箭號) 圖示。  
  
     ![展開節點，以在 code map](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
     若要展開所有項目，請使用 **CTRL+A**選取它們，然後開啟對應的捷徑功能表並依序選擇 [群組] 、[展開] 。 不過，如果展開所有群組會產生無法使用的對應或記憶體問題，則無法使用此選項。  
  
5.  繼續展開您感興趣的項目，視需要可一直到類別和成員層級。  
  
     ![將群組展開至類別和成員層級](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")  
  
     若要查看成員程式碼中，但不會出現在地圖上，按一下**重新擷取子系**圖示![重新擷取子系圖示](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon")右上群組的左上的角。  
  
6.  若要查看與對應上之項目相關的其他項目，請選取一個，在 Code Map 工具列上選擇 [顯示相關]  ，然後選取要加入對應的相關項目類型。 或者，選取一或多個項目，開啟捷徑功能表，然後針對要加入對應的相關項目類型選擇 [顯示]  選項。 例如:   
  
     對於 **組件**，選擇：  
  
    |||  
    |-|-|  
    |**顯示這一項參考的組件**|加入這個組件參考的組件。 外部組件會出現在 [外部]  群組中。|  
    |**顯示參考這一項的組件**|從參考這個組件的方案中加入組件。|  
  
     對於 **命名空間**，選擇 [顯示包含的組件] (如果看不到的話)。  
  
     對於 **類別** 或 **介面**，選擇：  
  
    |||  
    |-|-|  
    |**顯示基底類型**|對於類別，加入基底類別和實作的介面。<br /><br /> 對於介面，加入基底介面。|  
    |**顯示衍生類型**|對於類別，加入衍生類別。<br /><br /> 對於介面，加入衍生介面和實作類別或結構。|  
    |**顯示這一項參考的類型**|加入這個類別使用的所有類別和其成員。|  
    |**顯示參考這一項的類型**|加入使用這個類別的所有類別及其成員。|  
    |**顯示包含的命名空間**|加入父命名空間。|  
    |**顯示包含的命名空間和組件**|加入父容器階層架構。|  
    |**顯示所有基底類型**|以遞迴方式加入基底類別或介面階層架構。|  
    |**顯示所有衍生型別**|對於類別，以遞迴方式加入所有衍生類別。<br /><br /> 對於介面，以遞迴方式加入所有衍生介面和實作類別或結構。|  
  
     對於 **方法**，選擇：  
  
    |||  
    |-|-|  
    |**顯示這一項呼叫的方法**|加入這個方法呼叫的方法。|  
    |**顯示這一項參考的欄位**|加入這個方法所參考的欄位。|  
    |**顯示包含的類型**|加入父類型。|  
    |**顯示包含的類型、命名空間和組件**|加入父容器階層架構。|  
    |**顯示覆寫方法**|對於覆寫其他方法或實作介面方法的方法，加入所覆寫之基底類別中的所有抽象或虛擬方法，以及所實作之介面的方法 (若有的話)。|  
  
     對於 **欄位** 或 **屬性**，選擇：  
  
    |||  
    |-|-|  
    |**顯示包含的類型**|加入父類型。|  
    |**顯示包含的類型、命名空間和組件**|加入父容器階層架構。|  
  
     ![顯示這個成員所呼叫方法](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")  
  
7.  對應會顯示關聯性。 在此範例中，由 `Find` 方法呼叫的方法，以及它們在方案或外部的位置。  
  
     ![在 code map 上顯示的特定相依性](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
8.  若要簡化對應，並將焦點放在個別部分，請選擇 Code Map 工具列上的 [篩選]  ，然後只選取您感興趣的節點和連結類型。 例如，關閉方案資料夾、組件和命名空間的顯示。  
  
     ![使用 [篩選] 窗格來簡化顯示](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")  
  
##  <a name="SeeSourceHeader"></a> 查看 C 與 C++ 原始程式檔與標頭檔之間的相依性  
 如果要為 C++ 專案建立更完整的對應，請在這些專案上設定瀏覽資訊編譯器選項 (**/FR**)。 請參閱[/FR、 /Fr （建立）。Sbr 檔案）](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896)。 否則會出現訊息並提示您設定此選項。 如果選取 [確定] ，則只會為目前的對應設定這個選項。 您可以選擇隱藏所有之後對應的訊息。 如果隱藏這個訊息，之後可以讓它再次出現。 請將下列登錄機碼設定為 `0` ，或刪除該機碼：  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\NativeProvider : AutoEnableSbr**  
  
 當您開啟包含 Visual C++ 專案的方案時，更新 IntelliSense 資料庫可能需要一些時間。 此時，您可能無法建立標頭 (.h 或 `#include`) 檔案的 Code Map，直到 IntelliSense 資料庫完成更新。 您可以在 Visual Studio 狀態列中監視更新進度。 若要解決因為某些 IntelliSense 設定停用而發生的問題或訊息，請參閱 [C 和 C++ 程式碼對應疑難排解](#Troubleshooting)。  
  
-   若要查看方案中所有原始程式檔與標頭檔之間的相依性，請在 [架構]  功能表上，選擇 [產生 Include 檔圖形] 。  
  
     ![原生程式碼的相依性圖形](../modeling/media/dependencygraphgeneral-nativecode.png "DependencyGraphGeneral_NativeCode")  
  
-   若要查看目前開啟的檔案與相關原始程式檔和標頭檔之間的相依性，請開啟原始程式檔或標頭檔。 在檔案內的任意處開啟檔案捷徑功能表。 選擇 [產生 Include 檔圖形] 。  
  
     ![第一個&#45;.h 檔案的層級的相依性圖形](../modeling/media/dependencygraph-native-firstlevel.png "DependencyGraph_Native_FirstLevel")  
  
###  <a name="Troubleshooting"></a> C 和 C++ 程式碼對應疑難排解  
 C 和 C++ 程式碼不支援下列項目：  
  
-   基底類型不會出現在包含父代階層架構的對應中。  
  
-   大部分的 [顯示]  功能表項目無法供 C 和 C++ 程式碼使用。  
  
 建立 C 和 C++ 程式碼的 Code Map 時，可能會發生下列問題：  
  
|**問題**|**可能的原因**|**解決方法**|  
|---------------|------------------------|--------------------|  
|無法產生 Code Map。|方案中沒有成功建立的專案。|修正發生的建置錯誤，然後重新產生對應。|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 變得沒有回應，當您嘗試將產生的 code map**架構**功能表。|程式資料庫 (.pdb) 檔案可能會損毀。<br /><br /> .pdb 檔案會儲存偵錯資訊，例如類型、方法和原始程式檔資訊。|重建方案後再試一次。|  
|IntelliSense 瀏覽資料庫的某些設定已停用。|某些 IntelliSense 設定可能會在停用[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**選項** 對話方塊。|開啟這些設定來加以啟用。<br /><br /> 請參閱[選項、 文字編輯器、 C/c + +、 進階](../ide/reference/options-text-editor-c-cpp-advanced.md)。|  
|[未知方法]  訊息出現在方法節點上。<br /><br /> 發生這個問題是因為無法解析方法的名稱。|二進位檔可能沒有基底重新配置表格。|在連結器中開啟 **/FIXED:NO** 選項。<br /><br /> 請參閱[能有 /FIXED （固定基底位址）](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5)。|  
||程式資料庫 (.pdb) 檔案可能無法建置。<br /><br /> .pdb 檔案會儲存偵錯資訊，例如類型、方法和原始程式檔資訊。|在連結器中開啟 **/DEBUG** 選項。<br /><br /> 請參閱[/debug (Generate Debug Info)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103)。|  
||無法在預期的位置中開啟或找到 .pdb 檔案。|請確定預期的位置中有 .pdb 檔案存在。|  
||已從 .pdb 檔案中移除偵錯資訊。|如果在連結器中使用 **/PDBSTRIPPED** 選項，請改為包含完整的 .pdb 檔案。<br /><br /> 請參閱[/PDBSTRIPPED （移除專用符號）](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55)。|  
||呼叫端不是函式，而且為二進位檔案中的 Thunk 或資料區段中的指標。|當呼叫端為 Thunk 時，請嘗試使用 `_declspec(dllimport)` 來避免 Thunk。<br /><br /> 請參閱：<br /><br /> -   [一般規則和限制](http://msdn.microsoft.com/library/6c48902d-4259-4761-95d4-e421d69aa050)<br />-   [匯入函式呼叫使用 __declspec （dllimport）](http://msdn.microsoft.com/library/6b53c616-0c6d-419a-8e2a-d2fff20510b3)<br />-   [dllexport、 dllimport](http://msdn.microsoft.com/library/ff95b645-ef55-4e72-b848-df44657b3208)|  
  
##  <a name="RenderMoreQuickly"></a> 使 Code Map 更快速地轉譯  
 當您第一次產生對應時，Visual Studio 會為所有找到的相依性編製索引。 此程序可能需要一些時間 (尤其是大型方案)，但這可以改善之後的效能。 如果程式碼變更，則 Visual Studio 只會重新編製更新過的程式碼索引。 若要將完成轉譯對應所花費的時間降到最低，請考慮下列各項：  
  
-   [只對應您感興趣的相依性。](#SeeSpecificSource)  
  
-   在您產生整個方案的對應前，請縮小方案範圍。  
  
-   使用 Code Map 工具列上的 [略過建置]  按鈕，關閉自動建置方案。  
  
-   使用 Code Map 工具列上的 [包含父代]  按鈕，關閉自動加入父項目。  
  
-   編輯 Code Map，直接移除您不需要的節點和連結。 變更對應不會影響基礎程式碼。 請參閱 [藉由編輯 DGML 檔案自訂 Code Map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)。  
  
 ![略過建置] 和 [包含父代按鈕](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")  
  
 雖然 Visual Studio 可以使用 1 GB 的記憶體來執行，但建議您的電腦至少要有 2 GB 的記憶體，以免在 Visual Studio 建立程式碼索引並產生對應時延遲過於冗長。  
  
 當專案項目的 [複製到輸出目錄]  屬性設定為 [永遠複製] 時，可能需要更多時間從 [方案總管] 中建立對應或將項目加入對應。 這可能會導致累加建置問題，而且會使 Visual Studio 每次都重新建置專案。 若要增加效能，請將這個屬性變更為 **有更新時才複製** 或 `PreserveNewest`。 請參閱 [Incremental Builds](../msbuild/incremental-builds.md)。  
  
 完成的對應只會顯示成功建置之程式碼的相依性。 如果某些元件發生建置錯誤，則對應上會出現這些錯誤。 在根據對應進行架構決策前，請確定元件可實際建置且具有相依性。  
  
##  <a name="SavingExporting"></a> 共用 Code Map  
  
### <a name="share-the-map-with-other-visual-studio-users"></a>與其他 Visual Studio 使用者共用對應  
 使用 [檔案]  功能表以儲存對應。  
  
 -或-  
  
 若要為特定專案的一部分儲存對應，對應圖工具列上，選擇**共用**，**移動** \< *CodeMapName*>**.dgml到**，然後選擇您要儲存對應的專案。  
  
 ![將對應移至另一個專案](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")  
  
 Visual Studio 會將對應儲存為 .dgml 檔案，讓您可以和其他 Visual Studio Enterprise 和 Visual Studio Professional 的使用者共用。  
  
> [!NOTE]
>  在您與 Visual Studio Professional 使用者共用對應之前，請展開所有群組，顯示隱藏的節點和跨群組連結，並擷取任何您希望其他人在對應看到的已刪除節點。 否則，其他使用者就無法看到這些項目。  
>   
>  若您儲存的對應是位於模型專案中，或此對應是從模型專案複製到另一個位置，就會發生下列錯誤：  
>   
>  「無法將 *fileName* 儲存在專案目錄外。 不支援連結項目。」  
>   
>  Visual Studio 顯示錯誤，不過還是會建立儲存的版本。 若要避免此錯誤，請將對應建立在模型專案之外。 然後您可以將它儲存到您想要的位置。 只將檔案複製到方案中的另一個位置然後再嘗試儲存，這種做法不會有用。  
  
### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>將對應匯出為影像，因此您可以將它複製到其他應用程式，例如 Microsoft Word 文件或 PowerPoint  
  
1.  在 Code Map 工具列上，依序選擇 [共用] 、[以影像傳送電子郵件]  或 [複製影像] 。  
  
2.  將影像貼入另一個應用程式中。  
  
### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>將對應匯出為 XPS 檔案，如此您就可以在類似 Internet Explorer 的 XML 或 XAML 檢視器中查看  
  
1.  在 Code Map 工具列上，依序選擇 [共用] 、[以可攜式 XPS 傳送電子郵件]  或 [另存為可攜式 XPS] 。  
  
2.  瀏覽至儲存檔案的位置。  
  
3.  為 Code Map 命名。 請確定**將儲存為類型** 方塊設定為**XPS 檔案 (\*.xps)**。 選擇 [儲存] 。  
  
## <a name="what-else-can-i-do"></a>我還可以做什麼？  
  
-   [使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [在偵錯時於呼叫堆疊上對應方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)  
  
-   [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
-   [瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [藉由編輯 DGML 檔案自訂 Code Map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)



