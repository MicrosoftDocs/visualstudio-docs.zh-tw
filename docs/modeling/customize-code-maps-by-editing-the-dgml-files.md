---
title: Customize code maps by editing the DGML files
description: 瞭解如何藉由編輯程式碼對應的有向圖形標記語言 ( .dgml) 檔案來自訂。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b7c94834aeb6aa82efdb53dead97e26daa667c0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389484"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Customize code maps by editing the DGML files

若要自訂 code map，您可以編輯其有向圖形標記語言 ( .dgml) 檔。 例如，您可以編輯項目來指定自訂樣式、指派節點和連結的屬性與分類，或將文件或 URL 連結至程式碼項目或連結。 如需 DGML 專案的詳細資訊，請參閱 [導向圖形標記語言 (dgml) 參考](../modeling/directed-graph-markup-language-dgml-reference.md)。

在文字或 XML 編輯器中編輯 Code Map 的 .dgml 檔案。 如果地圖是 Visual Studio 解決方案的一部分，請在 **方案總管** 中加以選取、開啟快捷方式功能表，然後選擇 [ **開啟方式**]、[ **XML (文字) 編輯器**]。

> [!NOTE]
> 若要建立 code map，您必須有 Visual Studio Enterprise 版。 當您在 Visual Studio 中編輯 Code Map 時，它會在您儲存此 .dgml 檔案時刪除任何未使用的 DGML 項目和屬性，藉此予以清除。 它也會在您手動加入新的連結時自動建立程式碼項目。 當您儲存 .dgml 檔案時，任何加入至項目的屬性可能會自行按照字母順序重新排列。

## <a name="group-code-elements"></a><a name="OrganizeNodes"></a> 分組程式碼元素
 您可以加入新的群組，或將現有的節點轉換成群組。

1. 在文字或 XML 編輯器中開啟此 .dgml 檔案。

2. 若要將程式碼項目轉換成群組，請找出該程式碼項目的 `<Node/>` 項目。

    \- 或 -

    若要加入新的群組，請找出 `<Nodes>` 區段。 加入新的 `<Node/>` 項目。

3. 在 `<Node/>` 項目中加入 `Group` 屬性，指定群組呈現為展開或摺疊的狀態。 例如：

   ```xml
   <Nodes>
      <Node Id="MyFirstGroup" Group="Expanded" />
      <Node Id="MySecondGroup" Group="Collapsed" />
   </Nodes>
   ```

4. 在 `<Links>` 區段中，針對群組程式碼項目與其子程式碼項目之間的每一個關聯性，確定其中存在具有下列屬性的 `<Link/>` 項目：

   - `Source` 屬性，指定群組程式碼項目

   - `Target` 屬性，指定子程式碼項目

   - `Category` 屬性，指定群組程式碼項目與其子程式碼項目之間的 `Contains` 關聯性

     例如：

   ```xml
   <Links>
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
   </Links>
   ```

    如需屬性的詳細資訊 `Category` ，請參閱 [指派分類給程式碼專案和連結](#AssignCategories)。

## <a name="change-the-style-of-the-map"></a><a name="ChangeGraphStyle"></a> 變更地圖的樣式
 您可以編輯此對應的 .dgml 檔案，變更圖形的背景色彩和框線色彩。 若要變更程式碼專案和連結的樣式，請參閱 [變更程式碼元素和連結的樣式](#Highlight)。

1. 在文字或 XML 編輯器中開啟此 .dgml 檔案。

2. 在 `<DirectedGraph>` 項目中，加入下列任何屬性以變更其樣式：

     背景色彩

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     框線色彩

    ```xml
    Stroke="StrokeValue"
    ```

     例如：

    ```xml
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >
       ...
       ...
    </DirectedGraph>
    ```

## <a name="change-the-style-of-code-elements-and-links"></a><a name="Highlight"></a> 變更程式碼專案和連結的樣式

### <a name="CreateCustomStyles"></a>
 您可以將自訂樣式套用至下列程式碼項目：

- 單一程式碼項目和連結

- 程式碼項目和連結的群組

- 根據特定條件組成的程式碼項目和連結群組

> [!TIP]
> 如果您在許多不同的程式碼項目或連結之間使用了重覆的樣式，您可能可以考慮套用一個分類到那些程式碼項目或連結，然後將樣式套用到該分類。 如需詳細資訊，請參閱 [指派分類給程式碼專案和連結](#AssignCategories) ，以及 [將屬性指派給程式碼專案和連結](#AssignProperties)。

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>將自訂樣式套用至單一程式碼項目

1. 在文字或 XML 編輯器中開啟此 .dgml 檔案。

2. 請找出此程式碼項目的 `<Node/>` 項目。 加入下列任一屬性以自訂其樣式：

     背景色彩

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     外框

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     外框粗細

    ```xml
    StrokeThickness="StrokeValue"
    ```

     文字色彩

    ```xml
    Foreground="ColorNameOrHexadecimalValue"
    ```

     圖示

    ```xml
    Icon="IconFilePathLocation"
    ```

     文字大小

    ```xml
    FontSize="FontSizeValue"
    ```

     文字類型

    ```xml
    FontFamily="FontFamilyName"
    ```

     文字粗細

    ```xml
    FontWeight="FontWeightValue"
    ```

     文字樣式

    ```xml
    FontStyle="FontStyleName"
    ```

     例如，您可以指定 `Italic` 做為文字樣式。

     紋理

    ```xml
    Style="Glass"
    ```

     - 或 -

    ```xml
    Style="Plain"
    ```

     形狀

     若要以圖示取代圖形，請將 `Shape` 屬性設定為 `None`，並將 `Icon` 屬性設定為圖示檔案的路徑。

    ```xml
    Shape="ShapeFilePathLocation"
    ```

     例如：

    ```xml
    <Nodes>
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>
    </Nodes>
    ```

##### <a name="to-apply-a-custom-style-to-a-single-link"></a>若要將自訂樣式套用至單一連結

1. 在文字或 XML 編輯器中開啟此 .dgml 檔案。

2. 找出同時包含來源程式碼項目與目標程式碼項目名稱的 `<Link/>` 項目。

3. 在 `<Link/>` 項目中，加入下列任何屬性以自訂其樣式：

     外框和箭頭色彩

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     外框粗細

    ```xml
    StrokeThickness="StrokeValue"
    ```

     外框樣式

    ```xml
    StrokeDashArray="StrokeArrayValues"
    ```

     例如：

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>
    </Links>
    ```

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>將自訂樣式套用至程式碼項目或連結的群組

1. 在文字或 XML 編輯器中開啟此 .dgml 檔案。

2. 如果 `<Styles></Styles>` 項目不存在，請在 `<DirectedGraph></DirectedGraph>` 項目之後的 `<Links></Links>` 項目底下加入該項目。

3. 在 `<Styles></Styles>` 項目中的 `<Style/>` 項目底下，指定下列屬性：

   - `TargetType="Node` &#124; `Link | Graph"`

   - `GroupLabel="`*NameInLegendBox*`"`

   - `ValueLabel="`*NameInStylePickerBox*`"`

     若要將自訂樣式套用至所有目標類型，請勿使用條件。

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>將條件式樣式套用至程式碼項目或連結的群組

1. 在文字或 XML 編輯器中開啟此 .dgml 檔案。

2. 在 `<Style/>` 項目中加入包含 `<Condition/>` 屬性的 `Expression` 項目，以指定傳回布林值的運算式。

    例如：

   ```xml
   <Condition Expression="MyCategory"/>
   ```

    - 或 -

   ```xml
   <Condition Expression="MyCategory > 100"/>
   ```

    - 或 -

   ```xml
   <Condition Expression="HasCategory('MyCategory')"/>
   ```

    這個運算式會使用下列 Backus-Naur 格式 (BNF) 語法：

    \<Expression> ：： = \<BinaryExpression> &#124; \<UnaryExpression> &#124; " (" \<Expression> ") " &#124; \<MemberBindings> \<Literal> &#124; &#124; \<Number>

    \<BinaryExpression>::= \<Expression> \<Operator>\<Expression>

    \<UnaryExpression> ::= "!" \<Expression> &#124; "+" \<Expression> &#124; "-" \<Expression>

    \<Operator> ：： = "<" &#124; " \<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "！ =" &#124; "或" &#124; "和" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

    \<MemberBindings> ：： = \<MemberBindings> &#124; \<MemberBinding> "." \<MemberBinding>

    \<MemberBinding> ：： = \<MethodCall> &#124; \<PropertyGet>

    \<MethodCall> ：： = \<Identifier> " (" \<MethodArgs> ") "

    \<PropertyGet> ：： = 識別碼

    \<MethodArgs> ：： = \<Expression> &#124; \<Expression> "，" \<MethodArgs> &#124; \<empty>

    \<Identifier> ::= [^. ]*

    \<Literal> ：： = 單引號或雙引號括住的字串常值

    \<Number> ：： = 具有選用小數點的數位字串

    您可以指定多個 `<Condition/>` 元素，這些元素必須全部為 true 才能套用樣式。

3. 在 `<Condition/>` 項目的下一行加入一個或多個 `<Setter/>` 項目來指定 `Property` 屬性與固定的 `Value` 屬性，或加入計算的 `Expression` 屬性，以套用至符合條件的對應、程式碼項目或連結。

    例如：

   ```xml
   <Setter Property="BackGround" Value="Green"/>
   ```

   下列條件是一個簡單的完整範例，它會指定讓程式碼項目根據其 `Passed` 分類是設為 `True` 還是 `False` 來顯示為綠色或紅色：

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
   <Nodes>
      <Node Id="MyFirstNode" Passed="True" />
      <Node Id="MySecondNode" Passed="False" />
   </Nodes>
   <Links>
   </Links>
   <Styles>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">
         <Condition Expression="Passed='True'"/>
         <Setter Property="Background" Value="Green"/>
      </Style>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">
         <Condition Expression="Passed='False'"/>
         <Setter Property="Background" Value="Red"/>
      </Style>
   </Styles>
</DirectedGraph>
```

 下表包含一些您可以使用的範例條件：

 將字型大小設定成以程式碼行數為參數的函式，而此函式同時也會變更程式碼項目的大小。 這個範例會使用單一條件運算式來設定多個屬性，亦即 `FontSize` 和 `FontFamily`。

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" LinesOfCode ="200" />
   <Node Id="Class2" LinesOfCode ="1000" />
   <Node Id="Class3" LinesOfCode ="20" />
</Nodes>
<Properties>
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">
      <Condition Expression="LinesOfCode > 0" />
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />
      <Setter Property="FontFamily" Value="Papyrus" />
   </Style>
</Styles>
</DirectedGraph>
```

 根據 `Coverage` 屬性設定程式碼項目的背景色彩。 與 `if-else` 陳述式類似，會依照樣式出現的順序來評估樣式。

 在此範例中：

1. 如果 `Coverage` > 80，請將屬性設定 `Background` 為綠色。

2. 否則如果 `Coverage` > 50，則會 `Background` 根據屬性的值，將屬性設定為橙色的網底 `Coverage` 。

3. 如果是上述所有條件以外的情況，則根據 `Background` 屬性值，將 `Coverage` 屬性設定為深淺程度不同的紅色。

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" Coverage="58" />
   <Node Id="Class2" Coverage="95" />
   <Node Id="Class3" Coverage="32" />
</Nodes>
<Properties>
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">
      <Condition Expression="Coverage > 80" />
      <Setter Property="Background" Value="Green" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">
      <Condition Expression="Coverage > 50" />
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />
   </Style>
</Styles>
</DirectedGraph>
```

 將 `Shape` 屬性設定為 `None`，讓圖示取代該圖案。 使用 `Icon` 屬性來指定圖示的位置。

```xml
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Automation" Category="Test" Label="Automation" />
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />
</Nodes>
<Categories>
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />
</Categories>
<Properties>
   <Property Id="Icon" DataType="System.String" />
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />
   <Property Id="Shape" DataType="System.String" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">
      <Condition Expression="HasCategory('Group')" />
      <Setter Property="Background" Value="#80008080" />
   </Style>
   <Style TargetType="Node">
      <Setter Property="HorizontalAlignment" Value="Center" />
   </Style>
</Styles>
</DirectedGraph>
```

## <a name="assign-properties-to-code-elements-and-links"></a><a name="AssignProperties"></a> 將屬性指派給程式碼專案和連結
 您可以指派屬性給程式碼項目和連結，對其組合管理。 例如，您可以選取具有特定屬性的程式碼項目，以便組成群組、變更樣式或予以隱藏。

#### <a name="to-assign-a-property-to-a-code-element"></a>將屬性指派給程式碼項目

1. 在文字或 XML 編輯器中開啟此 .dgml 檔案。

2. 找出該程式碼項目的 `<Node/>` 項目。 指定此屬性的名稱及值。 例如：

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3. 將 `<Property/>` 項目加入至 `<Properties>` 區段，以指定其顯示名稱和資料類型等屬性：

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>若要將屬性指派給連結

1. 在文字或 XML 編輯器中開啟此 .dgml 檔案。

2. 找出同時包含來源程式碼項目與目標程式碼項目名稱的 `<Link/>` 項目。

3. 在 `<Node/>` 項目中，指定屬性名稱及其值。 例如：

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4. 將 `<Property/>` 項目加入至 `<Properties>` 區段，以指定其顯示名稱和資料類型等屬性：

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

## <a name="assign-categories-to-code-elements-and-links"></a><a name="AssignCategories"></a> 將分類指派給程式碼專案和連結
 下列章節示範如何將分類指派給程式碼項目，藉以組合管理，並示範您可以如何建立階層式分類，幫助您使用繼承來組合管理程式碼項目和將屬性加入子分類。

#### <a name="to-assign-a-category-to-a-code-element"></a>將分類指派給程式碼項目

- 在文字或 XML 編輯器中開啟此 .dgml 檔案。

- 找出您要的程式碼項目之 `<Node/>` 項目。

- 在 `<Node/>` 項目中加入 `Category` 屬性，以指定分類的名稱。 例如：

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     將 `<Category/>` 項目加入至 `<Categories>` 區段，如此即可使用 `Label` 屬性來指定該分類的顯示文字：

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>若要將分類指派給連結

1. 在文字或 XML 編輯器中開啟此 .dgml 檔案。

2. 找出同時包含來源程式碼項目與目標程式碼項目名稱的 `<Link/>` 項目。

3. 在 `<Link/>` 項目中加入 `Category` 屬性，以指定分類的名稱。 例如：

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4. 將 `<Category/>` 項目加入至 `<Categories>` 區段，如此即可使用 `Label` 屬性來指定該分類的顯示文字：

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>若要建立階層式分類

1. 在文字或 XML 編輯器中開啟此 .dgml 檔案。

2. 加入父分類的 `<Category/>` 項目，然後將 `BasedOn` 屬性加入至子分類的 `<Category/>` 項目。

     例如：

    ```xml
    <Nodes>
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />
       <Node Id="MySecondNode" Label="My Second Node" />
    </Nodes>
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" />
    </Links>
    <Categories>
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>
    </Categories>
    ```

     在本範例中，`MyFirstNode` 的背景為綠色，這是因為其 `Category` 屬性繼承了 `Background` 的 `MyParentCategory` 屬性。

## <a name="link-documents-or-urls-to-code-elements-and-links"></a><a name="AddReferences"></a> 將檔或 Url 連結至程式碼專案和連結
 您可以編輯此對應的 .dgml 檔案，並將 `Reference` 屬性加入程式碼項目的 `<Node/>` 項目或連結的 `<Link/>` 項目，藉此將文件或 URL 連結至程式碼項目或連結。 然後，您就可以從程式碼項目或連結開啟和檢視該內容。 `Reference` 屬性會指定該內容的路徑。 此路徑可以是相對於 .dgml 檔案位置的路徑，或是絕對路徑。

> [!CAUTION]
> 如果您使用相對路徑，而且 .dgml 檔案已移動到不同的位置，那麼那些路徑將不再解析。 當您嘗試開啟和檢視連結的內容時，會發生表示內容無法檢視的錯誤。

 例如，您可能會想要連結下列程式碼項目：

- 若要描述類別的變更，您可能會將工作程式碼項目、文件或其他 .dgml 檔的 URL 連結到類別的程式碼項目。

- 您可能會將相依性圖表連結到代表軟體邏輯架構中之圖層的群組程式碼專案。

- 若要顯示會公開介面之元件的詳細資訊，您可能會將元件圖連結到該介面的程式碼項目。

- 將程式碼項目連結至 Team Foundation Server 工作項目或 Bug，或一些其他與程式碼項目相關的資訊。

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>將文件或 URL 連結到程式碼項目

1. 在文字或 XML 編輯器中開啟此 .dgml 檔案。

2. 找出您要的程式碼項目之 `<Node/>` 項目。

3. 執行下表的其中一項工作：

    單一程式碼項目

   - 在 `<Node/>` 或 `<Link/>` 項目中，加入 `Reference` 屬性以指定此程式碼項目的位置。

     > [!NOTE]
     > 每個項目只能有一個 `Reference` 屬性。

     例如：

   ```xml
   <Nodes>
      <Node Id="MyNode" Reference="MyDocument.txt" />
   </Nodes>
   <Properties>
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    多個程式碼項目

   1. 在 `<Node/>` 或 `<Link/>` 中加入新屬性，以指定每個參考的位置。

   2. 在 `<Properties>` 區段中：

      1. 針對每一個新的參考類型加入 `<Property/>` 項目。

      2. 將 `Id` 屬性設定為新參考屬性的名稱。

      3. 加入 `IsReference` 屬性並將它設定為， `True` 讓參考出現在程式碼專案的 [ **移至參考** ] 快捷方式功能表上。

      4. 您 `Label` 可以使用屬性來指定程式碼專案的 [ **移至參考** ] 快捷方式功能表上的顯示文字。

      例如：

   ```xml
   <Nodes>
      <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>
   </Nodes>
   <Properties>
      <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />
      <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    在此對應上，該程式碼項目名稱會顯示為加上底線。 當您開啟程式碼專案或連結的快捷方式功能表時，會看到 [ **移至參考** ] 快捷方式功能表，其中包含可供您選擇的連結程式代碼元素。

4. 使用 `ReferenceTemplate` 屬性來指定多個參考使用的共同字串 (例如 URL)，而不要在參考中重複設定該字串。

    `ReferenceTemplate` 屬性會指定參考之值的預留位置。 在下列範例中，`{0}` 屬性中的 `ReferenceTemplate` 預留位置將會由 `MyFirstReference` 項目中的 `MySecondReference` 及 `<Node/>` 屬性值取代，以產生完整路徑：

   ```xml
   <Nodes>
      <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>
      <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>
   </Nodes>
   <Properties>
      <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>
      <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>
   </Properties>
   ```

5. 若要檢視參考的程式碼項目或來自此對應的程式碼項目，請開啟該程式碼項目或連結的捷徑功能表。 選擇 [ **移至參考** ]，然後選擇 [程式碼] 元素。

## <a name="see-also"></a>另請參閱

- [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)
- [使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)
- [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)
- [有向圖形標記語言 (DGML) 參考](../modeling/directed-graph-markup-language-dgml-reference.md)
