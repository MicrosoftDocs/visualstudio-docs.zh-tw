---
title: 有向圖形標記語言 (DGML) 參考 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc3e4ae7-60fa-4e22-9227-98020b480b73
caps.latest.revision: 10
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: a8059d30a5fddf29e7e20f3cb0e87d6da35e72ea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491596"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>有向圖形標記語言 (DGML) 參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[有向圖形標記語言 (DGML) 參考](https://docs.microsoft.com/visualstudio/modeling/directed-graph-markup-language-dgml-reference)。  
  
有向圖形標記語言 (DGML) 描述用於視覺化以及執行複雜度分析的資訊，而且是用來在 Visual Studio 中保存 Code Map 的格式。 它使用簡單的 XML 來描述循環與非循環的有向圖形。 有向圖形是一組用連結或邊緣相連的節點。 節點和連結可用來表示網路結構，例如軟體專案中的項目。  
  
 請注意，某些版本的 Visual Studio 只支援一部分的 DGML 功能，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
> [!NOTE]
>  當您編輯 .dgml 檔案時，IntelliSense 會協助您識別每個項目的可用屬性和其值。 若要以屬性指定色彩，請使用常見色彩名稱 (例如 "Blue") 或 ARGB 十六進位值 (例如 "#ffa0b1c3")。 DGML 使用一小部分的 Windows Presentation Foundation (WPF) 色彩定義格式。 如需詳細資訊，請參閱 <<c0> [ 色彩類別](http://go.microsoft.com/fwlink/?LinkId=182345)。  
  
##  <a name="DGML"></a> DGML 語法  
 下表說明 DGML 中所使用的項目種類：  
  
-   `<DirectedGraph></DirectedGraph>`  
  
     這個項目是 Code Map (.dgml) 文件的根項目。 其他所有 DGML 項目都會出現在這個項目的範圍內。  
  
     下列清單說明您可以加入的選擇性屬性：  
  
     `Background` - 地圖背景的色彩  
  
     `BackgroundImage` - 要做為地圖背景之影像檔的位置。  
  
     `GraphDirection` - 在地圖設定為樹狀配置 (`Sugiyama`) 時排列節點，使大部分的連結能夠朝指定的方向排列：`TopToBottom`、`BottomToTop`、`LeftToRight` 或 `RightToLeft`。 請參閱[變更對應配置](../modeling/browse-and-rearrange-code-maps.md#Selecting)。  
  
     `Layout` - 將地圖設定為下列配置：`None`、`Sugiyama` (樹狀配置)、`ForceDirected` (快速叢集) 或 `DependencyMatrix`。 請參閱[變更對應配置](../modeling/browse-and-rearrange-code-maps.md#Selecting)。  
  
     `NeighborhoodDistance` - 在地圖設定為樹狀配置或快速叢集配置時，僅顯示距所選節點在指定連結數量 (1-7) 之遠的連結。 請參閱[變更對應配置](../modeling/browse-and-rearrange-code-maps.md#Selecting)。  
  
     範例：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
       <Nodes>  
          ...  
       </Nodes>  
       <Links>  
          ...  
       </Links>  
       <Categories>  
          ...  
       </Categories>  
       <Properties>  
          ...  
       </Properties>  
    </DirectedGraph>  
    ```  
  
-   `<Nodes></Nodes>`  
  
     此選擇性項目包含 `<Node/>` 項目的清單，用以定義地圖上的節點。 如需詳細資訊，請參閱 `<Node/>` 項目。  
  
    > [!NOTE]
    >  當您在 `<Link/>` 項目中參考未定義的節點時，地圖會自動建立 `<Node/>` 項目。  
  
     範例：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
       <Nodes>  
          <Node ... />  
       </Nodes>  
       <Links>  
          <Link ... />  
       </Links>  
    </DirectedGraph>  
    ```  
  
-   `<Node/>`  
  
     這個項目會定義單一節點。 它會出現在 `<Nodes><Nodes/>` 項目清單內。  
  
     這個項目必須包括下列屬性：  
  
     `Id` - 節點的唯一名稱以及 `Label` 屬性的預設值 (如果未指定個別的 `Label` 屬性)。 此名稱必須符合參考該節點之連結的 `Source` 或 `Target` 屬性。  
  
     下列清單會描述一些您可以加入的選擇性屬性：  
  
     `Label` -的顯示名稱的節點。  
  
     樣式屬性。 請參閱 [藉由編輯 DGML 檔案自訂 Code Map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)。  
  
     `Category` - 分類的名稱，這個分類識別共用此屬性的項目。 如需詳細資訊，請參閱 `<Category/>` 項目。  
  
     `Property` - 屬性的名稱，這個屬性識別具有相同屬性值的項目。 如需詳細資訊，請參閱 `<Property/>` 項目。  
  
     `Group` - 如果節點中包含其他節點，請將此屬性設定為 `Expanded` 或 `Collapsed`，以顯示或隱藏其內容。 此時必須要有 `<Link/>` 項目，用以加入 `Category="Contains"` 屬性，以及將父節點指定為來源節點，將子節點指定為目標節點。 請參閱[程式碼項目分組](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes)。  
  
     `Visibility` - 請將此屬性設為 `Visible`、`Hidden` 或 `Collapsed`。 使用`System.Windows.Visibility`。 請參閱[隱藏或顯示節點和連結](../modeling/browse-and-rearrange-code-maps.md#HidingShowing)。  
  
     `Reference` - 請將此屬性設為連結到文件或 URL。 請參閱[文件或 Url 連結至程式碼項目和連結](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences)。  
  
     範例：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
       <Nodes>  
          <Node Id="Driver" Label="Student" Category="Person" />  
          <Node Id="Passenger" Label="Instructor" Category="Person" />  
          <Node Id="Car" Label="Car" Category="Automobile" />  
          <Node Id="Truck" Label="Truck" Category="Automobile" />  
       </Nodes>  
       <Links>  
          <Link ... />  
       </Links>  
       <Categories>  
          <Category Id="Person" Background="Orange" />  
          <Category Id="Automobile" Background="Yellow"/>  
       </Categories>  
    </DirectedGraph>  
    ```  
  
-   `<Links></Links>`  
  
     這個項目包含 `<Link>` 項目的清單，可用以定義節點之間的連結。 如需詳細資訊，請參閱 `<Link/>` 項目。  
  
     範例：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
       <Links>  
          <Link ... />  
       </Links>  
    </DirectedGraph>  
    ```  
  
-   `<Link/>`  
  
     這個項目定義將來源節點連接至目標節點的單一連結。 它會出現在 `<Links></Links>` 項目清單內。  
  
    > [!NOTE]
    >  如果這個項目參考未定義的節點，地圖文件會自動建立具有指定屬性 (如有指定的話) 的節點。  
  
     這個項目必須包括下列屬性：  
  
     `Source` - 連結的來源節點  
  
     `Target` - 連結的目標節點  
  
     下列清單會描述一些您可以加入的選擇性屬性：  
  
     `Label` - 連結的顯示名稱  
  
     樣式屬性。 請參閱 [藉由編輯 DGML 檔案自訂 Code Map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)。  
  
     `Category` - 分類的名稱，這個分類識別共用此屬性的項目。 如需詳細資訊，請參閱 `<Category/>` 項目。  
  
     `Property` - 屬性的名稱，這個屬性識別具有相同屬性值的項目。 如需詳細資訊，請參閱 `<Property/>` 項目。  
  
     範例：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
       <Nodes>  
          <Node Id="Driver" Label="Student" Category="Person" />  
          <Node Id="Passenger" Label="Instructor" Category="Person" />  
          <Node Id="Car" Label="Car" Category="Automobile" />  
          <Node Id="Truck" Label="Truck" Category="Automobile" />  
       </Nodes>  
       <Links>  
          <Category Id="Person" Background="Orange" />  
          <Category Id="Automobile" Background="Yellow"/>  
          <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />  
          <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />  
       </Links>  
    </DirectedGraph>  
    ```  
  
-   `<Categories></Categories>`  
  
     這個項目包含 `<Category/>` 項目的清單。 如需詳細資訊，請參閱 `<Category/>` 項目。  
  
     範例：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
       <Categories>  
           <Category ... />  
       </Categories>  
    </DirectedGraph>  
    ```  
  
-   `<Category/>`  
  
     這個項目定義 `Category` 屬性，用以識別共用此屬性的項目。 `Category` 屬性可用以組織地圖項目、提供可繼承的共用屬性，或定義其他中繼資料。  
  
     這個項目必須包括下列屬性：  
  
     `Id` - 分類的唯一名稱以及 `Label` 屬性的預設值 (如果未指定個別的 `Label` 屬性)。  
  
     下列清單會描述一些您可以加入的選擇性屬性：  
  
     `Label` - 方便讀者理解的分類名稱。  
  
     `BasedOn` - 目前項目的 `<Category/>` 所繼承自的父分類。  
  
     在這個項目的範例中，`FailedTest` 分類會從 `Stroke` 分類繼承 `PassedTest` 屬性。 請參閱 < 建立階層式分類 」[藉由編輯 DGML 檔案自訂 code map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)。  
  
     分類也提供一些基本的範本行為，用以控制節點和連結顯示於地圖時的外觀。 請參閱 [藉由編輯 DGML 檔案自訂 Code Map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)。  
  
     範例：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
       <Nodes>  
          <Node Id="Driver" Label="Driver" Category="Person" />  
          <Node Id="Car" Label="Car" Category="Automobile" />  
          <Node Id="Truck" Label="Truck" Category="Automobile" />  
          <Node Id="Passenger" Category="Person" />  
       </Nodes>  
       <Links>  
          <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />  
          <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />  
       </Links>  
       <Categories>  
          <Category Id="Person" Background="Orange" />  
          <Category Id="Automobile" Background="Yellow"/>  
          <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />  
          <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />  
       </Categories>  
    </DirectedGraph>  
    ```  
  
-   `<Properties></Properties>`  
  
     這個項目包含 `<Property/>` 項目的清單。 如需詳細資訊，請參閱 `<Property/>` 項目。  
  
     範例：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
       <Properties>  
           <Property ... />  
       </Properties>  
    </DirectedGraph>  
    ```  
  
-   `<Property/>`  
  
     這個項目定義 `Property` 屬性 (Attribute)，供您指派值給任何 DGML 項目或屬性 (Attribute)，包括分類和其他屬性 (Property) 在內。  
  
     這個項目必須包括下列屬性：  
  
    -   `Id` - 屬性 (Property) 的唯一名稱以及 `Label` 屬性 (Attribute) 的預設值 (如果未指定個別的 `Label` 屬性 (Attribute))。  
  
    -   `DataType` - 屬性所儲存的資料類型  
  
     如果您想要出現在屬性**屬性**視窗中，使用`Label`屬性來指定屬性的顯示名稱。  
  
     請參閱[指派分類給程式碼項目和連結](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories)。  
  
     範例：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
       <Nodes>  
          <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>  
          <Node Id="Car" Label="Car" Category="Automobile" />  
          <Node Id="Truck" Label="Truck" Category="Automobile" />  
          <Node Id="Passenger" Category="Person" />  
       </Nodes>  
       <Links>  
          <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />  
          <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />  
       </Links>  
       <Categories>  
          <Category Id="Person" Background="Orange" />  
          <Category Id="Automobile" Background="Yellow"/>  
          <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />  
          <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />  
       </Categories>  
       <Properties>  
           <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />  
       </Properties>  
    </DirectedGraph>  
    ```  
  
###  <a name="AddAlias"></a> 常用路徑的別名  
 以別名取代常用路徑，有助於縮減 .dgml 檔案的大小以及載入或儲存檔案所需的時間。 若要建立別名，請在 .dgml 檔案的結尾加入 `<Paths></Paths>` 區段。 在這個區段加入 `<Path/>` 項目，以定義路徑的別名：  
  
```xml  
<Paths>  
   <Path Id="MyPathAlias" Value="C:\...\..." />  
</Paths>  
```  
  
 若要從.dgml 檔案中的項目參考別名，請將`Id`的\<路徑 / > 項目以貨幣符號 （$） 和括號 （（））：  
  
```xml  
<Nodes>  
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />  
</Nodes>  
<Properties>  
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />  
</Properties>  
```  
  
## <a name="see-also"></a>另請參閱  
 [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)   
 [使用 code map 偵錯應用程式](../modeling/use-code-maps-to-debug-your-applications.md)   
 [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)



