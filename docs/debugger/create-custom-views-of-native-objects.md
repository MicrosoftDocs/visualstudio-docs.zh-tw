---
title: 建立 C++ 物件的自訂檢視
description: 使用 Natvis 架構來自訂 Visual Studio 在偵錯工具中顯示原生類型的方式
ms.date: 10/31/2018
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
ms.openlocfilehash: 67c96c8d28014ee22a387c3ba3ca828b37f267dd
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75405203"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>使用 Natvis 架構， C++在偵錯工具中建立物件的自訂視圖

Visual Studio *Natvis*架構會自訂原生類型在偵錯工具變數視窗中的顯示方式，例如 [**區域變數** **] 和 [監看式]** 視窗和 [**資料提示**]。 Natvis 視覺效果可協助您建立更容易在調試過程中看到的類型。

Natvis 會以 XML 語法、更佳的診斷、版本控制和多個檔案支援取代舊版 Visual Studio 中的*autoexp.dat。*

> [!NOTE]
> Natvis 自訂會使用類別和結構，但不能用於 typedef。

## <a name="BKMK_Why_create_visualizations_"></a>Natvis 視覺效果

您可以使用 Natvis 架構來建立所建立類型的視覺效果規則，讓開發人員可以更輕鬆地在進行偵錯工具時看到它們。

例如，下圖顯示偵錯工具視窗中類型為[Windows：： UI：： Xaml：： Controls：： TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox)的變數，但未套用任何自訂視覺效果。

![TextBox 預設視覺效果](../debugger/media/dbg_natvis_textbox_default.png "TextBox 的預設視覺化")

反白顯示的資料列會顯示 `Text` 類別的 `TextBox` 屬性。 複雜類別階層會讓您難以找到這個屬性。 偵錯工具不知道如何解讀自訂字串類型，因此您看不到保留在文字方塊內的字串。

當套用 Natvis 自訂視覺化檢視規則時，相同的 `TextBox` 在 [變數] 視窗中看起來很簡單。 類別的重要成員會一起出現，而偵錯工具會顯示自訂字串類型的基礎字串值。

![使用視覺化檢視的 TextBox 資料](../debugger/media/dbg_natvis_textbox_visualizer.png "使用視覺化檢視的 TextBox 資料")

## <a name="BKMK_Using_Natvis_files"></a>在專案中C++使用 natvis 檔案

Natvis 會使用*Natvis*檔案來指定視覺效果規則。 *Natvis*檔案是副檔名為*natvis*的 XML 檔案。 Natvis 架構定義于 *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*中。

*Natvis*檔案的基本結構是一或多個代表視覺效果專案的 `Type` 元素。 每個 `Type` 元素的完整名稱會在其 `Name` 屬性中指定。

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

Visual Studio 在 *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*資料夾中提供一些*natvis*檔案。 這些檔案具有許多常見類型的視覺化規則，可做為撰寫新類型視覺效果的範例。

### <a name="add-a-natvis-file-to-a-c-project"></a>將 natvis 檔案新增至C++專案

您可以將*natvis*檔案新增至任何C++專案。

**若要加入新的*natvis*檔案：**

1. 在方案總管C++中選取專案節點，**然後選取 [** **專案**] > [**加入新專案**]，或以滑鼠右鍵按一下專案，然後選取 [新增 > **新專案**]。

1. 在 [**加入新專案**] 對話方塊中，選取 [  **C++ Visual** > **公用程式** > **偵錯工具視覺效果檔案（. natvis）** ]。

1. 將檔案命名為，然後選取 [**新增**]。

   新的檔案會新增至**方案總管**，並在 [Visual Studio 檔] 窗格中開啟。

Visual Studio 偵錯工具會自動載入專案中C++的 natvis 檔案，而且根據預設，在專案建立時，也會將這些檔案包含在 *.pdb*檔案中。 如果您在建立應用程式時，偵錯工具會從 *.pdb*檔案載入*natvis*檔案，即使您沒有開啟專案也一樣。 如果您不想要將*natvis*檔案包含在 *.pdb*中，可以將它從建立的 *.pdb*檔案中排除。

**若要從 *.pdb*中排除*natvis*檔案：**

1. 在**方案總管**中選取*natvis*檔案，並選取 [**屬性**] 圖示，或以滑鼠右鍵按一下檔案，然後選取 [**屬性**]。

1. 下拉 [**從組建排除**] 旁的箭號，然後選取 **[是**]，再選取 **[確定]** 。

>[!NOTE]
>針對可執行檔專案，請使用方案專案來加入不在 *.pdb*中的任何C++ *natvis*檔案，因為沒有可用的專案。

>[!NOTE]
>從 *.pdb*載入的 Natvis 規則僅適用于 *.pdb*所參考模組中的類型。 例如，如果*module1*具有名為 `Test`之類型的 Natvis 專案，它只會套用至*Module1*中的 `Test` 類別。 如果另一個模組也定義了名為 *`Test`的類別，則 Natvis 專案*不適用。

### <a name="BKMK_natvis_location"></a>Natvis 檔案位置

如果您想要將*natvis*檔案套用至多個專案，您可以將檔案新增至使用者目錄或系統目錄。

*Natvis*檔案會依照下列順序進行評估：

1. 除非已載入的專案中有相同名稱的檔案，否則，內嵌于您要進行偵錯工具之 *.pdb*中的任何*natvis*檔案。

2. 載入 C++的專案或最上層方案中的任何 natvis 檔案。 這個群組包括所有已C++載入的專案，包括類別庫，但不包含其他語言的專案。

::: moniker range="vs-2017"

3. 使用者特定的 Natvis 目錄（例如， *%USERPROFILE%\Documents\Visual Studio 2017 \ 視覺化檢視*）。

::: moniker-end

::: moniker range=">= vs-2019"

3. 使用者特定的 Natvis 目錄（例如， *%USERPROFILE%\Documents\Visual Studio 2019 \ 視覺化檢視*）。

::: moniker-end

4. 全系統 Natvis 目錄 ( *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*)。 此目錄包含隨 Visual Studio 安裝的*natvis*檔案。 如果您有系統管理員許可權，您可以將檔案新增至此目錄。

## <a name="modify-natvis-files-while-debugging"></a>在進行調試時修改 natvis 檔

您可以修改 IDE 中的*natvis*檔案，同時對其專案進行調試。 在您要進行調試的相同 Visual Studio 實例中開啟檔案，加以修改並加以儲存。 儲存檔案之後，[**監看式] 和 [** **區域變數**] 視窗更新會反映變更。

您也可以在要進行偵錯工具的方案中新增或刪除*natvis*檔案，Visual Studio 新增或移除相關的視覺效果。

當您在進行偵錯工具時，無法更新內嵌于 *.pdb*檔案中的*natvis*檔案。

如果您修改 Visual Studio 外部的*natvis*檔案，變更不會自動生效。 若要更新偵錯工具視窗，您可以重新評估 [**監看**式] 視窗中的 **.natvisreload**命令。 然後，變更就會生效，而不需要重新開機調試進程。

也請使用 **.natvisreload**命令，將*natvis*檔案升級至較新的版本。 例如， *natvis*檔案可能會簽入原始檔控制，而您想要挑選其他人所做的最近變更。

## <a name="BKMK_Expressions_and_formatting"></a> 運算式和格式化
Natvis 視覺化使用 C++ 運算式來指定要顯示的資料項目。 除了在偵錯工具中的C++運算式增強功能和限制（如[內容運算子（C++）](../debugger/context-operator-cpp.md)中所述），請注意下列事項：

- Natvis 運算式是在正在視覺化之物件的內容 (而非目前的堆疊框架) 中進行評估。 例如，Natvis 運算式中的 `x` 指的是正在視覺化的物件中名為**x**的欄位，而不是目前函式中名為**x**的本機變數。 您無法存取 Natvis 運算式中的區域變數，雖然您可以存取全域變數。

- Natvis 運算式不允許函數評估或副作用。 系統會忽略函式呼叫和指派運算子。 由於 [偵錯工具內建函式](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) 沒有副作用，因此可自由地從任何 Natvis 運算式加以呼叫，即使不允許其他函式呼叫亦然。

- 若要控制運算式的顯示方式，您可以使用[中C++的格式](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)規範中所述的任何格式規範。 Natvis 內部使用專案時，會忽略格式規範，例如[ArrayItems 擴充](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)中的 `Size` 運算式。

## <a name="natvis-views"></a>Natvis 檢視

您可以定義不同的 Natvis 視圖，以不同的方式來顯示類型。 例如，以下是定義名為 `simple`之簡化視圖的 `std::vector` 視覺效果。 `DisplayString` 和 `ArrayItems` 元素會顯示在預設的視圖和 [`simple`] 視圖中，而 [`[size]`] 和 [`[capacity]`] 專案則不會顯示在 [`simple`] 視圖中。

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

在 [**監看**式] 視窗中，使用 **、view**格式規範來指定替代的視圖。 簡單的視圖會顯示為 [ **vec]、[view （簡單）** ]：

![具有簡單視圖的監看式視窗](../debugger/media/watch-simpleview.png "簡單檢視的監看式視窗")

## <a name="BKMK_Diagnosing_Natvis_errors"></a>Natvis 錯誤

當偵錯工具在視覺效果專案中遇到錯誤時，會忽略它們。 它會以原始格式顯示型別，或挑選另一個適當的視覺效果。 您可以使用 Natvis 診斷來瞭解偵錯工具忽略視覺效果專案的原因，以及查看基礎語法和剖析錯誤。

**若要開啟 Natvis 診斷：**

- 在 **工具**  > **選項** （或  **Debug** > **選項**）**下 > debug** > **輸出視窗**，將**Natvis 診斷訊息（C++僅限）** 設定為 **錯誤** **、** **警告** 或 **詳細**資訊，然後選取

錯誤會出現在 [**輸出**] 視窗中。

## <a name="BKMK_Syntax_reference"></a> Natvis 語法參考

### <a name="BKMK_AutoVisualizer"></a> AutoVisualizer 項目
`AutoVisualizer` 元素是 *.natvis* 檔案的根節點，並且包含命名空間 `xmlns:` 屬性。

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

`AutoVisualizer` 元素可以有[類型](#BKMK_Type)、 [HResult](#BKMK_HResult)、[看到 uivisualizer](#BKMK_UIVisualizer)和[CustomVisualizer](#BKMK_CustomVisualizer)子系。

### <a name="BKMK_Type"></a> Type 項目

基本 `Type` 看起來像這個範例：

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 `Type` 元素會指定：

1. 視覺效果應使用的類型（`Name` 屬性）。

2. 該類型物件的值外觀應該為何 ( `DisplayString` 項目)。

3. 當使用者在變數視窗中展開類型（`Expand` 節點）時，該類型的成員應該看起來的樣子。

#### <a name="templated-classes"></a>樣板化類別
`Type` 元素的 `Name` 屬性會接受星號 `*` 作為可用於樣板化類別名稱的萬用字元。

在下列範例中，不論物件是 `CAtlArray<int>` 或 `CAtlArray<float>`，都會使用相同的視覺效果。 如果 `CAtlArray<float>`有特定的視覺效果專案，則其優先順序會高於泛型一個。

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

您可以使用宏 $T 1、$T 2 等等，來參考視覺效果專案中的樣板參數。 若要尋找這些巨集的範例，請參閱 Visual Studio 隨附的 *.natvis* 檔案。

#### <a name="BKMK_Visualizer_type_matching"></a> 視覺化檢視類型比對
如果視覺效果專案無法驗證，則會使用下一個可用的視覺效果。

#### <a name="inheritable-attribute"></a>Inheritable 屬性
選擇性的 `Inheritable` 屬性會指定視覺效果只適用于基底類型，還是套用至基底類型和所有衍生類型。 `Inheritable` 的預設值為 `true`。

在下列範例中，視覺效果只適用于 `BaseClass` 型別：

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priority 屬性

如果無法剖析定義，選擇性的 `Priority` 屬性會指定要使用替代定義的順序。 `Priority` 的可能值為： `Low`、`MediumLow`、`Medium`、`MediumHigh`和 `High`。 預設值為 `Medium`。 `Priority` 屬性只會區分同一個*natvis*檔案中的優先順序。

下列範例會先剖析符合 2015 STL 的專案。 如果無法剖析，它會針對2013版的 STL 使用替代專案：

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
您可以將 `Optional` 屬性放在任何節點上。 如果選擇性節點內的子運算式無法剖析，則偵錯工具會忽略該節點，但會套用其餘的 `Type` 規則。 在下列類型中， `[State]` 是非選擇性的，但 `[Exception]` 是選擇性的。  如果 `MyNamespace::MyClass` 具有名為 _`M_exceptionHolder`的欄位，則 `[State]` 節點和 `[Exception]` 節點都會出現，但如果沒有 `_M_exceptionHolder` 欄位，則只會顯示 [`[State]`] 節點。

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="BKMK_Condition_attribute"></a> Condition 屬性

選擇性的 `Condition` 屬性適用于許多視覺效果元素，並指定使用視覺效果規則的時機。 如果 condition 屬性內的運算式解析為 `false`，就不會套用視覺效果規則。 如果評估為 `true`，或沒有 `Condition` 屬性，則會套用視覺效果。 您可以將這個屬性用於視覺效果專案中的 else 邏輯。

例如，下列視覺效果有兩個適用于智慧型指標類型的 `DisplayString` 元素。 當 `_Myptr` 成員是空的時，第一個 `DisplayString` 元素的條件會解析為 `true`，如此表單就會顯示。 當 `_Myptr` 成員不是空的時，條件會評估為 `false`，而第二個 `DisplayString` 元素會顯示。

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

`IncludeView` 和 `ExcludeView` 屬性會指定要顯示或不顯示在特定視圖中的元素。 例如，在 `std::vector`的下列 Natvis 規格中，[`simple`] 視圖不會顯示 `[size]` 和 `[capacity]` 專案。

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

您可以在類型和個別成員上使用 `IncludeView` 和 `ExcludeView` 屬性。

### <a name="BKMK_Versioning"></a> Version 項目
`Version` 元素會將視覺化專案範圍設為特定模組和版本。 `Version` 元素有助於避免名稱衝突、減少不小心的不符，並允許不同類型版本的不同視覺效果。

如果不同模組所使用的通用標頭檔定義類型，則只有當類型在指定的模組版本中時，才會顯示版本化的視覺效果。

在下列範例中，視覺效果僅適用于從版本1.0 到1.5 的 `Windows.UI.Xaml.dll` 中找到的 `DirectUI::Border` 類型。

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

您不需要 `Min` 和 `Max`。 它們是選擇性屬性。 不支援萬用字元。

`Name` 屬性的格式為*filename. ext*，例如*hello .exe*或*some .dll*。 不允許路徑名稱。

### <a name="BKMK_DisplayString"></a>DisplayString 元素
`DisplayString` 元素會指定要顯示為變數值的字串。 它接受與運算式混合的任意字串。 大括號內的所有項目都會解譯為運算式。 例如，下列 `DisplayString` 專案：

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

表示 `CPoint` 類型的變數會顯示如下圖所示：

 ![使用 DisplayString 元素](../debugger/media/dbg_natvis_cpoint_displaystring.png "使用 DisplayString 元素")

在 `DisplayString` 運算式中，`x` 和 `y`（也就是 `CPoint`的成員）都是在大括弧內，因此會評估其值。 此範例也會示範如何使用雙大括弧（`{{` 或 `}}`）來對大括弧進行換用。

> [!NOTE]
> `DisplayString` 項目是接受任意字串和大括號語法的唯一項目。 所有其他視覺效果元素只接受偵錯工具可評估的運算式。

### <a name="BKMK_StringView"></a>StringView 元素

`StringView` 元素會定義偵錯工具可以傳送至內建文字視覺化檢視的值。 例如，假設有下列 `ATL::CStringT` 類型的視覺效果：

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

`CStringT` 物件會顯示在變數視窗中，如下列範例所示：

![CStringT DisplayString 元素](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT 的 DisplayString 項目")

新增 `StringView` 元素會告訴偵錯工具，它可以將值顯示為文字視覺效果。

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

在調試過程中，您可以選取變數旁的放大鏡圖示，然後選取 [**文字視覺化檢視**] 以顯示**m_pszData**指向的字串。

 ![使用 StringView 視覺化 CStringT 資料](../debugger/media/dbg_natvis_stringview_cstringt.png "含有 StringView 視覺化檢視的 CStringT 資料")

運算式 `{m_pszData,su}` 包含C++格式規範**su**，可將值顯示為 Unicode 字串。 如需詳細資訊，請參閱[中C++的格式](../debugger/format-specifiers-in-cpp.md)規範。

### <a name="BKMK_Expand"></a>Expand 元素

選擇性的 `Expand` 節點會在您展開變數視窗中的類型時，自訂視覺化類型的子系。 [`Expand`] 節點會接受定義子項目的子節點清單。

- 如果視覺效果專案中未指定 `Expand` 節點，則子系會使用預設的擴充規則。

- 如果指定的 `Expand` 節點沒有子節點，則在偵錯工具視窗中不會展開該類型。

#### <a name="BKMK_Item_expansion"></a> Item 展開

 `Item` 專案是 `Expand` 節點中最基本的元素。 `Item` 定義單一子項目。 例如，具有欄位 `top`、`left`、`right`和 `bottom` 的 `CRect` 類別具有下列視覺效果專案：

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

在偵錯工具視窗中，`CRect` 類型如下列範例所示：

![具有專案元素展開的 CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "含有 Item 項目展開的 CRect")

偵錯工具會評估 `Width` 和 `Height` 元素中指定的運算式，並在 [變數] 視窗的 [**值**] 資料行中顯示值。

偵錯工具會自動建立每個自訂展開的 **[原始視圖]** 節點。 先前的螢幕擷取畫面會顯示展開的 **[原始視圖]** 節點，以顯示物件的預設原始視圖與它的 Natvis 視覺效果有何不同。 預設展開會建立基類的子樹，並列出基類的所有資料成員做為子系。

> [!NOTE]
> 如果 item 專案的運算式指向複雜型別，則**專案**節點本身是可展開的。

#### <a name="BKMK_ArrayItems_expansion"></a> Size
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

![std：： vector 使用 ArrayItems 擴充](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "使用 ArrayItems 展開的 std::vector")

`ArrayItems` 節點必須具有：

- 可讓偵錯工具了解陣列長度的 `Size` 運算式 (必須評估為整數)。
- 指向第一個專案的 `ValuePointer` 運算式（必須是不是 `void*`之元素類型的指標）。

該陣列的下限預設值為 0。 若要覆寫值，請使用 `LowerBound` 元素。 Visual Studio 隨附的*natvis*檔案有範例。

>[!NOTE]
>您可以使用 `[]` 運算子（例如 `vector[i]`）搭配使用 `ArrayItems`的任何一維陣列視覺效果，即使類型本身（例如 `CATLArray`）不允許這個運算子也一樣。

您也可以指定多維度陣列。 在此情況下，偵錯工具需要更多的資訊，才能正確顯示子項目：

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

- `Direction` 指定陣列是以資料列或資料行為主要的順序。
- `Rank` 指定陣列的陣序。
- `Size` 元素接受隱含的 `$i` 參數，並將參數取代為維度索引，以便在該維度中尋找陣列的長度。 在上述範例中，運算式 `_M_extent.M_base[0]` 應該提供第0個維度的長度，`_M_extent._M_base[1]` 第1個，依此類推。

以下是二維 `Concurrency::array` 物件在偵錯工具視窗中的外觀：

![具有 ArrayItems 擴充的二維陣列](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "具有 ArrayItems 擴充的二維陣列")

#### <a name="BKMK_IndexListItems_expansion"></a> IndexListItems 展開

只有當陣列元素在記憶體中連續配置時，您才能使用 `ArrayItems` 擴充。 偵錯工具會藉由只遞增其指標來取得下一個元素。 如果您需要操作值節點的索引，請使用 `IndexListItems` 節點。 以下是具有 `IndexListItems` 節點的視覺效果：

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

`ArrayItems` 和 `IndexListItems` 之間的唯一差異在於 `ValueNode`，這預期<sup>第</sup>i 個元素的完整運算式具有隱含的 `$i` 參數。

>[!NOTE]
>您可以使用 `[]` 運算子（例如 `vector[i]`）搭配使用 `IndexListItems`的任何一維陣列視覺效果，即使類型本身（例如 `CATLArray`）不允許這個運算子也一樣。

#### <a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems 展開

如果視覺化類型代表連結清單，則偵錯工具可以使用 `LinkedListItems` 節點顯示其子系。 下列 `CAtlList` 類型的視覺效果使用 `LinkedListItems`：

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

偵錯工具會評估 `LinkedListItems` 節點元素內容中的 `NextPointer` 和 `ValueNode` 運算式，而不是父清單類型。 在上述範例中，`CAtlList` 具有 `CNode` 類別（在 `atlcoll.h`中找到），這是連結清單的節點。 `m_pNext` 和 `m_element` 是該 `CNode` 類別的欄位，而不是 `CAtlList` 類別。

`ValueNode` 可以保留空白，或使用 `this` 來參考 `LinkedListItems` 節點本身。

#### <a name="customlistitems-expansion"></a>CustomListItems 展開
`CustomListItems` 展開可讓您撰寫周遊資料結構 (例如雜湊表) 的自訂邏輯。 使用 `CustomListItems`，將可使用C++運算式的資料結構視覺化，以用於您需要評估的所有專案，但不適合 `ArrayItems`、`IndexListItems`或 `LinkedListItems`的模具。

下列適用于 `CAtlMap` 的視覺化檢視是適合 `CustomListItems` 的絕佳範例。

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

您可以使用 `Exec`，利用展開中定義的變數和物件，在 `CustomListItems` 擴充內執行程式碼。 您可以使用邏輯運算子、算術運算子和指派運算子搭配 `Exec`。 您無法使用 `Exec` 來評估函式。

`CustomListItems` 支援下列內建函式：

- `strlen`、`wcslen`、`strnlen`、`wcsnlen`、`strcmp`、`wcscmp`、`_stricmp`、`_strcmpi`、`_wcsicmp`、`strncmp`、`wcsncmp`、`_strnicmp`、`_wcsnicmp`、`memcmp`、`memicmp`、`wmemcmp`、`strchr`、`wcschr`、`memchr`、`wmemchr`、`strstr`、`wcsstr`、`__log2`、`__findNonNull`
- `GetLastError`、`TlsGetValue`、`DecodeHString`、`WindowsGetStringLen`、`WindowsGetStringRawBuffer`、`WindowsCompareStringOrdinal`、`RoInspectCapturedStackBackTrace`、`CoDecodeProxy`、`GetEnvBlockLength`、`DecodeWinRTRestrictedException`、`DynamicMemberLookup`、`DecodePointer`、`DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

#### <a name="BKMK_TreeItems_expansion"></a> TreeItems 展開
 如果視覺化類型代表樹狀結構，則偵錯工具可以使用 `TreeItems` 節點查核樹狀結構並顯示其子系。 以下是使用 `TreeItems` 節點之 `std::map` 類型的視覺效果：

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

語法類似于 `LinkedListItems` 節點。 `LeftPointer`、`RightPointer`和 `ValueNode` 會在樹狀節點類別的內容下進行評估。 `ValueNode` 可以保留空白，或使用 `this` 來參考 `TreeItems` 節點本身。

#### <a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem 展開
 `ExpandedItem` 元素會藉由顯示基類或資料成員的屬性，來產生匯總的子視圖，如同其為視覺化類型的子系。 偵錯工具會評估指定的運算式，並將結果的子節點附加至視覺化類型的子清單。

例如，智慧型指標類型 `auto_ptr<vector<int>>` 通常會顯示為：

 ![自動&#95;ptr&#60;向量&#60;int&#62; &#62;預設展開](../debugger/media/dbg_natvis_expand_expandeditem_default.png "預設展開")

 若要查看向量的值，您必須在變數視窗中向下切入兩個層級，傳遞 `_Myptr` 成員。 藉由新增 `ExpandedItem` 元素，您可以從階層中排除 `_Myptr` 變數，並直接檢視向量元素：

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![自動&#95;ptr&#60;向量&#60;int&#62; &#62; ExpandedItem 擴充](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem 展開")

下列範例顯示如何從衍生類別中的基類匯總屬性。 假設 `CPanel` 類別衍生自 `CFrameworkElement`。 `ExpandedItem` 節點視覺效果不會重複來自基底 `CFrameworkElement` 類別的屬性，而是將這些屬性附加至 `CPanel` 類別的子清單。

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

此處需要 **nd** 格式規範，以關閉衍生類別的視覺化比對。 否則，運算式 `*(CFrameworkElement*)this` 會導致再次套用 `CPanel` 的視覺效果，因為預設的視覺效果類型比對規則會將它視為最適合的類別。 使用**nd**格式規範來指示偵錯工具使用基類視覺效果，如果基類沒有視覺效果，則為預設展開。

#### <a name="BKMK_Synthetic_Item_expansion"></a> Synthetic 項目展開
 其中 `ExpandedItem` 元素透過排除階層來提供更平面的資料檢視， `Synthetic` 節點則相反。 它可讓您建立不是運算式結果的人工子項目。 人工智慧元素可以有自己的子項目。 在下列範例中， `Concurrency::array` 類型的視覺化使用 `Synthetic` 節點向使用者顯示診斷訊息：

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

 ![Concurrency：： Array 與綜合元素展開](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency：： Array 與綜合元素展開")

### <a name="BKMK_HResult"></a>HResult 元素
 `HResult` 專案可讓您自訂偵錯工具視窗中的**HRESULT**所顯示的資訊。 `HRValue` 元素必須包含要自訂的 32 位元 **HRESULT** 值。 `HRDescription` 元素包含要在偵錯工具視窗中顯示的資訊。

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="BKMK_UIVisualizer"></a>看到 uivisualizer 元素
`UIVisualizer` 項目會向偵錯工具註冊圖形視覺化檢視外掛程式。 圖形化視覺化會建立一個對話方塊或其他介面，以與資料類型一致的方式來顯示變數或物件。 視覺化設計工具外掛程式必須撰寫為[VSPackage](../extensibility/internals/vspackages.md)，而且必須公開偵錯工具可以使用的服務。 *Natvis*檔案包含外掛程式的註冊資訊，例如其名稱、公開服務的 GUID，以及可哥視化的類型。

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

- `ServiceId` - `Id` 屬性組識別 `UIVisualizer`。 `ServiceId` 是視覺化檢視封裝所公開之服務的 GUID。 `Id` 是區分視覺化程式的唯一識別碼（如果服務提供一個以上的）。 在上述範例中，相同的視覺化服務提供兩種視覺化檢視。

- `MenuName` 屬性會定義要在偵錯工具中放大鏡圖示旁的下拉式按鈕中顯示的視覺化檢視名稱。 例如：

  ![看到 uivisualizer 功能表快捷方式功能表](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer 功能表捷徑功能表")

*Natvis*檔案中定義的每個類型都必須明確列出可以顯示它的任何 UI 視覺化程式。 偵錯工具會比對類型專案中的視覺化檢視參考與已註冊的視覺化檢視。 例如，下列 `std::vector` 的類型專案會參考上述範例中的 `UIVisualizer`。

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 您可以在 [[影像監看式]](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017)延伸模組中查看用來查看記憶體中點陣圖 `UIVisualizer` 的範例。

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer 元素
 `CustomVisualizer` 是擴充點，會指定您撰寫的 VSIX 擴充功能，以在 Visual Studio 程式碼中控制視覺效果。 如需撰寫 VSIX 擴充功能的詳細資訊，請參閱[VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

撰寫自訂的視覺化程式比 XML Natvis 定義更多，但您不受限於 Natvis 不支援的條件約束。 自訂的視覺化程式可以存取一組完整的偵錯工具擴充性 Api，這可查詢和修改偵錯工具的進程，或與 Visual Studio 的其他部分通訊。

 您可以在 `CustomVisualizer` 元素上使用 `Condition`、`IncludeView`和 `ExcludeView` 屬性。