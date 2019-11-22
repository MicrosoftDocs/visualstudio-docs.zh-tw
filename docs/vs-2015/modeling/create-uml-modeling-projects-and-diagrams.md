---
title: 建立 UML 模型專案和圖表 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5884dcd3f9e3cb8f1910d2e23ec80f910ed2fc9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301005"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>建立 UML 模型專案和圖表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 模型可協助您了解、討論及設計軟體系統。 Visual Studio 提供其中五個最常用的 UML 圖表的範本：活動圖、類別圖、元件圖、循序圖和使用案例圖。 此外，您可以建立圖層圖表，協助您定義系統的結構。

 UML 模型圖表與圖層圖表可以只存在於模型專案內部。 每個模型專案都包含共用的 UML 模型和數個 UML 圖表。 每個圖表都是模型的部分檢視。 UML 模型包含 UML 圖表上的所有元素，而且可以使用 [UML 模型總管] 來檢視。 如需模型及其與圖表關聯性的詳細資訊，請參閱[編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)。 如需版本控制下之模型專案的相關資訊，請參閱[在版本控制下管理模型和圖表](../modeling/manage-models-and-diagrams-under-version-control.md)和[建立模型方案的結構](../modeling/structure-your-modeling-solution.md)

> [!NOTE]
> 還有另一種圖表，也就是 .NET 類別圖表，可用來將程式碼視覺化。 如需詳細資訊，請參閱[設計和檢視類別與類型](https://go.microsoft.com/fwlink/?LinkId=142231)。

## <a name="CreatingModelingDiagrams"></a>在模型專案中建立圖表
 若要查看哪些版本的 Visual Studio 支援此功能，請參閱 [Architecture and Modeling Tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>若要建立圖表，請將它加入至專案

1. 在 [架構] 功能表上選擇 [新增 UML 或分層圖]。

2. 在 [加入新的圖表] 對話方塊中，按一下您想要的模型圖表類型。

    ![[加入新的圖表] 對話方塊](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. 輸入新圖表的名稱。

4. 在 [加入至模型專案] 方塊中：

   - 選取方案中已經存在的模型專案，然後按一下 [確定]。

     \-或-

   1. 選取 [建立新的模型專案]，然後按一下 [確定]。

   2. 在 [建立新的模型專案] 對話方塊中，輸入新專案的名稱和位置，然後按一下 [確定]。

        ![[建立新模型專案] 對話方塊](../modeling/media/uml-createmodel.png "UML_CreateModel")

        如果您的方案已經開啟，新的專案便會加入至方案中。 如果您沒有任何開啟的方案，則可以輸入新方案的名稱。

   如果您已經有模型專案時，也可以使用下列程序。

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>將圖表加入至現有的模型專案

1. 在 [方案總管] 中，按一下模型專案節點。

    > [!NOTE]
    > 模型專案包含一個名為 [模型定義] 的模型定義資料夾。

2. 在 [專案] 功能表中，按一下 [加入新項目]。

3. 在 [**加入新專案-** *\<專案名稱 >* ] 對話方塊的 [**範本**] 底下，按一下模型圖表類型，例如 [ **UML 元件圖**]。

4. 輸入圖表的名稱，然後按一下 [加入]。

     模型圖表隨即開啟，並出現在模型專案中。

    > [!CAUTION]
    > 不要加入、複製，或將現有的圖表檔案拖曳至其他模型專案或方案中其他位置。 這會造成所複製圖表中的項目消失，或在開啟圖表時發生錯誤。 您必須從其中所建立的模型專案中開啟圖表。 這是因為 UML 圖表是其模型專案所擁有的模型檢視。 若要複製圖表檔案，請建立新的圖表，然後將來源圖表中的項目複製到新的圖表。 如需詳細資訊，請參閱[疑難排解模型專案和圖表](#TroubleshootingModelingProjects)。

#### <a name="to-create-a-blank-modeling-project"></a>建立空白模型專案

1. 在 [檔案] **Deploying Office Solutions** 功能表中，指向 [新增]，然後按一下 [專案]。

2. 在 [新增專案] 對話方塊中，於 [已安裝的範本] 之下，按一下 [模型專案]。

3. 在中間視窗中，按一下 [模型專案]。

4. 在 [名稱] 方塊中為專案命名，並在 [位置] 方塊中指定位置。

5. 在 [方案] 方塊中，選取 [加入至方案] 以將新專案加入至您已開啟的方案；或 [建立新的方案] 以關閉任何開啟的方案，並將專案加入至新的方案。

## <a name="RemovingModelingDiagrams"></a>從專案中移除模型圖表
 您可以永久刪除圖表，或可以暫時從專案排除圖表再加以還原。

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>永久刪除專案中的圖表

- 在 [方案總管] 中，以滑鼠右鍵按一下代表圖表的主要檔案，然後按一下 [刪除]。

     圖表會從專案和檔案系統中移除。 圖表中顯示的項目並不會從 [UML 模型總管] 中移除。

    > [!NOTE]
    > 每個圖表都有兩個檔案，其中一個附屬於另一個之下。 例如，如果您具有名稱為 `CD1` 的元件圖表，您應該刪除名為 `CD1.componentdiagram` 的檔案。 名為 `CD1.componentdiagram.layout` 的附屬檔案會自動刪除。

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>暫時從專案排除圖表

- 在 [方案總管] 中，以滑鼠右鍵按一下圖表檔案，然後按一下 [從專案中排除]。

     圖表隨即從專案中移除。 它並不會從檔案系統中移除。

    > [!NOTE]
    > 圖表中顯示的項目並不會從 [UML 模型總管] 中移除。

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>將暫時排除的圖表還原至專案

1. 在 [方案總管] 中，按一下模型專案節點。

    > [!NOTE]
    > 模型專案包含一個名為 [模型定義] 的模型定義資料夾。

2. 在 [**專案**] 功能表上，按一下 [**加入現有項目**]。

3. 在 [**加入現有專案**] 對話方塊中，找出圖表檔案，選取檔案，然後按一下 [**新增**]。

     模型圖表隨即開啟，並出現在模型專案中。

    > [!NOTE]
    > 每個圖表都會在檔案系統中有一組檔案。 請勿選取副檔名為 `.layout` 的檔案。 此外，Visual Studio 並不支援將現有的 UML 圖表加入多個模型專案。 每個圖表檔案都必須在其中所建立的模型專案內開啟。 這是因為 UML 圖表會顯示其模型專案所擁有的模型檢視。

## <a name="NonModelDiagrams"></a>不需要模型專案的圖表
 下列類型的圖表並不屬於模型專案：

- 建立為原始程式碼檢視的類別圖表。 這些與 UML 類別圖表並不相關。 如需詳細資訊，請參閱[設計和檢視類別與類型](../ide/designing-and-viewing-classes-and-types.md)。

- Code Map。 請參閱[對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)。

- 非 UML 圖表或圖層圖表的圖表，例如網域特定語言的圖表。

## <a name="TroubleshootingModelingProjects"></a>疑難排解模型專案和圖表
 下表描述模型專案或圖表會發生的問題以及解決方式：

|**問題**|**都會**|**解決方法**|
|---------------|----------------|--------------------|
|無法開啟或載入至方案的模型專案。<br /><br /> 畫面顯示下列訊息：<br /><br /> 「方案中的一個或多個專案未正確載入。 如需詳細資訊，請參閱 [輸出] 視窗。」<br /><br /> [輸出] 視窗會顯示下列訊息：<br /><br /> 「*ModelingProjectFilenameAndPath*.modelproj: 錯誤：無法識別的 GUID 格式。」|模型專案具有相同名稱且位於相同方案中專案的參考。<br /><br /> 例如，圖層會連結至具有相同名稱且位於相同方案中的專案。|使用文字編輯器來開啟模型專案檔案，接著移除參考，然後再次嘗試開啟模型專案。<br /><br /> 若要避免這個問題，請勿加入具有相同名稱的專案參考。 確定專案具有唯一名稱。|
|已加入、複製或拖曳至其他模型專案或方案中其他位置的圖表，其中項目已遺失。<br /><br /> -或-<br /><br /> 在嘗試開啟圖表時，會顯示下列訊息：<br /><br /> -「因為圖表中的某些圖形或連接器的定義不存在於此專案中，所以其已遺失。 可能是在關閉圖表時從模型中刪除了定義，或是已將圖表複製到另一個不包含這些定義的專案。<br /><br /> -或-<br /><br /> -「此檔由另一個專案開啟。」|圖表檔案已從模型專案加入、拖曳，或複製至其他模型專案或方案中其他位置。|若要複製圖表檔案，請建立新的圖表，然後將來源圖表中的項目複製到新的圖表。|

## <a name="see-also"></a>另請參閱
 [編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)[結構您的模型化方案](../modeling/structure-your-modeling-solution.md)
