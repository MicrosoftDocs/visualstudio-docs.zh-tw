---
title: 建立 C++ 物件的自訂檢視
description: 使用 Natvis 框架自訂 Visual Studio 在除錯器中顯示本機類型的方式
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8bdd8d26ba450b1aedd790d644c183607c44af
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224507"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>使用 Natvis 框架在除錯器中建立C++物件的自訂檢視

Visual Studio *Natvis*框架自訂本機類型在除錯器變數視窗(如 **"局部變數**"和 **「監視」** 視窗)和**數據提示**中顯示的方式。 Natvis 可視化可幫助使創建的類型在調試期間更加可見。

Natvis 用 XML 語法、更好的診斷、版本控制以及多個檔支援替換早期版本的 Visual Studio 中的*autoexp.dat*檔。

> [!NOTE]
> Natvis 自定義項使用類和結構,但不使用 typedefs。

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>納特維斯可視化

您可以使用 Natvis 框架為所建立的類型創建視覺化規則,以便開發人員在除錯期間可以更輕鬆地查看這些規則。

例如,下圖顯示了[Windows::UI::::Xaml::控制項::](/uwp/api/Windows.UI.Xaml.Controls.TextBox)在調試器視窗中的 TextBox 的變數,而不應用任何自定義可視化效果。

![TextBox 的預設視覺化](../debugger/media/dbg_natvis_textbox_default.png "TextBox 的預設視覺化")

反白顯示的資料列會顯示 `Text` 類別的 `TextBox` 屬性。 複雜的類層次結構使得很難找到此屬性。 除錯器不知道如何解釋自訂字串類型,因此您看不到文字框中持有的字串。

應用`TextBox`Natvis 自訂可視化工具規則時,在變數視窗中,同樣看起來要簡單得多。 類的重要成員一起顯示,除錯器顯示自訂字串類型的基礎字串值。

![使用視覺化檢視的 TextBox 資料](../debugger/media/dbg_natvis_textbox_visualizer.png "使用視覺化檢視的 TextBox 資料")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>在C++專案中使用 .natvis 檔案

Natvis 使用 *.natvis*檔案來指定可視化規則。 *.natvis*檔案是具有 *.natvis*副檔名的 XML 檔。 Natvis 架構在 *%VSINSTALLDIR%_Xml_Schemas_natvis.xsd 中*定義。

*.natvis*檔案的基本結構是表示可視化條目的`Type`一 個或多個元素。 每個`Type`元素的完全限定名稱`Name`在其 屬性中指定。

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio 在 *%VSINSTALLDIR%_Common7_Packages_除錯器_視覺化器*資料夾中提供了一些 *.natvis*檔案。 這些檔具有許多常見類型的可視化規則,並可用作為新類型的編寫可視化效果的範例。

### <a name="add-a-natvis-file-to-a-c-project"></a>將 .natvis 檔案加入C++專案

您可以將 *.natvis*檔案添加到任何C++專案。

**要添加新的 *.natvis*檔,**

1. 選擇**解決方案資源管理員**中的C++專案節點,然後選擇 **「專案** > **添加新項**」,或右鍵按一下**Add** > 專案並選擇「**添加新項**」。

1. 在「**新增新專案」** 對話方塊中,選擇**視覺C++** > **實用程式** > **調試器視覺化檔 (.natvis)。**

1. 命名檔案,然後選擇 **「添加」。**

   新檔將添加到**解決方案資源管理器**,並在可視化工作室文件窗格中打開。

Visual Studio 除錯器會自動在C++專案中載入 *.natvis*檔案,預設情況下,在生成專案時,還會將它們包括在 *.pdb*檔中。 如果除錯產生的應用,除錯器將從 *.pdb*檔載入 *.natvis*檔案,即使您沒有打開專案也是如此。 如果不希望 *.natvis*檔包含在 *.pdb*中,則可以將其從生成的 *.pdb*檔中排除。

**要從 *.pdb*中排除 *.natvis*檔案:**

1. 在**解決方案資源管理員**中選擇 *.natvis*檔案 ,然後選擇 **「屬性**」圖示,或右鍵按一下該檔並選擇 **「屬性**」 。

1. 下拉"**從生成中排除「** 旁邊的箭頭,然後選擇」**OK****確定**」。

>[!NOTE]
>對於調試可執行專案,請使用解決方案項添加不在 *.pdb*中的任何 *.natvis*文件,因為沒有C++專案可用。

>[!NOTE]
>從 *.pdb*載入的 Natvis 規則僅適用於 *.pdb*引用的模組中的類型。 例如,如果*Module1.pdb*`Test`具有名為的類型的 Natvis 條目,`Test`則它僅適用於模組*1.dll*中的類。 如果另一個模組也定義了名為`Test`的類,則*Module1.pdb* Natvis 條目不適用於它。

**要透過 VSIX 套件安裝和註冊 *.natvis*檔案,請執行:**

VSIX 套件可以安裝和註冊 *.natvis*檔案。 無論它們安裝在何處,所有已註冊的 *.natvis*文件都會在調試期間自動拾取。

1. 在 VSIX 套件中包括 *.natvis*檔案。 例如,對於以下項目檔:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. 在*來源.擴展.vsixmanifest*檔案中註冊 *.natvis*檔案:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>納特維斯檔案位置

如果希望 *.natvis*檔案應用於多個專案,則可以將 .natvis 檔案添加到使用者目錄或系統目錄中。

*.natvis*檔案按以下順序計算:

1. 任何 *.natvis*檔嵌入到要調試的 *.pdb*中,除非載入的專案中存在同名檔。

2. 載入C++專案或頂級解決方案中的任何 *.natvis*檔案。 此組包括所有載入C++專案(包括類庫),但不包括其他語言的專案。

3. 通過 VSIX 包安裝和註冊的任何 *.natvis*檔案。

::: moniker range="vs-2017"

4. 特定於使用者的 Natvis 目錄 (例如 *,%USERPROFILE% *文件_視覺工作室 2017 年_可視化工具*)。

::: moniker-end

::: moniker range=">= vs-2019"

4. 特定於使用者的 Natvis 目錄 (例如 *,%USERPROFILE% *文件_視覺工作室 2019 年_可視化工具*)。

::: moniker-end

5. 全系統 Natvis 目錄 (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*)。 此目錄具有與 Visual Studio 一起安裝的 *.natvis*檔案。 如果您有管理員許可權,則可以將檔案添加到此目錄。

## <a name="modify-natvis-files-while-debugging"></a>除錯時修改 .natvis 檔案

在除錯其專案時,可以在IDE中修改 *.natvis*檔。 在正在調試的 Visual Studio 的相同實例中打開該檔,對其進行修改並保存它。 儲存檔案後,「**監視」** 和 **「局部變數」** 視窗將立即更新以反映更改。

您還可以在正在調試的解決方案中添加或刪除 *.natvis*檔案,Visual Studio 會添加或刪除相關的可視化效果。

在除錯時,無法更新嵌入在 *.pdb*檔中的 *.natvis*檔案。

如果在 Visual Studio 外部修改 *.natvis*檔案,則更改不會自動生效。 要更新除錯器視窗,讓 **「立即」** 視窗中重新評估 **.natvisreload 命令**。 然後更改生效,而不會重新啟動調試會話。

還使用 **.natvisreload**命令將 *.natvis*檔案升級到較新版本。 例如 *,.natvis*檔可能會簽入原始程式碼管理,並且您希望選取其他人最近所做的更改。

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a>運算式和格式
Natvis 視覺化使用 C++ 運算式來指定要顯示的資料項目。 除了在[上下文中運算子 (C++)](../debugger/context-operator-cpp.md)中描述的除錯器中 C++表示式的增強和限制外,請注意以下事項:

- Natvis 運算式是在正在視覺化之物件的內容 (而非目前的堆疊框架) 中進行評估。 例如,`x`在 Natvis 表示式中,是指可視化物件中名為**x**的欄位,而不是目前的函數中名為**x**的局部變數。 您無法訪問 Natvis 表示式中的局部變數,儘管可以存取全域變數。

- Natvis 表示式不允許函數計算或副作用。 函數調用和賦值運算符將被忽略。 由於 [偵錯工具內建函式](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) 沒有副作用，因此可自由地從任何 Natvis 運算式加以呼叫，即使不允許其他函式呼叫亦然。

- 要控制表示式的顯示方式,可以使用[C++ 格式指定器中描述的](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)任何格式指定器。 當 Natvis 在內部使用條目時,格式指定符將被忽略`Size`,例如[ArrayItems 擴充](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)中的運算式。

## <a name="natvis-views"></a>Natvis 檢視

您可以定義不同的 Natvis 檢視以以不同的方式顯示類型。 例如,下面是定義名為`std::vector``simple`的 簡化視圖的可視化效果。 和`DisplayString``ArrayItems``simple`元素 顯示在預設檢視和檢視中,而和`[size]``[capacity]`項不顯示在`simple`檢視中。

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

在 **「監視」** 視窗中,使用 **、檢視**格式指定器指定備用檢視。 簡單檢視顯示為**vec,檢視(簡單)**:

![簡單檢視的監看式視窗](../debugger/media/watch-simpleview.png "簡單檢視的監看式視窗")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>納特維斯錯誤

當調試器在可視化條目中遇到錯誤時,它會忽略它們。 它要麼以原始形式顯示類型,要麼選擇另一個合適的可視化效果。 您可以使用 Natvis 診斷來瞭解除錯器忽略視覺化項目的原因,並查看基礎語法並分析錯誤。

**要開啟 Natvis 診斷:**

- 在**工具** > **選項**(或**除錯** > **選項**)>**除錯** > **輸出視窗**下,將**Natvis 診斷訊息(僅C++)** 設定為**錯誤**、**警告**或**詳細,** 然後選擇 **"確定**"。

錯誤將顯示在 **「輸出」** 視窗中。

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a>納特維斯語法參考

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> AutoVisualizer 項目
該`AutoVisualizer`元素是 *.natvis*檔案的根節點,並且`xmlns:`包含命名空間 屬性。

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

該`AutoVisualizer`元素可以具有[類型](#BKMK_Type)[、HResult、UI](#BKMK_HResult)[視覺化器](#BKMK_UIVisualizer)和[自訂可視化器](#BKMK_CustomVisualizer)子級。

### <a name="type-element"></a><a name="BKMK_Type"></a>類型元素

基本`Type`如下所示:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 這個`Type`元素指定:

1. 可視化效果應用於什麼類型(屬性`Name`)。

2. 該類型物件的值外觀應該為何 ( `DisplayString` 項目)。

3. 當使用者在變數視窗(`Expand`節點)中展開類型時,類型的成員應是什麼樣子。

#### <a name="templated-classes"></a>樣本化類
`Type`元素`Name`的屬性接受星號`*`作為通配符,可用於範本化類名稱。

在下面的範例中,無論對像是,`CAtlArray<int>``CAtlArray<float>`還是使用相同的可視化效果。 如果有特定的可視化條目,`CAtlArray<float>`則它優先於泛型。

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

可以使用宏$T1、$T2等來引用可視化條目中的範本參數。 要查找這些宏的範例,請參閱 Visual Studio 附帶的 *.natvis*檔案。

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a>視覺化工具類型符合
如果可視化條目無法驗證,則使用下一個可用的可視化效果。

#### <a name="inheritable-attribute"></a>Inheritable 屬性
可選`Inheritable`屬性指定可視化是僅適用於基類型,還是應用於基類型和所有派生類型。 `Inheritable` 的預設值為 `true`。

在以下範例中,視覺化效果僅適用於類型`BaseClass`:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priority 屬性

可選`Priority`屬性指定在定義無法解析時使用備用定義的順序。 的可能`Priority`值是`Low`: `MediumLow``Medium` `MediumHigh`、`High`、 、 和 。 預設值是 `Medium`。 該`Priority`屬性僅區分同一 *.natvis*檔案中的優先順序。

下面的範例首先分析與 2015 STL 匹配的條目。 如果無法解析,它將使用 2013 版 STL 的備用條目:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Optional 屬性
您可以將屬性`Optional`放在任何節點上。 如果可選節點內的子表達式無法解析,調試器將忽略該節點,但應用`Type`規則的其餘部分。 在下列類型中， `[State]` 是非選擇性的，但 `[Exception]` 是選擇性的。  如果`MyNamespace::MyClass`出現名為`M_exceptionHolder`* 的`[State]`欄位,`[Exception]`則節點和 節點`_M_exceptionHolder`都會出現,但如果沒有`[State]`欄位,則只顯示節點。

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Condition 屬性

可選`Condition`屬性可用於許多可視化元素,並指定何時使用可視化規則。 如果條件屬性中的表達式解析為`false`,則可視化規則不適用。 如果它計算到`true`,或者`Condition`沒有 屬性,則應用可視化效果。 可以在可視化條目中使用此屬性作為if-else邏輯。

例如,以下可視化效果具有智慧指標`DisplayString`類型的兩個元素。 當`_Myptr`成員為空時,第一個`DisplayString`元素的條件解析`true`為 ,以便窗體顯示。 當`_Myptr`成員不為空時,條件將計算為`false`,第`DisplayString`二 個元素將顯示。

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>IncludeView 和 ExcludeView 屬性

`IncludeView`和`ExcludeView`屬性指定要在特定檢視中顯示或不顯示的元素。 例如,在下面的 Natvis`std::vector`規範`simple`中, 視圖`[size]``[capacity]`不顯示和項。

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

您可以在類型和單個`IncludeView``ExcludeView`成員上使用和 屬性。

### <a name="version-element"></a><a name="BKMK_Versioning"></a>版本項目
元素`Version`將可視化條目範圍限定為特定模組和版本。 該`Version`元素有助於避免名稱衝突,減少意外不匹配,並允許針對不同類型版本進行不同的可視化。

如果由不同模組使用的常見標頭檔定義了類型,則僅在類型位於指定的模組版本中時才會顯示版本化可視化。

在下面的示例中,可視化僅適用於`DirectUI::Border``Windows.UI.Xaml.dll`從版本 1.0 到 1.5 中找到的類型。

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

你不需要兩者兼`Min` `Max` 。 它們是可選屬性。 不支援通配符。

該`Name`屬性在格式*檔名.ext*中,如*hello.exe*或*某些.dll*。 不允許路徑名稱。

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>顯示字串元素
這個`DisplayString`元素指定要顯示為變數值的字串。 它接受與運算式混合的任意字串。 大括號內的所有項目都會解譯為運算式。 例如,以下`DisplayString`項目:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

表示類型`CPoint`變數顯示如下圖所示:

 ![使用顯示字串元素](../debugger/media/dbg_natvis_cpoint_displaystring.png "使用顯示字串元素")

在表示式`DisplayString`中,`x``y`和,`CPoint`是的成員, 位於大括弧內, 因此計算其值。 該示例還演示如何使用雙大括弧(`{{``}}`或 ) 來轉義大括弧。

> [!NOTE]
> `DisplayString` 項目是接受任意字串和大括號語法的唯一項目。 所有其他可視化元素僅接受調試器可以計算的運算式。

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>字串檢視元素

該`StringView`元素定義除錯器可以發送到內建文字可視化工具的值。 例如,給定`ATL::CStringT`以下類型的視覺化效果:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

物件`CStringT`顯示在變數視窗中,如下所示:

![CStringT 的 DisplayString 項目](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT 的 DisplayString 項目")

添加`StringView`元素告訴除錯器它可以將值顯示為文本可視化。

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

在除錯期間,您可以選擇變數旁邊的放大鏡圖示,然後選擇 **「文本可視化器**」以顯示**m_pszData**指向的字串。

 ![含有 StringView 視覺化檢視的 CStringT 資料](../debugger/media/dbg_natvis_stringview_cstringt.png "含有 StringView 視覺化檢視的 CStringT 資料")

該表示式`{m_pszData,su}`包括 C++格式指定器**su,** 以將該值顯示為 Unicode 字串。 關於詳細資訊,請參閱[C++ 的格式指定器](../debugger/format-specifiers-in-cpp.md)。

### <a name="expand-element"></a><a name="BKMK_Expand"></a>展開元素

在變數`Expand`視窗中展開類型時,可選節點自定義可視化類型的子節點。 節點`Expand`接受定義子元素的子節點的清單。

- 如果在可視化`Expand`條目中未指定節點,則子級使用預設擴展規則。

- `Expand`如果指定了節點,並且沒有子節點,則該類型在調試器視窗中不可擴展。

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a>專案延伸

 該`Item`元素`Expand`是節點中最基本和最常見的元素。 `Item` 定義單一子項目。 例如,具有欄位`CRect``top``left`的類、`right``bottom`具有以下可視化項目:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

在除錯器視窗中,`CRect`類型如下所示:

![含有 Item 項目展開的 CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "含有 Item 項目展開的 CRect")

除錯器計算與`Width``Height`元素中指定的運算式,並顯示變數**視窗的「值」** 欄中的值。

除錯器會自動為每個自訂擴展**創建 [原始檢視]** 節點。 前面的螢幕截圖顯示展開的 **[原始檢視]** 節點,以顯示物件的預設原始視圖與其 Natvis 可視化有何不同。 默認擴展為基類創建一個子樹,並將基類的所有數據成員列為子級。

> [!NOTE]
> 如果項目的表示式指向複雜類型,**則 Item**節點本身是可展開的。

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a>陣列項目延伸
使用 `ArrayItems` 節點，讓 Visual Studio 偵錯工具將類型解譯為陣列並顯示其個別項目。 `std::vector` 的視覺化即為一個好例子：

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

當在變數視窗中展開時， `std::vector` 會顯示其個別項目：

![使用 ArrayItems 展開的 std::vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "使用 ArrayItems 展開的 std::vector")

節點`ArrayItems`必須具有:

- 可讓偵錯工具了解陣列長度的 `Size` 運算式 (必須評估為整數)。
- 指向`ValuePointer`第一個元素的運算式(它必須不是 元素類型的`void*`指標)。

該陣列的下限預設值為 0。 要重寫該值,請使用元素`LowerBound`。 與 Visual Studio 一起附帶的 *.natvis*檔都有示例。

>[!NOTE]
>例如`[]``vector[i]`,可以將運算元用於使用`ArrayItems`的任何單維陣組可視化,即使類型本身(`CATLArray`例如 )不允許此運算符。

您還可以指定多維陣組。 在這種情況下,除錯器需要稍微多一些資訊才能正確顯示子元素:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction`指定陣列是按行主順序還是列主順序排列。
- `Rank` 指定陣列的陣序。
- `Size` 元素接受隱含的 `$i` 參數，並將參數取代為維度索引，以便在該維度中尋找陣列的長度。 在前面的示例中,表達式`_M_extent.M_base[0]`應給出第 0 個`_M_extent._M_base[1]`維度、 第 1 個維度等的長度。

以下是二維`Concurrency::array`物件在除錯器視窗中的外觀:

![具有陣列項目延伸的二維陣列](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "具有陣列項目延伸的二維陣列")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> IndexListItems 展開

僅當陣列元素`ArrayItems`連續在記憶體中佈局時,才能使用擴展。 調試器只需增加其指標即可到達下一個元素。 如果需要操作索引到值節點,請使用`IndexListItems`節點。 下面是具有節點的`IndexListItems`視覺化效果:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

之間的`ArrayItems``IndexListItems`唯一區別`ValueNode`是 , 它期望`$i`使用隱式 參數對<sup>ith</sup>元素的完整運算式。

>[!NOTE]
>例如`[]``vector[i]`,可以將運算元用於使用`IndexListItems`的任何單維陣組可視化,即使類型本身(`CATLArray`例如 )不允許此運算符。

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a>連結清單項目延伸

如果視覺化類型代表連結清單，則偵錯工具可以使用 `LinkedListItems` 節點顯示其子系。 `CAtlList`以下類型的視覺化使用`LinkedListItems`:

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

`Size` 項目參考清單的長度。 `HeadPointer` 指向第一個項目， `NextPointer` 參考下一個項目，而 `ValueNode` 參考項目的值。

除錯器在`NextPointer``LinkedListItems`節點元素的上下文中`ValueNode`計算和運算式,而不是父清單類型。 在前面的範例中,`CAtlList`有一`CNode`個類(`atlcoll.h`在中找到),該類是連結清單的節點。 `m_pNext`是`m_element``CNode`該 類的欄位,而不是`CAtlList`類的 欄位。

`ValueNode`可以留空,也可以用於`this`引用`LinkedListItems`節點本身。

#### <a name="customlistitems-expansion"></a>CustomListItems 展開

`CustomListItems` 展開可讓您撰寫周遊資料結構 (例如雜湊表) 的自訂邏輯。 用於`CustomListItems`可視化數據結構,這些結構可以使用C++表達式進行評估所需的一切,但不太`ArrayItems`適合`IndexListItems`的模具`LinkedListItems`。

可以使用`Exec`擴充中定義的變數和物件`CustomListItems`在擴展內部執行代碼。 可以使用邏輯運算子、算術運算子和賦值運算子使用`Exec`。 除了C++表達式賦值`Exec`器支援的[調試器內部函數](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state)外,不能用於計算函數。

以下視覺化工具`CAtlMap`是合適的優秀範例`CustomListItems`。

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a>樹專案延伸
 如果視覺化類型代表樹狀結構，則偵錯工具可以使用 `TreeItems` 節點查核樹狀結構並顯示其子系。 下面是使用`std::map``TreeItems`節點的類型的視覺化效果:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

語法與`LinkedListItems`節點類似。 `LeftPointer``RightPointer`,並在`ValueNode`樹節點類的上下文中求計算。 `ValueNode`可以留空或用於`this`引用`TreeItems`節點本身。

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem 展開
 元素`ExpandedItem`通過顯示基類或數據成員的屬性來生成聚合的子視圖,就像它們是可視化類型的子級一樣。 除錯器計算指定的表示式,並將結果的子節點追加到可視化類型的子清單中。

例如,智慧指標類型`auto_ptr<vector<int>>`通常顯示為:

 ![自動&#95;ptr&#60;矢量&#60;&#62;&#62; 預設延伸](../debugger/media/dbg_natvis_expand_expandeditem_default.png "預設延伸")

 要查看向量的值,您必須在變數視窗中向下鑽取兩個級別,通過`_Myptr`成員。 藉由新增 `ExpandedItem` 元素，您可以從階層中排除 `_Myptr` 變數，並直接檢視向量元素：

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![自動&#95;&#60;向量&#60;&#62;&#62; 扩展项目扩展](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem 展開")

下面的示例演示如何從派生類中的基類聚合屬性。 假設 `CPanel` 類別衍生自 `CFrameworkElement`。 節點可視化效果將這些屬性追加到`CFrameworkElement``CPanel`類的子清單中,而不是重複來自基類的屬性`ExpandedItem`。

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

此處需要關閉派生類的可視化匹配**的 nd**格式指定器。 否則,表達式`*(CFrameworkElement*)this`將導致再次應用`CPanel`可視化效果,因為預設可視化類型匹配規則認為它是最合適的。 使用**nd**格式指定器指示調試器使用基類視覺化,或者如果基類沒有可視化,則使用預設擴展。

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a>合成項目延伸
 其中 `ExpandedItem` 元素透過排除階層來提供更平面的資料檢視， `Synthetic` 節點則相反。 它允許您創建不是表達式的結果的人工子元素。 人工元素可以有自己的子元素。 在下列範例中， `Concurrency::array` 類型的視覺化使用 `Synthetic` 節點向使用者顯示診斷訊息：

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![併發::具有合成元素擴展的陣列](../debugger/media/dbg_natvis_expand_synthetic.png "併發::具有合成元素擴展的陣列")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>HResult 元素
 該`HResult`元素允許您自定義除錯器視窗中為**HRESULT**顯示的資訊。 元素`HRValue`必須包含要自定義的**HRESULT**的 32 位值。 元素`HRDescription`包含要在除錯器視窗中顯示的資訊。

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>UI 視覺化器元素
`UIVisualizer` 項目會向偵錯工具註冊圖形視覺化檢視外掛程式。 圖形可視化工具創建一個對話方塊或其他介面,以與其數據類型一致的方式顯示變數或物件。 可視化工具外掛程式必須作為[VSPackage](../extensibility/internals/vspackages.md)編寫,並且必須公開除錯器可以使用的服務。 *.natvis*檔包含外掛程式的註冊資訊,例如其名稱、公開服務的 GUID 及其可以可視化的類型。

以下是 UIVisualizer 項目的範例：

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- 屬性對識別`UIVisualizer``ServiceId` - `Id`。 是`ServiceId`可視化工具組公開的服務的 GUID。 `Id`是一個唯一標識碼,用於區分可視化工具(如果服務提供多個)。 在前面的示例中,相同的可視化工具服務提供了兩個可視化工具。

- 該`MenuName`屬性定義一個可視化工具名稱,以顯示在調試器中的放大鏡圖示旁邊的下拉清單中。 例如：

  ![UIVisualizer 功能表捷徑功能表](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer 功能表捷徑功能表")

*.natvis*檔案中定義的每種類型都必須顯式列出可以顯示它的任何 UI 可視化工具。 除錯器將類型項目中的可視化工具引用與已註冊的可視化工具匹配。 例如,引用上例中的以下`std::vector``UIVisualizer`類型條目。

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 在用於查看記憶體中位圖`UIVisualizer`[的圖像監視](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance)擴展中,可以看到一個範例。

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>CustomVisualizer 項目
 `CustomVisualizer`是一個擴展點,用於指定為控制 Visual Studio 代碼中的可視化效果而編寫的 VSIX 擴展。 有關編寫 VSIX 擴充的詳細資訊,請參閱[視覺化工作室 SDK](../extensibility/visual-studio-sdk.md)。

編寫自定義可視化工具比 XML Natvis 定義工作得多,但您不受 Natvis 執行或不支援的限制。 自定義視覺化工具可以存取完整的除錯器擴展 API 集,它可以查詢和修改除錯過程或與 Visual Studio 的其他部分通訊。

 可以在`Condition`元素上`IncludeView``CustomVisualizer`使用`ExcludeView`和屬性。

 ## <a name="limitations"></a>限制

Natvis 自定義項使用類和結構,但不使用 typedefs。

Natvis 不支援基元類型的可視化工具(`int`例如 ,,)`bool`或指向基元類型的指標。 在這種情況下,一個選項是使用適合您的用例的[格式指定器](../debugger/format-specifiers-in-cpp.md)。 例如,如果在代碼`double* mydoublearray`中使用,則可以在除錯器**的「監視」** 視窗中使用陣列格式指定器,例如顯示前 100 個元素`mydoublearray, [100]`的運算式 。
