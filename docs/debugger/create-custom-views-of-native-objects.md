---
title: 建立原生物件的自訂檢視
description: 自訂 Visual Studio 偵錯工具顯示原生類型的方式使用 Natvis 架構
ms.custom: ''
ms.date: 10/31/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 937692f11cbd642da823d6f7d13bcd90de59b388
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000857"
---
# <a name="create-custom-views-of-native-objects-in-the-debugger"></a>在 偵錯工具中建立原生物件的自訂檢視

Visual Studio *Natvis* framework 自訂原生類型的顯示的方式偵錯工具變數視窗中，例如**區域變數**並**監看式**windows 中，在**DataTips**。 Natvis 視覺化可以協助讓您建立偵錯期間更明顯可見的類型。 

Natvis 會取代*autoexp.dat* XML 語法、 更佳診斷、 版本控制，與舊版的 Visual Studio 中的檔案和支援的多個檔案。  

Natvis 不適用於：

- C + + Windows 桌面專案與**偵錯工具類型**設為**混合**之下**組態屬性** > **偵錯**. 
- [混合模式偵錯](how-to-debug-in-mixed-mode.md)受管理的相容性模式中的 Windows 傳統型應用程式 (**工具** > **選項** > **偵錯**  > **一般** > **使用 Managed 相容性模式**)。

## <a name="BKMK_Why_create_visualizations_"></a>Natvis 視覺化

您可以使用 Natvis 架構來建立您所建立之類型的視覺效果規則，以便開發人員可以更容易看清楚偵錯期間。  

例如下, 圖顯示類型的變數[textbox](http://go.microsoft.com/fwlink/?LinkId=258422)在偵錯工具視窗中未套用任何自訂視覺化。  

![TextBox 的預設視覺化](../debugger/media/dbg_natvis_textbox_default.png "TextBox 的預設視覺化")  

反白顯示的資料列會顯示 `Text` 類別的 `TextBox` 屬性。 複雜類別階層架構可讓您更容易找到這個屬性。 偵錯工具並不知道如何解譯的自訂字串類型，因此看不到保留在文字方塊的字串。  

相同`TextBox`看起來更簡單變數視窗中套用 Natvis 自訂視覺化檢視規則時。 類別的重要成員一起出現，並偵錯工具顯示的自訂字串類型的基礎字串值。  

![使用視覺化檢視的 TextBox 資料](../debugger/media/dbg_natvis_textbox_visualizer.png "使用視覺化檢視的 TextBox 資料")  

##  <a name="BKMK_Using_Natvis_files"></a>使用 c + + 專案中的.natvis 檔案  

使用 Natvis *.natvis*檔案來指定視覺效果的規則。 A *.natvis*檔案是 XML 檔案 *.natvis*延伸模組。 Natvis 結構描述定義於 *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*。  

基本結構 *.natvis*是一或多個`Type`元素代表視覺化項目。 每個完整的名稱`Type`項目中指定其`Name`屬性。  

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

Visual Studio 提供了一些 *.natvis*中的檔案 *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*資料夾。 這些檔案會有許多的常見類型的視覺化規則，並可做為撰寫新類型的視覺效果的範例。  

### <a name="add-a-natvis-file-to-a-c-project"></a>將.natvis 檔案加入至 c + + 專案  

您可以加入 *.natvis*檔案加入任何 c + + 專案。  

**若要加入新 *.natvis*檔案：**

1. C + + 專案中選取節點**方案總管**，然後選取**專案** > **加入新項目**，或以滑鼠右鍵按一下專案，然後選取**新增**  > **新項目**。
   
1. 在 **加入新項目**對話方塊中，選取**Visual c + +** > **公用程式** > **偵錯工具視覺化檔案 (.natvis)**. 
   
1. 命名檔案，然後選取**新增**。
   
   新檔案新增至**方案總管 中**，並在 Visual Studio 的 文件 窗格中開啟。 

Visual Studio 偵錯工具載入 *.natvis* c + + 專案中的檔案自動執行，並根據預設，也包含在 *.pdb*時在組建專案檔案。 如果您偵錯建置的應用程式，偵錯工具會載入 *.natvis*檔案 *.pdb*檔案，即使您沒有開啟的專案。 如果您不想 *.natvis*檔案中包含 *.pdb*，您可以從內建中排除它 *.pdb*檔案。

**若要排除 *.natvis*檔案 *.pdb*:**

1. 選取 *.natvis*中的檔案**方案總管**，然後選取**屬性**圖示，或以滑鼠右鍵按一下檔案，並選取**屬性**.
   
1. 向下箭號旁卸除**從組建排除**，然後選取**是**，然後選取**確定**。  

>[!NOTE]
>進行偵錯可執行檔專案，請使用方案項目加入任何 *.natvis*檔案，不是處於 *.pdb*，因為沒有可用的 c + + 專案。  

>[!NOTE]
>從載入的 Natvis 規則 *.pdb*僅適用於在模組中類型的 *.pdb*參考。 例如，如果*Module1.pdb*具有名為類型的 Natvis 項目`Test`，它只適用於`Test`類別*Module1.dll*。 如果另一個模組也會定義名為類別`Test`，則*Module1.pdb* Natvis 項目不會加以套用。  

### <a name="BKMK_natvis_location"></a> Natvis 檔案位置  

您可以加入 *.natvis*加入使用者目錄或檔案系統目錄中，如果您想要套用至多個專案。  

*.Natvis*檔案會依下列順序進行評估：  

1. 任何 *.natvis*檔案中內嵌 *.pdb*您偵錯時，除非已載入的專案中的相同名稱的檔案存在。  

1. 任何 *.natvis*位於已載入的 c + + 專案或最上層方案的檔案。 此群組包含所有已載入的 c + + 專案，包括 其他語言中的 類別庫，但不是專案。 

1.  使用者專屬的 Natvis 目錄 (例如 *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*)。  

1.  全系統 Natvis 目錄 (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*)。 此目錄已 *.natvis*與 Visual Studio 一起安裝的檔案。 如果您有系統管理員權限，您可以將檔案新增到這個目錄。  

## <a name="modify-natvis-files-while-debugging"></a>偵錯時修改.natvis 檔案  

您可以修改 *.natvis*其專案進行偵錯時 IDE 中的檔案。 在相同的執行個體，您要使用偵錯的 Visual studio 中開啟檔案，修改它，然後儲存起來。 已儲存的檔案，如**監看式**並**區域變數**windows 更新以反映變更。 

您也可以新增或刪除 *.natvis*的解決方案，您要偵錯，Visual Studio 中加入或移除相關的視覺效果中的檔案。  

您不能更新 *.natvis*檔案中內嵌 *.pdb*偵錯時的檔案。  

如果您修改 *.natvis*檔案在 Visual Studio 中，外部所做的變更不會自動生效。 若要更新偵錯工具視窗，您可以重新評估 **.natvisreload**命令**監看式**視窗。 然後變更才會生效，不需要重新啟動偵錯工作階段。  

也使用 **.natvisreload**命令來升級 *.natvis*為較新版本的檔案。 例如， *.natvis*檔案可能簽入原始檔控制，而且您想要挑選最新變更人別人建立。 

##  <a name="BKMK_Expressions_and_formatting"></a> 運算式和格式化  
Natvis 視覺化使用 C++ 運算式來指定要顯示的資料項目。 除了增強功能和限制的偵錯工具中的 c + + 運算式，其中所述[內容運算子 （c + +）](../debugger/context-operator-cpp.md)，要注意下列事項：  

- Natvis 運算式是在正在視覺化之物件的內容 (而非目前的堆疊框架) 中進行評估。 例如，`x`在 Natvis 運算式會參考名為欄位**x**中，不會以名為區域變數正在視覺化的物件**x**中目前的函式。 您無法存取 Natvis 運算式中的本機變數，但您可存取全域變數。  

- Natvis 運算式不允許函式評估或副作用。 會忽略函式呼叫和指派運算子。 由於 [偵錯工具內建函式](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) 沒有副作用，因此可自由地從任何 Natvis 運算式加以呼叫，即使不允許其他函式呼叫亦然。  

- 若要控制運算式的顯示方式，您可以使用任何所述的格式規範[格式規範，在 c + +](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)。 當項目 Natvis 在內部使用，例如，系統會忽略格式規範`Size`中的運算式[ArrayItems 展開](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)。  

## <a name="natvis-views"></a>Natvis 檢視  

您可以定義不同的 Natvis 檢視，以不同的方式顯示類型。 例如，以下是視覺效果`std::vector`，定義名為的簡化的檢視`simple`。 `DisplayString`和`ArrayItems`的預設檢視中顯示的項目和`simple`檢視中，而`[size]`並`[capacity]`項目不會顯示在`simple`檢視。 

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


在 **監看式**視窗中，使用 **，檢視**格式規範來指定替代的檢視。 簡單的檢視會顯示為**vec,view(simple)**:  

![簡單檢視的監看式視窗](../debugger/media/watch-simpleview.png "簡單檢視的監看式視窗")  

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis 錯誤  

當偵錯工具遇到視覺化項目中的錯誤時，它會忽略它們。 它會以其原始格式，顯示類型或挑選另一個適當的視覺化。 您可以使用 Natvis 診斷，來了解為什麼偵錯工具忽略視覺化項目，並查看基礎的語法和剖析錯誤。 

**若要開啟 Natvis 診斷：**

- 底下**工具** > **選項**(或**偵錯** > **選項**) >**偵錯** > **輸出視窗**，將**Natvis 診斷訊息 （只有 c + +）** 來**錯誤**，**警告**，或**Verbose**，然後選取 **[確定]**。 

在出現的錯誤**輸出**視窗。  

##  <a name="BKMK_Syntax_reference"></a> Natvis 語法參考  

###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer 項目  
`AutoVisualizer`元素是根節點 *.natvis*檔案，並包含命名空間`xmlns:`屬性。 

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

`AutoVisualizer`項目可以有[型別](#BKMK_Type)， [HResult](#BKMK_HResult)， [UIVisualizer](#BKMK_UIVisualizer)，並[CustomVisualizer](#BKMK_CustomVisualizer)子系。 

###  <a name="BKMK_Type"></a> Type 項目  

基本`Type`如這個範例所示：  

```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  

 `Type`項目會指定：  

1. 應該使用哪種類型的視覺效果的 (`Name`屬性)。  
   
2. 該類型物件的值外觀應該為何 ( `DisplayString` 項目)。  
   
3. 型別的成員外觀應該為何當使用者展開變數視窗中的型別 (`Expand`節點)。  
   
#### <a name="templated-classes"></a>樣板化類別
`Name`的屬性`Type`項目接受星號`*`做為萬用字元，可供樣板化類別名稱。  

在下列範例中，相同的視覺效果會使用的物件是否`CAtlArray<int>`或`CAtlArray<float>`。 如果沒有特定的視覺化項目`CAtlArray<float>`，則其優先順序高於一般項。  

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

您可以使用巨集 $T1，$T2 來參考在視覺化項目中的範本參數等等。 若要尋找這些巨集的範例，請參閱 *.natvis* Visual Studio 隨附的檔案。  

####  <a name="BKMK_Visualizer_type_matching"></a> 視覺化檢視類型比對  
如果驗證失敗的視覺化項目，則會使用下一個可用的視覺效果。  

#### <a name="inheritable-attribute"></a>Inheritable 屬性  
選擇性`Inheritable`屬性指定視覺效果是否僅適用於基底類型或基底型別和所有衍生型別。 `Inheritable` 的預設值為 `true`。  

在下列範例中，視覺效果只適用於`BaseClass`類型：  

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

#### <a name="priority-attribute"></a>Priority 屬性  

選擇性`Priority`屬性會指定要使用替代的定義中的順序，如果定義無法剖析。 可能的值`Priority`是： `Low`， `MediumLow`，`Medium`， `MediumHigh`，和`High`。 預設值是 `Medium`。 `Priority`屬性只區分在相同的優先順序 *.natvis*檔案。  

下列範例會先剖析符合 2015 STL 的項目。 如果無法剖析，但是它會使用 STL 的 2013年版本的替代項目：  

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
您可以放入`Optional`任何節點上的屬性。 如果選擇性節點內的子運算式無法剖析，偵錯工具會忽略該節點中，但套用的其餘部分`Type`規則。 在下列類型中， `[State]` 是非選擇性的，但 `[Exception]` 是選擇性的。  如果`MyNamespace::MyClass`具有名為 _ 欄位`M_exceptionHolder`，這兩個`[State]`節點和`[Exception]`出現節點，但如果沒有任何`_M_exceptionHolder`欄位中，只有`[State]`節點會出現。

```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

###  <a name="BKMK_Condition_attribute"></a> Condition 屬性  

選擇性`Condition`屬性可供許多視覺化項目，並指定使用視覺化規則的時機。 如果 condition 屬性中的運算式解析為`false`，不會套用的視覺化規則。 如果評估為`true`，或者沒有任何`Condition`屬性，視覺效果會套用。 如果其他邏輯在視覺化項目中，您可以使用這個屬性。 

例如，下列視覺效果有兩個`DisplayString`智慧型指標類型的項目。 當`_Myptr`成員是空的第一個條件`DisplayString`項目解析成`true`，因此該表單會顯示。 當`_Myptr`成員不是空的條件評估為`false`，而第二個`DisplayString`項目顯示。  

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

`IncludeView`和`ExcludeView`屬性會指定要顯示或不在特定的檢視中顯示的項目。 例如，在下列的 Natvis 規格`std::vector`，則`simple`檢視不會顯示`[size]`和`[capacity]`項目。

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

您可以使用`IncludeView`和`ExcludeView`個別成員和類型上的屬性。  

###  <a name="BKMK_Versioning"></a> Version 項目  
`Version`項目範圍設為特定模組和版本的視覺化項目。 `Version`項目可協助避免發生名稱衝突可減少意外不符的情況，並可讓不同的型別版本的不同視覺效果。  

常見的標頭檔，可由不同的模組定義的類型，如果已建立版本的視覺效果隨即出現，類型是在指定的模組版本時，才。  

在下列範例中，視覺效果是只適用於`DirectUI::Border`中找到類型`Windows.UI.Xaml.dll`1.0 至 1.5 版中。 

```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

###  <a name="BKMK_DisplayString"></a> DisplayString 項目 
`DisplayString`項目會指定要顯示變數的值的字串。 它接受與運算式混合的任意字串。 大括號內的所有項目都會解譯為運算式。 比方說，下列`DisplayString`項目：  

```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
```  

表示類型的變數`CPoint`顯示如本圖所示：  

 ![使用 DisplayString 項目](../debugger/media/dbg_natvis_cpoint_displaystring.png "使用 DisplayString 項目")  

在 `DisplayString`運算式中，`x`並`y`的成員`CPoint`，位於大括號，所以其值會評估。 此範例也示範如何使用雙重大括號逸出大括號 (`{{`或`}}`)。  

> [!NOTE]
> `DisplayString` 項目是接受任意字串和大括號語法的唯一項目。 所有其他視覺效果項目接受偵錯工具可以評估的運算式。  

###  <a name="BKMK_StringView"></a> StringView 項目 

`StringView`元素會定義偵錯工具可以傳送至內建文字視覺化檢視的值。 例如，假設下列視覺效果`ATL::CStringT`類型：  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  

`CStringT`物件會顯示變數視窗，如下列範例中：   

![CStringT 的 DisplayString 項目](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT 的 DisplayString 項目")  

新增`StringView`項目會告知偵錯工具就可以將值顯示為文字的視覺效果。  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

偵錯期間，您可以選取 在變數中，旁邊的放大鏡圖示，然後選取**文字視覺化檢視**來顯示字串之**m_pszData**指向。  

 ![含有 StringView 視覺化檢視的 CStringT 資料](../debugger/media/dbg_natvis_stringview_cstringt.png "含有 StringView 視覺化檢視的 CStringT 資料")  

運算式`{m_pszData,su}`包含 c + + 格式規範**su**，用來做為 Unicode 字串顯示值。 如需詳細資訊，請參閱 <<c0> [ 格式規範，在 c + +](../debugger/format-specifiers-in-cpp.md)。  

###  <a name="BKMK_Expand"></a> 展開項目 

選擇性`Expand`節點自訂視覺化類型的子系，當您展開變數視窗中的型別。 `Expand`節點接受定義子項目節點的子節點清單。  

- 如果`Expand`節點未指定在視覺化項目子系會使用預設展開規則。  
  
- 如果`Expand`指定節點在其下方沒有子節點的型別不會在偵錯工具視窗可展開。  

####  <a name="BKMK_Item_expansion"></a> Item 展開  

 `Item`項目是在最基本且常見的項目`Expand`節點。 `Item` 定義單一子項目。 例如，`CRect`類別的欄位`top`， `left`， `right`，和`bottom`具有下列視覺化項目：  

```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
```  

在 [偵錯工具] 視窗中，`CRect`型別是由本範例所示：  

![使用 item 項目展開的 CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "項目的項目展開的 CRect")  

偵錯工具評估中指定的運算式`Width`並`Height`項目，並顯示在值**值**變數視窗的資料行。 

偵錯工具會自動建立 **[未經處理的檢視]** 每個自訂的展開的節點。 上述螢幕擷取畫面會顯示 **[未經處理的檢視]** 節點展開，以顯示物件的預設未經處理檢視與其 Natvis 視覺化的不同方式。 預設展開會建立基底類別中，子樹狀結構，並列出所有的資料成員的基底類別做為子系。  

> [!NOTE]
> 如果 item 項目的運算式指向複雜類型，**項目**節點本身是可展開。  

####  <a name="BKMK_ArrayItems_expansion"></a> Size  
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

![使用 ArrayItems 展開的 std:: vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "使用 ArrayItems 展開的 std:: vector")  

`ArrayItems`節點必須有：  

- A`Size`運算式 （必須評估為整數） 偵錯工具若要了解陣列的長度。  
- A`ValuePointer`指向的第一個元素的運算式 (必須是不是項目類型的指標`void*`)。  

該陣列的下限預設值為 0。 若要覆寫值，請使用`LowerBound`項目。 *.Natvis*檔案隨附於 Visual Studio 有範例。  

>[!NOTE]
>您可以使用`[]`運算子，例如`vector[i]`，與使用任何一維陣列視覺化`ArrayItems`，即使該型別本身 (例如`CATLArray`) 不允許這個運算子。  

您也可以指定多維陣列。 在此情況下，偵錯工具需要稍微多一點的資訊，才能正確地顯示子項目：  

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

- `Direction` 指定陣列是否列還是資料行主要順序。 
- `Rank` 指定陣列的陣序。 
- `Size`項目接受隱含`$i`參數，它換成要在該維度中尋找陣列的長度的二維索引。 在上一個範例中，運算式`_M_extent.M_base[0]`應可提供第 0 個維度的長度`_M_extent._M_base[1]`第 1，依此類推。  

以下是二維`Concurrency::array`偵錯工具視窗中尋找的物件：  

![含有 ArrayItems 展開的二維陣列](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "含有 ArrayItems 展開的二維陣列")  

####  <a name="BKMK_IndexListItems_expansion"></a> IndexListItems 展開  

您可以使用`ArrayItems`只有當陣列項目連續配置在記憶體中的擴充。 偵錯工具取得下一個項目只是遞增其指標。 如果您需要管理值節點的索引，使用`IndexListItems`節點。 以下是使用視覺效果`IndexListItems`節點：  

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

唯一的差別`ArrayItems`並`IndexListItems`是`ValueNode`，這會預期完整的運算式，i<sup>第</sup>項目具有隱含`$i`參數。  

>[!NOTE]
>您可以使用`[]`運算子，例如`vector[i]`，與使用任何一維陣列視覺化`IndexListItems`，即使該型別本身 (例如`CATLArray`) 不允許這個運算子。  

####  <a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems 展開  

如果視覺化類型代表連結清單，則偵錯工具可以使用 `LinkedListItems` 節點顯示其子系。 下列視覺效果`CAtlList`輸入使用`LinkedListItems`:  

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

偵錯工具評估`NextPointer`並`ValueNode`的內容中的運算式`LinkedListItems`節點項目，不在父清單類型。 在上述範例中，`CAtlList`已經`CNode`類別 (位於`atlcoll.h`) 也就是連結清單節點。 `m_pNext` 並`m_element`是的欄位`CNode`類別，不是`CAtlList`類別。  

`ValueNode` 可以保留空白，或使用`this`來參考`LinkedListItems`節點本身。  

#### <a name="customlistitems-expansion"></a>CustomListItems 展開  
`CustomListItems` 展開可讓您撰寫周遊資料結構 (例如雜湊表) 的自訂邏輯。 使用 `CustomListItems`視覺化資料結構，可以使用 c + + 運算式評估，但非常不需要的一切符合區域變數`ArrayItems`， `IndexListItems`，或`LinkedListItems`。  

下列視覺化檢視`CAtlMap`的絕佳範例其中`CustomListItems`適合。  

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

您可以使用`Exec`來執行程式碼內的`CustomListItems`擴充，使用變數和擴充中定義的物件。 您可以使用邏輯運算子、 算術運算子，與指派運算子與`Exec`。 您無法使用`Exec`評估函式。

`CustomListItems` 支援下列的內建函式：

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
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

####  <a name="BKMK_TreeItems_expansion"></a> TreeItems 展開  
 如果視覺化類型代表樹狀結構，則偵錯工具可以使用 `TreeItems` 節點查核樹狀結構並顯示其子系。 以下是 視覺效果`std::map`輸入使用`TreeItems`節點：  

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

語法是類似於`LinkedListItems`節點。 `LeftPointer``RightPointer`，和`ValueNode`會在樹狀節點類別的內容下進行評估。 `ValueNode` 可以保留空白，或使用`this`來參考`TreeItems`節點本身。  

####  <a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem 展開  
 `ExpandedItem`所顯示的基底類別或資料成員的屬性，如同它們是視覺化類型的子系項目會產生的彙總的子檢視。 偵錯工具會評估指定的運算式，並將結果的子節點附加至視覺化類型的子清單。 

比方說，智慧型指標類型`auto_ptr<vector<int>>`通常會顯示為：  

 ![自動&#95;ptr&#60;向量&#60;int&#62; &#62;預設展開](../debugger/media/dbg_natvis_expand_expandeditem_default.png "預設展開")  

 若要查看向量的值，您必須在變數視窗中，透過傳遞的兩個層級向下鑽研`_Myptr`成員。 藉由新增`ExpandedItem`項目，您就可以排除`_Myptr`變數從階層並直接檢視向量項目：  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

 ![自動&#95;ptr&#60;向量&#60;int&#62; &#62; ExpandedItem 展開](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem 展開")  

下列範例示範如何從衍生類別中的基底類別彙總屬性。 假設 `CPanel` 類別衍生自 `CFrameworkElement`。 而不是重複的屬性，來自基底`CFrameworkElement`類別，`ExpandedItem`節點的視覺效果會將這些屬性附加至的子清單`CPanel`類別。 

```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  

**Nd**格式規範，以關閉 比對衍生類別的視覺效果，以下是必要。 否則，運算式`*(CFrameworkElement*)this`會導致`CPanel`視覺效果，以套用同樣的因為預設視覺化類型比對規則將它視為最適當的一個。 使用  **nd**格式規範來指示偵錯工具使用基底類別的視覺效果或預設展開，如果基底類別不有任何視覺效果。  

####  <a name="BKMK_Synthetic_Item_expansion"></a> 綜合的項目展開  
 雖然`ExpandedItem`項目透過排除階層架構，提供資料 flatter 檢視`Synthetic`節點執行相反的動作。 它可讓您建立假造的子項目不是運算式的結果。 假造的項目可以有它自己的子元素。 在下列範例中， `Concurrency::array` 類型的視覺化使用 `Synthetic` 節點向使用者顯示診斷訊息：  

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

 ![綜合的項目展開含有](../debugger/media/dbg_natvis_expand_synthetic.png "含有綜合的項目展開")  

###  <a name="BKMK_HResult"></a> HResult 項目 
 `HResult`元素可讓您自訂顯示的資訊**HRESULT**偵錯工具視窗。 `HRValue`項目必須包含的 32 位元值**HRESULT**要進行自訂。 `HRDescription`項目包含在偵錯工具視窗中顯示的資訊。  

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

###  <a name="BKMK_UIVisualizer"></a> UIVisualizer 項目 
`UIVisualizer` 項目會向偵錯工具註冊圖形視覺化檢視外掛程式。 圖形視覺化檢視建立對話方塊或其他介面會顯示變數或物件的方式以及其資料類型一致。 視覺化檢視外掛程式必須撰寫做[VSPackage](../extensibility/internals/vspackages.md)，且必須公開偵錯工具可以取用的服務。 *.Natvis*檔案包含註冊外掛程式的資訊，例如其名稱、 公開的服務，以及可視覺化之類型的 GUID。  

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

- A `ServiceId`  -  `Id`屬性組會識別`UIVisualizer`。 `ServiceId`封裝會公開為服務的視覺化檢視的 GUID。 `Id` 在服務提供一個以上時，是區分視覺化檢視的唯一識別碼。 在上述範例中，相同的視覺化檢視服務提供兩個視覺化檢視。  
  
- `MenuName`屬性定義要在偵錯工具的放大鏡圖示旁邊下拉式清單中顯示的視覺化檢視名稱。 例如:   

  ![UIVisualizer 功能表捷徑功能表](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer 功能表捷徑功能表")  

定義在每個型別 *.natvis*檔案都必須明確列出可以顯示任何 UI 視覺化檢視。 偵錯工具與已註冊視覺化檢視進行比對視覺化檢視中參考的型別項目。 例如，下列輸入項目`std::vector`參考`UIVisualizer`在上述範例中。  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 您所見的範例`UIVisualizer`中[Image Watch](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017)用來檢視記憶體中點陣圖的延伸模組。 

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer 項目  
 `CustomVisualizer` 是指定 VSIX 擴充功能，您撰寫來控制在 Visual Studio code 中的視覺效果的擴充點。 如需撰寫 VSIX 擴充功能的詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。 

它是更多的工作，來撰寫 XML Natvis 定義中，比自訂視覺化檢視，但是您可以從解 Natvis 沒有或不支援的條件約束。 自訂視覺化檢視可以存取完整的偵錯工具擴充性 Api，可以查詢和修改偵錯項目處理序或與 Visual Studio 的其他部分通訊。  

 您可以使用`Condition`， `IncludeView`，並`ExcludeView`上的屬性`CustomVisualizer`項目。
