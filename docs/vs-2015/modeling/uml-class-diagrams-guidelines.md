---
title: UML 類別圖： 方針 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: bfd0b13942f5faee82e284c435b7f937d3ae5094
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726513"
---
# <a name="uml-class-diagrams-guidelines"></a>UML 類別圖表：方針
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，您可以使用*UML 類別圖*來描述資料型別和實作的個別關係。 該圖表可用來重點描述類別的邏輯方面，而非實作。  
  
 若要建立 UML 類別圖中，在**架構**功能表上，選擇**新的 UML 圖表或分層圖**。  
  
 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
> [!NOTE]
>  本主題說明 UML 類別圖。 另外有一種類別圖，您可建立並用來視覺化程式碼。 請參閱[設計和檢視類別與類型](http://go.microsoft.com/fwlink/?LinkId=142231)。  
  
##  <a name="Using"></a> 使用 UML 類別圖  
 您可以將 UML 類別圖用於各種目的：  
  
-   提供與實作無關的類型說明，這些類型可在系統中使用，並在元件之間傳遞。  
  
     例如，類型「餐點訂購」可能的實作位置為：商務圖層的 .NET 程式碼中、元件之間介面上的 XML 中、資料庫的 SQL 中和使用者介面的 HTML 中。 儘管這些實作的細節不同，但「餐點訂購」與諸如「菜單」和「付款」等其他類型之間的關聯性卻始終是相同的。 UML 類別圖讓您可以分別討論這些關聯性與實作。  
  
-   釐清應用程式與使用者之間通訊所使用的字彙，以及使用者需求說明中的字彙。 請參閱[模型使用者需求](../modeling/model-user-requirements.md)。  
  
     例如，考慮餐廳應用程式的使用者劇本、使用案例和其他要求說明。 在此類說明中，可找到諸如「菜單」、「訂購」、「餐點」、「價格」、「付款」等詞彙。 您可以繪製 UML 類別圖，定義這些詞彙之間的關聯性。 這樣可降低要求說明中、使用者介面中和說明文件中出現詞彙不一致的風險。  
  
### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性  
 UML 類別圖通常與其他模型圖表一起繪製，以提供它們所使用的類型說明。 在每一種情況下，任何圖表都沒有隱含類型的實體表示。  
  
 活動圖表  
  
 通過「物件節點」的資料類型。  
  
 輸入與輸出連接和活動參數節點的類型。  
  
 請參閱[UML 活動圖表： 指導方針](../modeling/uml-activity-diagrams-guidelines.md)。  
  
 順序圖表  
  
 參數和訊息傳回值的類型。  
  
 生命線的類型。 生命線的類別應包括可能收到之所有訊息的作業。  
  
 請參閱[UML 循序圖： 方針](../modeling/uml-sequence-diagrams-guidelines.md)。  
  
 元件圖  
  
 元件介面，列出其作業。  
  
 請參閱[UML 元件圖： 方針](../modeling/uml-component-diagrams-guidelines.md)。  
  
 使用案例圖  
  
 目標的說明和使用案例步驟中提及的類型。  
  
 請參閱[UML 使用案例圖： 方針](../modeling/uml-use-case-diagrams-guidelines.md)。  
  
##  <a name="BasicSteps"></a> 繪製類別圖的基本步驟  
 如需 UML 類別圖 參考之元素的相關資訊，請參閱[UML 類別圖： 參考](../modeling/uml-class-diagrams-reference.md)。  
  
> [!NOTE]
>  建立任何模型圖的詳細的步驟所述[編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)。  
  
#### <a name="to-create-a-uml-class-diagram"></a>若要建立 UML 類別圖  
  
1.  在 **架構**功能表上，選擇**新增 UML 或分層圖**。  
  
2.  底下**範本**，選擇**UML 類別圖**。  
  
3.  命名圖表。  
  
4.  中**加入至模型專案**，在您方案中，選取現有的模型專案或**建立新的模型專案**，然後選擇 **確定**。  
  
     新的類別圖會顯示**UMLClass 圖表**工具箱。 工具箱包含需要的項目和關聯。  
  
#### <a name="to-draw-a-uml-class-diagram"></a>若要繪製 UML 類別圖  
  
1.  若要建立的類型，選擇**類別**，**介面**或是**列舉型別**工具在 [工具箱]，然後按一下圖表的空白部分。 (如果看不到工具箱，請按 CTRL+ALT+X)。  
  
2.  若要將屬性或作業新增至類型或列舉的常值中，選擇**屬性**， **Operations**或是**常值**標題在 [類型]，然後按 ENTER 鍵。  
  
     您可以撰寫簽章，例如 `f(x:Boolean):Integer`。 請參閱[屬性和作業](#AttributesAndOperations)。  
  
     若要快速加入數個項目，請在加入每個項目後按兩次 ENTER 鍵。 您可以使用方向鍵在清單中上下移動。  
  
3.  若要展開或摺疊類型，請選擇左上角的＞形箭號圖示。 您也可以展開和摺疊**屬性**並**Operations**類別或介面的一節。  
  
4.  若要繪製類型之間的關聯、繼承或相依性連結，請按一下適當的工具，然後按一下來源類型和目標類型。  
  
5.  若要建立封裝中的類型，建立封裝，使用**封裝**工具，並接著建立新的類型和封裝內的套件。 您也可以使用複製命令來複製類型，並在套件中貼上它們。  
  
6.  每個圖表都是相同專案中其他圖表之間共用之模型的檢視。 若要查看完整模型的樹狀檢視，請選擇**檢視**，**其他 Windows**， **UML 模型總管**。  
  
##  <a name="UsingTypes"></a> 使用類別、 介面和列舉型別  
 工具箱中可以使用三種標準類型的 Classifier。 這些指*型別*整份文件。  
  
 ![類別、 列舉和介面](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")  
  
- 使用**類別**(1) 來代表大部分的用途資料或物件的類型。  
  
- 使用**介面**(2) 中，您必須區分純介面和具有內部實作的具象類別的內容。 當圖表的用途是用於說明軟體實作時，此區分非常有用。 當建立被動資料模型，或正在定義用來說明使用者要求的概念時，它不是很有用。  
  
- 使用**列舉型別**(3) 來表示，例如具有有限的數目的常值之型別的`Stop`和`Go`。  
  
  -   將常值加入至列舉。 為每個項目提供不同的名稱。  
  
  -   需要的話，也可以針對每個常值提供數值。 開啟中列舉的常值的捷徑功能表選擇 **屬性**，然後輸入中的數字**值**欄位中**屬性**視窗。  
  
  為每個類型提供唯一的名稱。  
  
### <a name="getting-types-from-other-diagrams"></a>從其他圖表取得類型  
 您可以讓來自其他圖表的類型出現在 UML 類別圖上。  
  
 UML 類別圖表  
  
 您可以讓類別出現在多個 UML 類別圖上。 當您在一個圖表上建立一個類別時，將從類別拖曳**UML 模型總管**拖曳至其他圖表。  
  
 如果您希望每個圖表重點強調關聯性的特定群組，這會非常有用。  
  
 例如，您可以在一個圖表上顯示「餐點訂購」和餐廳「菜單」之間的關聯，而在其他圖表上顯示「餐點訂購」和「付款」之間的關聯。  
  
 元件圖  
  
 如果您已定義介面的元件在元件圖中，您可以拖曳的介面**UML 模型總管**拖曳至類別圖表。 在類別圖中，您可以定義介面中所包含的方法。  
  
 請參閱[UML 元件圖： 方針](../modeling/uml-component-diagrams-guidelines.md)。  
  
 UML 循序圖表  
  
 您可以從在循序圖中的生命線建立類別和介面，並再拖曳 [從類別**UML 模型總管]** 至 UML 類別圖。 順序圖表中的每個生命線都表示物件、元件或行動的執行個體。  
  
 若要從生命線建立類別，開啟生命線，捷徑功能表，然後選擇**建立類別**或是**建立介面**。 請參閱[UML 循序圖： 方針](../modeling/uml-sequence-diagrams-guidelines.md)。  
  
##  <a name="AttributesAndOperations"></a> 屬性和作業  
 屬性 (4) 是類型的每個執行個體可以具有的已命名的值。 存取屬性不會變更執行個體的狀態。  
  
 作業 (5) 是類型的執行個體可以執行的方法或函式。 它會傳回值。 如果其**isQuery**屬性為 true 時，無法變更執行個體的狀態。  
  
 若要將屬性或作業加入至類型中，開啟類型的捷徑功能表，選擇**新增**，然後選擇**屬性**或是**作業**。  
  
 若要查看其屬性，開啟屬性或作業的捷徑功能表，然後選擇 **屬性**。 屬性會出現在**屬性**視窗。  
  
 若要查看的作業參數的屬性，請選擇<strong>[...]</strong>中**參數**屬性。 新的屬性對話方塊隨即出現。  
  
 如需所有可設定屬性的詳細資訊，請參閱：  
  
-   [UML 類別圖表中屬性 (Attribute) 的屬性 (Property)](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [UML 類別圖表上作業的屬性](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
### <a name="types-of-attributes-and-operations"></a>屬性和作業的類型  
 每個*型別*屬性或作業，以及每個參數類型，可以是下列其中之一：  
  
- **（無）** -您可以保留類型，不會指定簽章中省略前面的冒號 (`:`)。  
  
- 其中一個標準基本類型：**布林**，**整數**，**字串**。  
  
- 在模型中定義的類型。  
  
- 範本類型，撰寫範本的參數化的值\<參數 >。 請參閱[範本類型](#Templates)。  
  
  您也可以撰寫尚未在模型中定義的類型名稱。 名稱將列在下**未指定的型別**UML 模型總管 中。  
  
> [!NOTE]
>  如果您後續在模型中定義了使用該名稱的類別或介面，較舊的屬性和作業仍將參考 [未指定的類型] 中的項目。 如果要使其改為參考新類別，您必須審視每個屬性或作業並重設類型，從下拉式功能表選取新類別。  
  
#### <a name="multiple-types"></a>多個類型  
 您可以設定任何屬性、作業或參數類型的多重性。  
  
 允許的值如下：  
  
 `[1]`  
  
 指定之類型的一個值。 這是預設值。  
  
 `[0..1]`  
  
 **Null**或指定型別的值。  
  
 `[*]`  
  
 指定之類型任何數目執行個體的集合。  
  
 `[1..*]`  
  
 指定之類型至少一個執行個體的集合。  
  
 `[n..m]`  
  
 指定之類型 `n` 到 `m` 個執行個體的集合。  
  
 如果多重性大於 1，也可以設定以下屬性：  
  
-   **IsOrdered** -如果為 true，集合已定義的順序。  
  
-   **IsUnique** -如果為 true，沒有任何重複值的集合中。  
  
### <a name="visibility"></a>可視性  
 *可見性*指出屬性或作業是否可以在類別定義之外存取。 允許的值如下：  
  
 **Public**  
  
 **+**  
  
 可從所有其他類型中存取。  
  
 **Private**  
  
 **-**  
  
 只能由這個類型的內部定義存取。  
  
 **套件**  
  
 **~**  
  
 只能在包含這個類型的套件中和明確匯入它的任何套件中存取。 請參閱[定義命名空間和封裝](#Packages)。  
  
 **Protected**  
  
 **#**  
  
 只能由這個類型和從它繼承的類型存取。 請參閱[繼承](#Inheritance)。  
  
### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>設定屬性或作業的簽章  
 屬性或作業的簽章 (含有可視性、名稱、參數 (用於作業) 和類型) 是屬性的集合。  
  
 您可以直接在圖表中撰寫簽章。 按一下屬性或作業以選取該屬性或作業，然後按一下該屬性或作業。  
  
 使用以下形式撰寫表單：  
  
```  
visibility attribute-name : Type  
```  
  
 \-或-  
  
```  
visibility operation-name (parameter1 : Type1, ...) : Type  
```  
  
 例如:   
  
```  
+ AddItem (item : MenuItem, quantity : Integer) : Boolean  
```  
  
 使用可視性的簡短形式。 預設值為 `+` (公用)。  
  
 每個類型都可以是在模型中已定義的類型、標準類型 (例如 Integer 或 String) 或尚未定義的新類型名稱。  
  
> [!NOTE]
>  如果撰寫參數清單中沒有類型的名稱，則會指出參數的名稱，而非類型。 在以下範例中，MenuItem 和 Integer 成為具有未指定類型的兩個參數名稱：  
>   
>  `AddItem(MenuItem, Integer) /* parameter names, not types! */`  
  
 若要在簽章中設定類型的多重性，請在類型名稱後面的方括弧中撰寫多重性，例如：  
  
```  
+ AddItems (items : MenuItem [1..*])  
+ MenuContent : MenuItem [*]  
```  
  
 如果屬性或作業是靜態的，則其名稱會在簽章中加底線顯示。 如果是抽象的，則名稱會以斜體字型顯示。  
  
 不過，您只能設定**Is Static**並**Is Abstract**中的屬性**屬性**視窗。  
  
#### <a name="full-signature"></a>完整簽章  
 編輯屬性 (Attribute) 或作業的簽章時，部分其他屬性 (Property) 可能出現在行的結尾、每個參數之後。 它們在大括號 {…} 之中顯示。 您可以編輯或加入這些屬性。 例如：  
  
```  
+ AddItems (items: MenuItem [1..*] {unique, ordered})  
+ GetItems (filter: String) : MenuItem [*] {ordered, query}  
```  
  
 這些屬性如下所示：  
  
 `unique`  
  
 **是唯一的**  
  
 集合中沒有重複值。 適用於多重性大於 1 的類型。  
  
 `ordered`  
  
 **排序**  
  
 集合是序列。 若為 false，則沒有明確的第一個項目。 適用於多重性大於 1 的類型。  
  
 `query`  
  
 **是查詢**  
  
 作業不會變更執行個體的狀態。 只適用於作業。  
  
 `/`  
  
 **衍生**  
  
 屬性是從其他屬性或關聯的值計算得出的。  
  
 "/" 出現在屬性的名稱之前。 例如：  
  
```  
/TotalPrice: Integer  
```  
  
 通常僅在編輯簽章時，圖表上才會顯示完整簽章。 完成編輯時，會隱藏其他屬性。 如果您想要一直看到完整簽章，開啟類型 的捷徑功能表，然後選擇**顯示完整簽章**。  
  
##  <a name="Associations"></a> 繪圖和使用關聯  
 使用關聯來表示兩個項目之間的任何連結類型，無論軟體中如何實作該連結。 例如，您可以使用關聯來表示 C# 中的指標、資料庫中的關聯，或從 XML 檔案的一部分到另一部分的交互參考。 它可以表示現實世界中物件之間的關聯，例如地球與太陽。 關聯不會說明連結的表示方式，只會說明有該資訊存在。  
  
### <a name="properties-of-an-association"></a>關聯的屬性  
 建立關聯之後，需設定其屬性。 開啟關聯的捷徑功能表，然後選擇**屬性**。  
  
 整體而言，關聯的屬性除了每個*角色*，亦即，關聯的兩端都有自己的一些屬性。 若要檢視它們，請展開**第一個角色**並**第二個角色**屬性。  
  
 每個角色的部分屬性都會直接顯示在圖表中。 這些屬性如下：  
  
- 角色名稱。 這會顯示在圖表上關聯的適當一端。 您可以將它設定在圖表上或在**屬性**視窗。  
  
- **多重性**，預設為**1**。 這也會顯示在圖表上關聯的適當一端。  
  
- **彙總**。 這會以菱形圖案顯示在連接器的一端。 您可以使用它來指出彙總角色上的執行個體擁有或包含其他項目的執行個體。  
  
- **是可瀏覽**。 如果只有一個角色為 true，則在巡覽方向中顯示箭號。 您可以使用它來指出軟體中連結和資料庫關聯的巡覽性。  
  
  這些和其他屬性的完整詳細資料，請參閱[屬性的關聯性，在 UML 類別圖](../modeling/properties-of-associations-on-uml-class-diagrams.md)。  
  
### <a name="navigability"></a>巡覽性  
 當您繪製關聯時，它的一端會有箭頭，表示可在該方向巡覽關聯。 如果類別圖代表軟體類別，而關聯代表指標或參考，這會很有用。 不過，使用類別圖代表實體和關聯或商務概念時，它與代表巡覽性比較不相關。 在這種情況下，您可能會偏好繪製不帶箭頭的關聯。 則可以藉由設定**是可巡覽**屬性設為 True 的關聯的兩端。 為了簡化起見，您可以下載程式碼範例[UML 網域模型](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4)。  
  
### <a name="attributes-and-associations"></a>屬性和關聯  
 關聯是顯示屬性的圖示方式。 例如，您可以繪製從「餐廳」到「菜單」的關聯，而不是建立具有類型為「菜單」之屬性的「餐廳」類別。  
  
 每個屬性名稱都會成為角色名稱。 它會顯示在關聯中與擁有類型相反的另一端。 例如，請參閱示範中的 `myMenu`。  
  
 通常，最好只針對不會在圖表上繪製的類型 (例如基本類型) 使用屬性。  
  
 ![對等的關聯和屬性](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")  
  
##  <a name="Inheritance"></a> 繼承  
 使用**繼承**工具來建立下列關聯性：  
  
- A*一般化*特製化的型別和一般型別之間的關聯性  
  
   \-或-  
  
- A*實現*類別和它所實作的介面之間的關聯性。  
  
  您無法在繼承關聯性中建立迴圈。  
  
### <a name="generalization"></a>一般化  
 一般化表示特製化或衍生類型繼承一般或基本類型的屬性、作業和關聯。  
  
 一般類型會顯示在關聯的箭頭一端。  
  
 繼承的作業和屬性通常不會顯示在特化製類型中， 但您可以將繼承的作業加入至特製化類型的作業清單。 如果想要覆寫特製化類型中的部分作業屬性，或想要指出實作程式碼可以執行此操作，則這非常有用。  
  
##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>若要覆寫特製化類型中作業的定義  
  
1. 按一下一般化關聯。  
  
    它會以反白顯示，旁邊出現行動標籤。  
  
2. 按一下此行動標籤，然後再按一下**覆寫作業**。  
  
    **覆寫作業** 對話方塊隨即出現。  
  
3. 選取您想要出現在特製化的類型，然後按一下 operations**確定**。  
  
   您所選取的作業隨即出現在特製化類型中。  
  
### <a name="realization"></a>實現  
 實現是指類別實作由介面指定的屬性和作業。 介面位於連接器的箭號一端。  
  
 建立實現連接器時，介面的作業會自動在實現類別中複寫。 如果將新作業加入至介面，則這些作業會在實現類別中複寫。  
  
 建立實現關聯性之後，可以將其轉換為棒棒糖標記法。 以滑鼠右鍵按一下 關聯性，然後選擇 **顯示為棒棒糖符號**。  
  
 這可讓您顯示類別實作的介面，而不會在類別圖上顯示很多實現連結而使圖表凌亂不堪。 您也可以在個別圖表上顯示實現作業的介面和類別。  
  
 ![使用連接器和棒棒糖符號顯示的實現](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")  
  
##  <a name="Templates"></a> 範本類型  
 您可以定義可由其他類型或值進行參數化的泛型類型或範本類型。  
  
 例如，您可以建立由索引鍵和實值類型參數化的泛型「字典」：  
  
 ![具有兩個參數的樣板類別](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")  
  
#### <a name="to-create-a-template-type"></a>若要建立範本類型  
  
1. 建立類別或介面。 這會成為範本類型。 根據實際情況進行命名，例如 `Dictionary`。  
  
2. 開啟新的類型的捷徑功能表，然後選擇**屬性**。  
  
3. 在 **屬性**] 視窗中，按一下 [ **[...]** 中**範本參數**欄位。  
  
    **範本參數集合編輯器** 對話方塊隨即出現。  
  
4. 選擇 [新增]。  
  
5. 將名稱屬性設定為範本類型的參數名稱，例如 `Key`。  
  
6. 設定**參數類型**。 預設值是**類別**。  
  
7. 如果您想要接受特定的基底類別只在衍生的類別的參數，設定**條件約束的值**您想要的基底類別。  
  
8. 新增多個參數，視需要然後選擇**確定**。  
  
9. 如您在其他類別中所執行動作，將屬性和作業加入至範本類型。  
  
     您可以使用的參數類型是**類別**，**介面**或是**列舉型別**屬性和作業的定義中。 例如，透過使用參數類別 `Key` 和 `Value`，可以在 `Dictionary` 中定義下列作業：  
  
     `Get(k : Key) : Value`  
  
     您可以使用的參數類型**整數**為多重性中的繫結。 例如，參數整數最大值可以用來定義屬性的多重性為 `[0..max]`。  
  
   如果您已經建立範本類型，可以使用它們來定義範本繫結：  
  
   ![從 Dictionary 樣板繫結的類別](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")  
  
#### <a name="to-use-a-template-type"></a>若要使用範本類型  
  
1.  建立新類型，例如 `AddressTable`。  
  
2.  開啟新的類型的捷徑功能表，然後選擇**屬性**。  
  
3.  在 **範本繫結**屬性中，選取範本類型，例如`Dictionary`，從下拉式清單。  
  
4.  依序展開**範本繫結**屬性。  
  
     系統會為範本類型的每個參數顯示一個資料列。  
  
5.  將每個參數設定為適當的值。 例如，將 `Key` 參數設定為稱為 `Name` 的類別。  
  
##  <a name="Packages"></a> 封裝  
 在 UML 類別圖中可以檢視封裝。 套件是其他模型項目的容器。 您可以在套件內建立任何項目。 在圖表上，如果移動套件，該套件內的項目也會隨之移動。  
  
 您可以使用摺疊/展開控制項來隱藏或顯示套件的內容。  
  
 請參閱[定義套件和命名空間](../modeling/define-packages-and-namespaces.md)。  
  
##  <a name="generating"></a> 從 UML 類別圖產生程式碼  
 若要開始實作 UML 類別圖上的類別，您可以產生 C# 程式碼或自訂程式碼產生的範本。 使用提供的 C# 範本來產生程式碼：  
  
-   開啟圖表或項目，快顯功能表選擇 **產生的程式碼**，然後設定必要的屬性。  
  
     如需如何設定這些屬性和自訂所提供的範本的詳細資訊，請參閱[從 UML 類別圖產生程式碼](../modeling/generate-code-from-uml-class-diagrams.md)。  
  
## <a name="see-also"></a>另請參閱  
 [編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)   
 [UML 類別圖： 參考](../modeling/uml-class-diagrams-reference.md)   
 [模型使用者需求](../modeling/model-user-requirements.md)   
 [UML 元件圖： 參考](../modeling/uml-component-diagrams-reference.md)   
 [UML 循序圖： 參考](../modeling/uml-sequence-diagrams-reference.md)   
 [UML 使用案例圖： 參考](../modeling/uml-use-case-diagrams-reference.md)   
 [UML 元件圖表：參考](../modeling/uml-component-diagrams-reference.md)



