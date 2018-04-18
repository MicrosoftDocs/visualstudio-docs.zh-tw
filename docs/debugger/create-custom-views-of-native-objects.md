---
title: 在 偵錯工具中建立原生物件的自訂檢視 |Microsoft 文件
ms.custom: ''
ms.date: 06/27/2017
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 40a78f95ed98b0486b1ffa85eabea3ae8591b823
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="create-custom-views-of-native-objects-in-the-visual-studio-debugger"></a>在 Visual Studio 偵錯工具中建立原生物件的自訂檢視
Visual Studio Natvis 架構可讓您自訂 Visual Studio 偵錯工具變數視窗中顯示原生類型的方式 (例如，**監看式**視窗中，**區域變數**視窗中，然後在**資料提示方塊**。
  
 Natvis 會取代舊版 Visual Studio 使用的 **autoexp.dat** 檔案，並提供 XML 語法、更佳診斷、版本設定和多重檔案支援。  
  
> [!NOTE]
>  在下列情況下，您無法使用 Natvis 架構進行視覺化：  
>   
>  -  您正以類型設定為 **混合**的偵錯工具進行偵錯 C++ Windows 桌面專案。  
> -   您正進行混合的模式偵錯 managed 相容性模式中的 Windows 桌面應用程式中 (**工具 > 選項 > 偵錯 > 一般 > 使用 Managed 相容性模式**)。  
> -   您進行偵錯原生相容性模式中的 Windows 桌面應用程式 (**工具 > 選項 > 偵錯 > 一般 > 使用原生相容性模式**)。  
  
##  <a name="BKMK_Why_create_visualizations_"></a> 建立 Natvis 視覺化的原因  
 您可以使用 Natvis 架構來為您建立的類型建立視覺化規則，以讓開發人員在偵錯期間便於查看。  
  
 例如下, 圖顯示類型的變數[Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422)所顯示的偵錯工具不套用任何自訂視覺化。  
  
 ![TextBox 的預設視覺化](../debugger/media/dbg_natvis_textbox_default.png "DBG_NATVIS_TextBox_Default")  
  
 反白顯示的資料列會顯示 `Text` 類別的 `TextBox` 屬性。 複雜類別階層架構讓使用者難以發現此值。此外，偵錯工具並不知道如何解譯物件所使用的因此您看不到保留在文字方塊中的字串的自訂字串類型。  
  
 相同`TextBox`時看起來更簡單變數視窗中套用自訂視覺化規則。 您可以同時檢視類別的所有重要成員，且偵錯工具會顯示自訂字串類型的基礎字串值。  
  
 ![使用視覺化檢視的 TextBox 資料](../debugger/media/dbg_natvis_textbox_visualizer.png "DBG_NATVIS_TextBox_Visualizer")  
  
##  <a name="BKMK_Using_Natvis_files"></a> 使用 Natvis 檔案  
 .natvis 檔案是一種具有 natvis 副檔名的 XML 檔案。 結構描述是在 **%VSINSTALLDIR%\Xml\Schemas\natvis.xsd**中定義。  
  
 .natvis 檔案的基本結構是一或多個 `Type` 項目，其中每個 `Type` 項目代表某個類型的視覺化項目，而其完整名稱是在 `Name` 屬性中指定。  
  
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
  
 Visual Studio 在 **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers** 資料夾中隨附一些 .natvis 檔案。 這些檔案包含許多常見類型的視覺化規則，且可做為撰寫新類型視覺化時的範例。  
  
## <a name="adding-natvis-files-to-your-projects"></a>將 .natvis 檔案加入您的專案  
 您可以將 .natvis 檔案加入任何 C++ 專案。  
  
 若要加入新的.natvis 檔案，與開啟的 c + + 專案中選取專案節點**方案總管 中**，然後按一下**新增 > 新項目 > Visual c + + > 公用程式 > 偵錯工具視覺化檔案 (.natvis)**。 偵錯工具會自動從 C++ 專案載入 Natvis 檔案。 根據預設，也會將專案中的 Natvis 檔案插入到專案所建置的 .pdb 檔案。 這表示如果您偵錯此專案所建置的二進位檔，即使您沒有開啟此專案，偵錯工具還是會從 .pdb 載入 Natvis 檔案。 如果您不想將 .natvis 檔案包含在 .pdb 中，請以滑鼠右鍵按一下 **方案總管**中的 .natvis 檔案，然後在 [組態屬性]  視窗中將 [從組建排除]  設定為 [是] 。  
  
 建議您使用 Visual Studio 編輯 Natvis 檔案；任何您在偵錯期間所做的變更，都會在儲存檔案時自動生效。 您同時可從 IntelliSense 獲得較佳的編輯經驗。  
  
 從 .pdb 載入的 Natvis 檔案只會套用至該 pdb 所參考模組中的類型。 例如，如果 Module1.pdb 定義了名為 `Test`的類型項目，則這個項目只會套用至 Module1.dll 中的 **Test** 類別。 如果另一個模組也定義類別，名為**測試**，則 Module1.pdb 的 natvis 項目不會加以套用。  
  
##  <a name="BKMK_natvis_location"></a> 部署.natvis 檔案  
 如果您的.natvis 檔案只套用至您要建立 Visual Studio 專案中的類型，您不必執行任何動作;此.natvis 會包含在該.pdb 中。 不過，如果您要讓 .natvis 檔案套用至多個專案，可以將其加入使用者目錄或系統目錄。  
  
 評估 .natvis 檔案的順序如下：  
  
1.  （除非已載入的專案中存在相同名稱的檔案） 進行偵錯的.pdb 中內嵌的 natvis 檔案。  
  
2.  載入的 c + + 專案或最上層方案項目一部分的.natvis 檔案。 此群組包含所有已載入的 c + + 專案，包括類別庫，但是它不包含其他語言的專案 （例如，您無法載入.natvis 檔案從 C# 專案）。 針對可執行檔專案，您應該使用方案項目來裝載任何 .pdb 中尚未出現的 .natvis 檔案，因為沒有可供使用的 C++ 專案。  
  
3.  使用者專屬的 natvis 目錄 (例如， **%USERPROFILE%\Documents\Visual Studio 2017\Visualizers**或**%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers**)。  
  
4.  全系統 Natvis 目錄 (**%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers**)。 這個目錄是隨 Visual Studio 的.natvis 檔案複製的位置。 如果您有系統管理員權限，您可以將其他檔案加入這個目錄以及。  
  
## <a name="modifying-natvis-files-while-debugging"></a>在偵錯時修改 .natvis 檔案  
 您可以修改 IDE 中的 .natvis 檔案，同時偵錯包含該檔案的專案。 在 IDE 中開啟檔案 (使用和您用來偵錯的同一個 Visual Studio 執行個體)、加以修改並儲存。 只要已儲存檔案，[監看式]  和 [區域變數]  視窗應該就會更新，以反映此項變更。 如果您修改此 IDE 外的 .natvis 檔案，則該變更並不會自動生效。 若要更新此視窗，您可以評估 [監看式]  視窗中的 **.natvisreload** 命令。 這個動作會讓此變更才會生效，不需要重新啟動偵錯工作階段。  
  
 您也可以新增或刪除的方案，您正在偵錯，以及 Visual Studio 中加入或移除相關的視覺效果的.natvis 檔案。  
  
 如果.natvis 檔案內嵌於.pdb，您無法在偵錯時加以修改。  
  
 使用**.natvisreload**命令時，您要的 natvis 檔案升級為較新版本 （例如，如果它已簽入原始檔控制，而且您想要取得最新變更的其他人對該檔案）。 建議您使用 Visual Studio XML 編輯器來編輯 natvis 檔案。  
  
##  <a name="BKMK_Expressions_and_formatting"></a> 運算式和格式化  
 Natvis 視覺化使用 C++ 運算式來指定要顯示的資料項目。 除了增強功能和 c + + 運算式在偵錯工具中所述的限制[內容運算子 （c + +）](../debugger/context-operator-cpp.md)，您應該注意下列差異：  
  
-   Natvis 運算式是在正在視覺化之物件的內容 (而非目前的堆疊框架) 中進行評估。 例如，如果您使用`x`在 Natvis 運算式中，識別項參考名為欄位`x`，不到名為區域變數正在視覺化之物件中`x`目前正在執行的函式中。 您無法存取 Natvis 運算式中的區域變數，但可存取全域變數。  
  
-   Natvis 運算式不允許函式評估或副作用。 這表示已忽略函式呼叫和指派運算子。 由於 [偵錯工具內建函式](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) 沒有副作用，因此可自由地從任何 Natvis 運算式加以呼叫，即使不允許其他函式呼叫亦然。  
  
 若要控制運算式如何顯示在變數視窗中，您可以使用的任何格式規範中所述[格式規範](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)區段[c + + 中的格式規範](../debugger/format-specifiers-in-cpp.md)主題。 請注意，當虛擬項目由內部使用 Natvis，例如，會忽略格式規範`Size`中的運算式[ArrayItems 展開](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)。  
  
## <a name="natvis-views"></a>Natvis 檢視  
 Natvis 檢視可讓您以多種方式查看任何類型。 例如，您可以將提供簡單類型檢視的檢視定義名為 **simple** 。 例如，以下為 `std::vector`的視覺化：
  
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
  
 `DisplayString` 和 `ArrayItems` 項目用於預設檢視及簡單檢視，而簡單檢視中會將 `[size]` 和 `[capacity]` 項目排除。 您可以使用 **,view** 格式規範來指定替代的檢視。 在 [監看式]  視窗中，您可將簡單檢視指定為 **vec,view(simple)**：  
  
 ![監看式視窗，與簡單檢視](../debugger/media/watch-simpleview.png "監看式 SimpleView")  
  
##  <a name="BKMK_Diagnosing_Natvis_errors"></a> 診斷 Natvis 錯誤  
 您可以使用 Natvis 診斷來疑難排解語法和剖析錯誤。 此偵錯工具在視覺化項目中遇到錯誤時會忽略錯誤，並以未經處理的格式顯示類型或挑選另一個適當的視覺化。 若要了解為什麼會忽略某個視覺化項目，並查看有哪些基礎錯誤，您可以開啟 Natvis 診斷**工具 > 選項 > 偵錯 > 輸出 視窗 > Natvis 診斷訊息 （只有 c + +）**選項。 該錯誤會顯示在 [輸出]  視窗中。  
  
##  <a name="BKMK_Syntax_reference"></a> Natvis 語法參考  
  
###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer 項目  
 `AutoVisualizer`  項目是 .natvis 檔案的根節點，並且包含命名空間 `xmlns:` 屬性。  
  
```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  
  
###  <a name="BKMK_Type"></a> Type 項目  
 基本的 Type 看起來就像這樣：  
  
```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  
  
 其會指定：  
  
1.  這個視覺化應該用於哪種類型 ( `Type Name` 屬性)。  
  
2.  該類型物件的值外觀應該為何 ( `DisplayString` 項目)。  
  
3.  當使用者在變數視窗中展開類型的成員時，該成員外觀應該為何 ( `Expand` 節點)。  
  
 **樣板化類別** `Name` 項目的 `Type` 屬性接受星號 `*` 做為可供樣板化類別名稱使用的萬用字元：  
  
```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
  
```  
  
 在此範例中，不論物件是，會使用相同的視覺化`CAtlArray<int>`或`CAtlArray<float>`。 如果有特定視覺化項目`CAtlArray<float>`，則其優先順序高於一般項。  
  
 請注意，使用 $T1、$T2 等巨集，可以在視覺化項目中參考樣板參數。 若要尋找這些巨集的範例，請參閱 Visual Studio 隨附的 .natvis 檔案。  
  
####  <a name="BKMK_Visualizer_type_matching"></a> 視覺化檢視類型比對  
 如果視覺化項目無法驗證，則會使用下一個可用的視覺化。  
  
#### <a name="inheritable-attribute"></a>Inheritable 屬性  
 您可以指定視覺效果是否僅適用於基底類型，或適用於具有選擇性 `Inheritable` 屬性的基底類型和所有衍生類型。 在下列程式碼中，此視覺效果只適用於 `BaseClass` 類型：  
  
```xml
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  
  
 `Inheritable` 的預設值為 `true`。  
  
#### <a name="priority-attribute"></a>Priority 屬性  
 如果定義無法剖析，則 `Priority` 屬性會指定使用替代定義的順序。 `Priority` 的可能值為： `Low`、 `MediumLow`、`Medium`、 `MediumHigh`和 `High`，且預設值是 `Medium`。  
  
 Priority 屬性應該只用來區分相同 .natvis 檔案的優先權，而非不同檔案的優先權。  
  
 在下列範例中，我們先剖析符合 2015 STL 中，項目，如果無法剖析，我們使用替代項目的 STL 之 2013 年版本：  
  
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
  
####  <a name="BKMK_Versioning"></a> Version 項目  
 `Version` 項目可用來將視覺化範圍設為特定模組及其版本，以將名稱衝突降到最低，並且可針對不同版本的類型使用不同視覺化。 例如:   
  
```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
 在這個範例中，視覺化只適用於 `DirectUI::Border` 1.0 至 1.5 版中存在的 `Windows.UI.Xaml.dll` 類型。 加入版本項目範圍設為特定模組和版本將視覺化項目，並減少不當的不符。 不過，如果類型定義通用的標頭檔，以供不同的模組中，已建立版本的視覺效果未套用時的類型不是所指定模組中。  
  
#### <a name="optional-attribute"></a>Optional 屬性  
 `Optional` 屬性可以出現在任何節點上。 如果選擇性節點內的任何子運算式無法剖析，會忽略該節點，而其他的型別項目仍然有效。 在下列類型中， `[State]` 是非選擇性的，但 `[Exception]` 是選擇性的。  這表示如果`MyNamespace::MyClass`包含名為 _ 欄位`M_exceptionHolder`，您仍看見`[State]`節點和`[Exception]`節點，但如果`_M_exceptionHolder`遺失，您只會看到`[State]`節點。
  
```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  
  
###  <a name="BKMK_Condition_attribute"></a> Condition 屬性  
 選擇性 `Condition` 屬性可供許多視覺化項目使用，並指定何時應該使用視覺化規則。 如果 Condition 屬性中的運算式解析為 `false`，則不會套用項目所指定的視覺化規則。 如果評估為 true，或者沒有 `Condition` 屬性，則會將視覺化規則套用至類型。 您可以在視覺化項目中針對 `if-else` 邏輯使用這個屬性。 例如，下列視覺化為具有兩個`DisplayString`智慧型指標類型的項目：  
  
```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
  
```  
  
 當 `_Myptr` 成員為 `null`，會將第一個 `DisplayString` 項目的條件解析成 `true`，如此就可顯示表單。 當 `_Myptr` 成員不是 `null`時，條件評估為 `false`，而且會顯示第二個 `DisplayString` 項目。  
  
### <a name="includeview-and-excludeview-attributes"></a>IncludeView 和 ExcludeView 屬性  
 這些屬性會指定在不同檢視中要顯示或不顯示的項目。 例如，給定 `std::vector`的 Natvis 規格：  
  
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
  
 簡單檢視並不會顯示簡單檢視中的 [size] 和 [capacity] 項目。 如果我們使用了 `IncludeView="simple"` 而非 `ExcludeView`，則 `[size]` 和 `[capacity]` 項目會顯示在簡單檢視中，而非預設檢視中。  
  
 您可以在類型和個別成員上使用 `IncludeView` 和 `ExcludeView` 屬性。  
  
###  <a name="BKMK_DisplayString"></a> DisplayString  
 `DisplayString` 項目指定要顯示為變數值的字串。 它接受與運算式混合的任意字串。 大括號內的所有項目都會解譯為運算式。 比方說，`DisplayString`項目，如下所示：  
  
```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
  
```  
  
 表示類型的變數`CPoint`會顯示如圖所示：  
  
 ![使用 DisplayString 項目](../debugger/media/dbg_natvis_cpoint_displaystring.png "DBG_NATVIS_CPoint_DisplayString")  
  
 在 `DisplayString` 運算式中， `x` 和 `y`( `CPoint`的成員) 位於大括號中，因此會評估它們的值。 這個運算式也會示範如何使用雙重大括號 ( `{{` 或 `}}` ) 來逸出大括號。  
  
> [!NOTE]
>  `DisplayString` 項目是接受任意字串和大括號語法的唯一項目。 其他所有視覺化項目只會接受由偵錯工具評估的運算式。  
  
###  <a name="BKMK_StringView"></a> StringView  
 `StringView` 項目定義其值會傳送至內建文字視覺化檢視的運算式。 例如，假設我們有 `ATL::CStringT` 類型的下列視覺化：  
  
```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  
  
 視覺化在變數視窗中顯示類似如下的 `CStringT` 物件：   
  
 ![CStringT 的 DisplayString 項目](../debugger/media/dbg_natvis_displaystring_cstringt.png "DBG_NATVIS_DisplayString_CStringT")  
  
 加入`StringView`項目指示偵錯工具，這個值可以透過文字視覺化檢視：  
  
```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  
  
 請注意下列值旁邊顯示的放大鏡圖示。 選擇圖示會啟動文字視覺化檢視，其中會顯示字串的`m_pszData`指向。  
  
 ![含有 StringView 視覺化檢視的 CStringT 資料](../debugger/media/dbg_natvis_stringview_cstringt.png "DBG_NATVIS_StringView_CStringT")  
  
> [!NOTE]
>  請注意，運算式 `{m_pszData,su}` 包含 C++ 格式規範 `su` 來以 Unicode 字串顯示值。 如需詳細資訊，請參閱 [Format Specifiers in C++](../debugger/format-specifiers-in-cpp.md) 。  
  
###  <a name="BKMK_Expand"></a> Expand  
 當使用者在變數視窗中展開時，可使用 `Expand` 節點自訂視覺化類型的子系。 它接受定義子項目的子節點清單。  
  
 `Expand` 為選擇性節點。  
  
-   如果`Expand`節點中未指定的視覺化項目，會使用 Visual Studio 預設展開規則。  
  
-   如果`Expand`節點指定在其下方沒有子節點型別不是可展開偵錯工具視窗。  
  
####  <a name="BKMK_Item_expansion"></a> Item 展開  
 `Item` 項目是用於 `Expand` 節點的最基本和最常用的項目。 `Item` 定義單一子項目。 例如，假設您有 `CRect` 類別，其包含做為其欄位的 `top`、 `left`、 `right`和 `bottom` ，以及下列視覺化項目：  
  
```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
  
```  
  
 `CRect` 類型會顯示如下：  
  
 ![含有 item 項目展開的 CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "DBG_NATVIS_Expand_Item_CRect1")  
  
 在 `Width` 和 `Height` 項目中指定的運算式會評估並顯示在值資料行中。 每次使用自訂展開時，偵錯工具都會自動建立 `[Raw View]` 節點。 此節點已在上面的螢幕擷取畫面中展開，以顯示物件的未經處理檢視與其視覺化有何不同。 Visual Studio 預設展開會建立基底類別的子樹狀結構，並列出基底類別的所有資料成員做為子系。  
  
> [!NOTE]
>  如果 Item 項目的運算式指向複雜類型，則 `Item` 節點本身是可展開的。  
  
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
  
 ![使用 ArrayItems 展開的 std:: vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  
  
 `ArrayItems` 節點至少必須有：  
  
1.  可讓偵錯工具了解陣列長度的 `Size` 運算式 (必須評估為整數)。  
  
2.  應指向第一個項目 (必須是不屬於 `ValuePointer` 之項目類型的指標) 的 `void*`運算式。  
  
 該陣列的下限預設值為 0。 使用 `LowerBound` 項目可以覆寫這個值 (範例可以在 Visual Studio 隨附的 .natvis 檔案中找到)。  
  
 您現在可以使用 `[]` 運算子搭配 `ArrayItems` 擴充，例如 `vector[i]`。 [] 運算子可用於將使用 `ArrayItems` 或 `IndexListItems`的任何一維陣列視覺化，即使該類型本身不允許這個運算子 (例如 `CATLArray`)。  
  
 也可以指定多維陣列。 偵錯工具必須以適當地顯示子項目在此情況下只會稍微多一點資訊：  
  
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
  
 `Direction` 指定陣列是以資料列還是以資料行做為主要次序。 `Rank` 指定陣列的陣序。 `Size`項目接受隱含`$i`參數，以取代與維度的索引，以在該維度中尋找陣列的長度。 例如，在上述範例中，運算式 `_M_extent.M_base[0]` 上方應提供第 0 維度、第 1 維度等 `_M_extent._M_base[1]` 的長度。  
  
 以下是二維`Concurrency::array`物件在偵錯工具中的外觀：  
  
 ![含有 ArrayItems 展開的二維陣列](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  
  
####  <a name="BKMK_IndexListItems_expansion"></a> IndexListItems 展開  
 您僅能在陣列元素於記憶體中連續配置時，才能使用 `ArrayItems` 展開。 偵錯工具只是遞增其目前項目的指標，即可到達下一個項目。 若要支援您需要管理值節點索引的情況，可以使用 `IndexListItems` 節點。 以下是 視覺效果使用`IndexListItems`節點：  
  
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
  
 您現在可以使用 `[]` 運算子搭配 `IndexListItems` 擴充，例如 `vector[i]`。 `[]` 運算子可用於將使用 `ArrayItems` 或 `IndexListItems`的任何一維陣列視覺化，即使該類型本身不允許這個運算子 (例如 `CATLArray`)。  
  
 `ArrayItems` 和 `IndexListItems` 之間的唯一差異在於， `ValueNode` 需要第 i<sup></sup> 個項目的完整運算式具有隱含 `$i` 參數。  
  
####  <a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems 展開  
 如果視覺化類型代表連結清單，則偵錯工具可以使用 `LinkedListItems` 節點顯示其子系。 以下是 視覺效果`CAtlList`輸入使用這項功能：  
  
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
  
-   `NextPointer` 和 `ValueNode` 運算式是在連結清單節點項目的內容中，而不是在父清單類型中評估。 在上述範例中，`CAtlList`具有`CNode`類別 (位於`atlcoll.h`) 代表連結清單節點。 `m_pNext` 和 `m_element` 是該 `CNode` 類別 (而不是 `CAtlList` 類別) 的欄位。  
  
-   `ValueNode` 可以保留空白，或使用 `this` 來參考連結清單節點本身。  
  
#### <a name="customlistitems-expansion"></a>CustomListItems 展開  
 `CustomListItems` 展開可讓您撰寫周遊資料結構 (例如雜湊表) 的自訂邏輯。 您應該使用`CustomListItems`來視覺化資料結構中的所有項目，您必須評估為可以 c + + 運算式表示，但不完全符合一切`ArrayItems`， `TreeItems`，或 `LinkedListItems.`  
  
 CAtlMap 的視覺化檢視為 `CustomListItems` 適用時機的絕佳範例。  
  
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

您可以使用`Exec`執行內的程式碼`CustomListItems`使用變數和物件中定義的擴充`CustomListItems`擴充。 您無法使用`Exec`評估函式。

您可以使用邏輯運算子、 算術的運算子和指派運算子，與`Exec`。

支援下列的內建函式：

- `strlen, wcslen, strnlen, wcsnlen, strcmp, wcscmp, _stricmp, _strcmpi, _wcsicmp, strncmp, wcsncmp, _strnicmp, _wcsnicmp, memcmp, memicmp, wmemcmp, strchr, wcschr, memchr, wmemchr, strstr, wcsstr, __log2, __findNonNull`
- `GetLastError, TlsGetValue, DecodeHString, WindowsGetStringLen, WindowsGetStringRawBuffer, WindowsCompareStringOrdinal, RoInspectCapturedStackBackTrace, CoDecodeProxy, GetEnvBlockLength, DecodeWinRTRestrictedException, DynamicMemberLookup, DecodePointer, DynamicCast`
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
 如果視覺化類型代表樹狀結構，則偵錯工具可以使用 `TreeItems` 節點查核樹狀結構並顯示其子系。 以下是 視覺效果`std::map`輸入使用這項功能：  
  
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
  
 語法是類似於`LinkedListItems`節點。 `LeftPointer`、 `RightPointer`和 `ValueNode` 會在樹狀節點類別的內容下進行評估，而 `ValueNode` 可以保留空白，或使用 `this` 來參考樹狀節點本身。  
  
####  <a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem 展開  
 `ExpandedItem` 項目可用來產生彙總子檢視，方法是將基底類別或資料成員的屬性當做視覺化類型的子系來顯示。 系統會評估指定的運算式，並將結果的子節點附加至視覺化類型的子清單。 例如，假設我們具有智慧型指標類型`auto_ptr<vector<int>>`，這通常會顯示為：  
  
 ![自動&#95;ptr&#60;向量&#60;int&#62; &#62;預設展開](../debugger/media/dbg_natvis_expand_expandeditem_default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  
  
 若要查看向量的值，您必須在變數視窗中通過 _Myptr 成員，向下切入兩個層級。 藉由加入 `ExpandedItem` 項目，您可以從階層架構中排除 `_Myptr` 變數，並直接檢視向量項目：  
  
```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
 ![自動&#95;ptr&#60;向量&#60;int&#62; &#62; ExpandedItem 展開](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  
  
 下列範例會示範如何從衍生類別中的基底類別彙總屬性。 假設 `CPanel` 類別衍生自 `CFrameworkElement`。 `CFrameworkElement` 節點不會重複來自基底 `ExpandedItem` 類別的屬性，而是允許將這些屬性附加至 `CPanel` 類別的子清單。 **Nd**格式規範，則會關閉視覺效果比對衍生的類別，以下是必要。 否則，運算式`*(CFrameworkElement*)this`導致`CPanel`視覺效果，因為預設視覺化類型比對規則，重新套用至其視為最適當的一個。 使用**nd**格式規範會指示使用基底類別視覺化或基底類別預設展開基底類別沒有視覺化偵錯工具。  
  
```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
####  <a name="BKMK_Synthetic_Item_expansion"></a> Synthetic 項目展開  
 其中 `ExpandedItem` 項目透過排除階層架構來提供更平面的資料檢視， `Synthetic` 節點則相反。 其可讓您建立假造的子項目 (意即不是運算式結果的子項目)。 這個子項目可以包含它自己的子項目。 在下列範例中， `Concurrency::array` 類型的視覺化使用 `Synthetic` 節點向使用者顯示診斷訊息：  
  
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
  
 ![含有綜合的項目擴充](../debugger/media/dbg_natvis_expand_synthetic.png "DBG_NATVIS_Expand_Synthetic")  
  
###  <a name="BKMK_HResult"></a> HResult  
 `HResult` 項目可讓您自訂在偵錯工具視窗中用於顯示 HRESULT 的資訊。 `HRValue` 項目必須包含要自訂的 32 位元 HRESULT 值。 `HRDescription` 項目包含在偵錯工具中顯示的資訊。  
  
```  
  
<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  
  
###  <a name="BKMK_UIVisualizer"></a> UIVisualizer  
 `UIVisualizer` 項目會向偵錯工具註冊圖形視覺化檢視外掛程式。 圖形視覺化檢視外掛程式會建立對話方塊或其他介面，以適用於其資料類型的方式來顯示變數或物件。 視覺化檢視外掛程式必須撰寫做為 [VSPackage](../extensibility/internals/vspackages.md) ，而且需要公開可由偵錯工具使用的服務。 natvis 檔案包含外掛程式的註冊資訊，例如其名稱、公開之服務的 GUID，以及可視覺化的類型。  
  
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
  
 當在變數視窗中展開時， `UIVisualizer` 是以 `ServiceId` - `Id` 屬性組來識別。 `ServiceId` 是視覺化檢視封裝所公開之服務的 GUID， `Id` 是在服務提供多個視覺化檢視時，可用來區分視覺化檢視的唯一識別項。 在上述範例中，同一個視覺化檢視服務提供兩個視覺化檢視。  
  
 `MenuName` 屬性是使用者在偵錯工具變數視窗中開啟放大鏡圖示旁邊的下拉式功能表時，所看到的視覺化檢視名稱，例如：  
  
 ![UIVisualizer 功能表捷徑功能表](../debugger/media/dbg_natvis_vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  
  
 在 .natvis 檔案中定義的每個類型都必須明確列出可以顯示它們的 UI 視覺化檢視。 偵錯工具比對類型項目中的視覺化檢視參考，以符合已註冊之視覺化檢視的類型。 例如，下列類型項目`std::vector`參考上述範例中的 UIVisualizer。  
  
```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  
  
 您可以在用來檢視記憶體內部點陣圖影像的 Image Watch 擴充功能中看到 UIVisualizer 的範例： [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  
  
### <a name="customvisualizer-element"></a>CustomVisualizer 項目  
 `CustomVisualizer` 是指定 VSIX 擴充功能的擴充點，您可以撰寫此擴充來控制在 Visual Studio 中執行之程式碼的視覺化。 如需撰寫 VSIX 擴充功能的詳細資訊，請參閱 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。 撰寫自訂視覺化檢視時，會比撰寫 XML natvis 定義花更多心力，但您綁手綁腳哪些 natvis 支援或不支援。 自訂視覺化檢視可以存取完整的偵錯工具擴充性 API 集，這可用於查詢和修改偵錯項目處理序或與 Visual Studio 的其他組件通訊。  
  
 您可以在 CustomVisualizer 項目上使用 `Condition`、 `IncludeView`和 `ExcludeView` 屬性。