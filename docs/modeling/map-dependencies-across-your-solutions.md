---
title: Code Map
ms.date: 05/16/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 553e2437abc2d8f498b556300a9266c9e79297f7
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265561"
---
# <a name="map-dependencies-with-code-maps"></a>使用 code map 中對應的相依性

您可以視覺化程式碼之間的相依性，藉由建立 code map。 Code map 可協助您查看如何將程式碼搭配運用，而無須閱讀所有檔案和程式碼行。

![檢視方案之間的相依性](../modeling/media/codemapsmainintro.png)

若要使用 code map，您將需要 Visual Studio Enterprise 或 Professional 版。 Professional edition 中的程式碼地圖功能會比在 Enterprise edition 中稍微限制。

> [!NOTE]
> 共用在 Visual Studio Enterprise 中建立與其他使用 Visual Studio Professional 的對應之前，請確定在地圖，例如隱藏的項目、 展開的群組和跨群組連結） 上的所有項目會顯示。

您可以將對應的相依性這些語言的程式碼：

- Visual C# 或 Visual Basic 中的方案或組件 (*.dll*或 *.exe*)

- 原生或 managed C 或 c + + 程式碼在 Visual c + + 專案中，標頭檔 (*.h*或`#include`)，或二進位檔

- 由 .NET 模組製作的 Microsoft Dynamics AX X++ 專案和組件

> [!NOTE]
> 針對 C# 或 Visual Basic 以外的專案，有較少的選項，啟動 code map 或是將項目加入至現有的 code map。 例如，您無法以滑鼠右鍵按一下 C++ 專案中 [文字編輯器] 的物件並將它加入 Code Map。 不過，您可以拖放個別程式碼項目或檔案從**方案總管 中**，**類別檢視**，和**物件瀏覽器**。

## <a name="install-code-map-and-live-dependency-validation"></a>安裝程式碼對應和即時的相依性驗證

若要建立 Visual Studio 2017 code map，第一次安裝**Code Map**和**Live 相依性驗證**元件：

1. 開啟**Visual Studio 安裝程式**。 您可以開啟它從 [開始] 功能表中，或在 Visual Studio 中選取**工具** > **取得工具和功能**。

1. 選取 [個別元件] 索引標籤。

1. 向下捲動至**程式碼工具**區段，然後選取**Code Map**和**Live 相依性驗證**。

   ![在 Visual Studio 安裝程式的程式碼對應和即時相依性驗證元件](media/modeling-components.png)

1. 選取 [修改]。

   **Code Map**和**Live 相依性驗證**元件可讓您開始安裝。 系統可能會要求您關閉 Visual Studio。

## <a name="add-a-code-map"></a>加入程式碼對應

您可以建立空的 code map，並將項目拖曳到它，包括組件參考的檔案與資料夾，或您可以產生所有的 code map 或方案的一部分。

若要加入空白的 code map:

1. 在 [方案總管] 中，開啟最上層方案節點的捷徑功能表。 選擇**新增** > **新項目**。

2. 在**加入新項目**對話方塊下方**已安裝**，選擇**一般**類別目錄。

3. 選擇**導向圖形 Document(.dgml)** 範本，然後選取**新增**。

   > [!TIP]
   > 此範本可能不會顯示依字母順序，因此向下捲動 [範本] 清單的底部如果您沒有看到它。

   空白的對應會出現在您的方案**方案項目**資料夾。

同樣地，您可以建立新的 code map，而不將它加入至方案，藉由選取**架構** > **新的 Code Map**或**檔案** > **新** > **檔案**。

## <a name="generate-a-code-map-for-your-solution"></a>產生您方案的程式碼對應

若要查看方案中的所有相依性：

1. 在功能表列上選擇 **架構** > **產生方案的 Code Map**。 如果您的程式碼沒有變更，最後一次建置之後，您可以選取**架構** > **產生而不建置方案的 Code Map**改為。

   ![產生程式碼對應命令](../modeling/media/codemapsarchitecturemenu.png)

   地圖會產生顯示最上層組件和它們之間的彙總的連結。 彙總連結愈廣，代表的相依性就愈高。

2. 使用 Code Map 工具列上的 [圖例]  按鈕以顯示或隱藏專案類型圖示清單 (例如測試、Web 和 Phone 專案)，程式碼項目 (例如類別、方法和屬性)，和關聯性類型 (例如「繼承自」、「實作」，和「呼叫」)。

   ![組件的最上層相依性圖形](../modeling/media/dependencygraph_toplevelassemblies.png)

   此範例方案包含方案資料夾 ([測試] 和 [元件] )、測試專案、Web 專案和組件。 所有內含項目關聯性預設會顯示為 *「群組」*(group)，您可將其展開及摺疊。 [外部]  群組中含有在您的方案之外的任何項目，包括平台相依性。 外部組件只會顯示所使用的項目。 根據預設，系統基底類型在對應中會隱藏，以減少雜亂。

3. 若要向下切入到對應，請展開代表專案和組件的群組。 您可以藉由按下 **CTRL + A** 選取所有節點，然後從捷徑功能表選擇 [群組] 、[展開]  ，展開所有項目。

   ![展開程式碼對應中的所有群組](../modeling/media/codemapsexpandallgroups.png)

4. 不過，這可能不適用於大型的方案。 事實上，對於複雜的方案而言，記憶體限制可能會導致您無法展開所有群組。 相反地，若要查看個別節點的內部，請展開它。 將滑鼠指標移至節點上方，然後按一下出現的＞形箭號 (向下箭號)。

   ![展開 Code Map 中的節點](../modeling/media/dependencygraph_containment.png)

   或使用鍵盤選取項目，然後按下加號鍵 (**+**)。 若要瀏覽更深層的程式碼，請為命名空間、類型和成員執行相同的作業。

   > [!TIP]
   > 如需詳細資訊使用程式碼對應使用滑鼠、 鍵盤和觸控，請參閱[瀏覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)。

5. 若要簡化對應，並將焦點放在個別部分，請選擇 Code Map 工具列上的 [篩選]  ，然後只選取您感興趣的節點和連結類型。 例如，您可以隱藏所有的方案資料夾和組件容器。

   ![篩選容器以精簡對應](../modeling/media/codemapsfilterfoldersassemblies.png)

   您也可以隱藏或移除對應上的個別群組和項目來簡化對應，而不會影響基礎的方案程式碼。

6. 若要查看項目之間的關聯性，請在對應中加以選取。 連結的色彩表示關聯性的類型，如 [圖例]  窗格中所示。

   ![檢視方案之間的相依性](../modeling/media/codemapsmainintro.png)

   在此範例中，紫色連結是呼叫、虛線的連結是參考，而淺藍色連結則是欄位存取。 綠色的連結可以是繼承，或者可以是 *「彙總連結」* (aggregate link)，表示多個關聯性類型 (或 *「分類」*(category))。

   > [!TIP]
   > 如果看到綠色連結，可能不表示只有繼承關聯性。 也有可能是方法呼叫，但是繼承關聯性將其隱藏。 若要查看特定類型的連結，使用中的核取方塊**篩選**窗格，即可隱藏您不感興趣的類型。

7. 若要取得項目或連結的詳細資訊，請將指標移到頂端，直到出現工具提示。 這會顯示程式碼項目或連結代表的類別分類的詳細資料。

   ![顯示關聯性的類別目錄](../modeling/media/codemapsshowlinkcatgories.png)

8. 若要檢查彙總連結代表的項目和相依性，請先選取連結，然後開啟其捷徑功能表。 選擇 [顯示參與連結]  (或 [在新 Code Map 上顯示參與連結] )。 這會展開在連結兩端的群組，並只顯示參與此連結的項目和相依性。

9. 若要將焦點放在對應的特定部分，您可以繼續移除您不感興趣的項目。 例如，若要向下鑽研到類別和成員檢視，只要篩選 [篩選]  窗格中的所有命名空間節點。

   ![向下鑽研類別及成員層級](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. 專注於複雜方案對應的另一個方法是產生新的對應，其中包含來自現有對應的選取項目。 保存**Ctrl**時選取您想要專注的項目，開啟捷徑功能表，然後選擇 **從選取範圍的新圖形**。

   ![在新的 Code Map 上顯示選取的項目](../modeling/media/codemapsshowonnewmap.png)

11. 包含的內容會轉至新的對應。 隱藏方案資料夾和您不想要查看使用的其他容器**篩選**窗格。

   ![篩選容器以精簡檢視](../modeling/media/codemapsexpandnewgroups.png)

12. 展開群組，然後選取對應中的項目以檢視關聯性。

   ![選取項目以檢視其關聯性](../modeling/media/codemapsviewnewrelationships.png)

另請參閱：

- [瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)
- [藉由編輯 DGML 檔案自訂 Code Map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- 尋找程式碼中的潛在問題[執行分析器](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-specific-dependencies-in-a-code-map"></a>檢視程式碼對應中的特定相依性

假設您有要在出現暫止變更的某些檔案中執行的程式碼檢閱。 若要查看這些變更中的相依性，您可以從那些檔案建立 Code Map。

   ![顯示與 Code Map 之間的相依性](../modeling/media/codemapsspecificdependenciesintro.png)

1. 在**方案總管 中**，選取專案、 組件參考、 資料夾、 檔案、 類型或您想要對應的成員。

   ![選取您要對應的項目](../modeling/media/codemapsselectinsolutionexplorer.png)

1. 在**方案總管 中**工具列上，選擇**Code Map 上顯示**![建立新圖表中選取節點 按鈕](../modeling/media/createnewgraphfromselectedbutton.gif)。 或者，開啟一個或一組項目的捷徑功能表，然後選擇  **Code Map 上顯示**。

   您也可以拖曳項目從**方案總管 中**，**類別檢視**，或**物件瀏覽器**，到[新](#add-a-code-map)或現有的程式碼對應。 若要包含項目的父階層，請按住**Ctrl**鍵不放同時拖曳項目，或使用**包含父代**來指定預設動作的 code map 工具列上的按鈕。 您也可以將這類組件檔從 Visual Studio 外部，從**Windows 檔案總管**。

   > [!NOTE]
   > 當您從共用跨多個應用程式，例如 Windows Phone 或 Microsoft 市集專案中加入項目這些項目會出現在目前作用中的應用程式專案的對應。 如果您將內容變更為其他應用程式專案，並且從共用專案加入更多項目，這些項目現在會與新的作用中應用程式專案一起顯示。 您使用對應中項目執行的作業僅適用於共用相同內容的項目。

3. 對應會在其包含的組件內顯示選取的項目。

   ![在地圖上顯示為群組的選取項目](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. 若要瀏覽項目，請將其展開。 將滑鼠指標移至項目上方，然後按一下出現的＞形箭號 (向下箭號) 圖示。

   ![展開 code map 中的節點](../modeling/media/dependencygraph_containment.png)

   若要展開所有項目，請選取它們使用**Ctrl**+**A**，然後開啟對應的捷徑功能表並選擇**群組** >  **展開**。 不過，如果展開所有群組會產生無法使用的對應或記憶體問題，則無法使用此選項。

5. 繼續展開您感興趣，一直到類別和成員層級必要項目。

   ![將群組展開至類別與成員](../modeling/media/codemapsexpandtoclassandmember.png)

   若要查看成員程式碼中，但不會出現在地圖上，按一下 **重新擷取子系**圖示![重新擷取子系圖示](../modeling/media/dependencygraph_deletednodesicon.png)中群組的左上角。

6. 若要查看與對應上之項目相關的其他項目，請選取一個，在 Code Map 工具列上選擇 [顯示相關]  ，然後選取要加入對應的相關項目類型。 或者，選取一或多個項目、 開啟捷徑功能表，然後選擇**顯示**將加入至對應的相關項目類型的選項。 例如: 

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

    ![顯示此成員呼叫的方法](../modeling/media/codemapsshowrelatedmethods.png)

7. 對應會顯示關聯性。 在此範例中，對應可顯示所呼叫的方法`Find`方法以及它們在方案或外部的位置。

   ![顯示與 Code Map 之間的相依性](../modeling/media/codemapsspecificdependenciesintro.png)

8. 若要簡化對應，並將焦點放在個別部分，請選擇 Code Map 工具列上的 [篩選]  ，然後只選取您感興趣的節點和連結類型。 例如，關閉方案資料夾、組件和命名空間的顯示。

   ![使用 [篩選] 窗格來簡化顯示](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>另請參閱

- [視訊： 了解從 Visual Studio 2015 程式碼對應的程式碼設計](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)]
- [使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)
- [偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)
- [藉由編輯 DGML 檔案自訂 Code Map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
