---
title: 自訂檔案儲存體和 XML 序列化
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07efe6f73047efe389722bdeac8fa28ca4448cf1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55944932"
---
# <a name="customize-file-storage-and-xml-serialization"></a>自訂檔案儲存體和 XML 序列化

當使用者儲存執行個體，或*模型*，Visual Studio 中的特定領域語言 (DSL)，建立或更新的 XML 檔案。 可以重新載入檔案，才能重新建立存放區中的模型。

您可以藉由調整下的設定自訂的序列化配置**Xml 序列化行為**DSL 總管 中。 沒有下的一個節點**Xml 序列化行為**的每個網域類別、 屬性和關聯性。 關聯性位於其來源類別。 另外還有對應至圖形、 連接器和圖表類別的節點。

您也可以撰寫更進階的自訂程式碼。

> [!NOTE]
> 如果您想要將模型儲存在特定的格式，但您不需要將它重新載入來自該表單，請考慮使用文字範本產生輸出，從模型中，而不是一種自訂的序列化配置。 如需詳細資訊，請參閱 <<c0> [ 特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

## <a name="model-and-diagram-files"></a>模型和圖表檔

每個模型通常會儲存在兩個檔案：

-   模型檔案的名稱這類**Model1.mydsl**。 它會儲存模型項目和關聯性和其屬性。 這類副檔名 **.mydsl**取決**FileExtension**屬性**編輯器**DSL 定義中的節點。

-   圖表檔案的名稱這類**Model1.mydsl.diagram**。 它會儲存圖形、 連接器和其位置、 色彩、 線條寬度和其他詳細資料圖表的外觀。 如果使用者刪除 **.diagram**檔案，在模型中的基本資訊不會遺失。 只有圖表的版面配置會遺失。 模型檔案開啟時，一組預設圖形和連接器將會建立。

### <a name="to-change-the-file-extension-of-a-dsl"></a>若要變更 DSL 的副檔名

1.  開啟 DSL 定義中。 在 [DSL 總管] 中，按一下 [編輯器] 節點。

2.  在 [屬性] 視窗中，編輯**FileExtension**屬性。 不包含初始"。"的檔案名稱的副檔名。

3.  在 [方案總管] 中變更兩個項目範本中的檔案名稱**DslPackage\ProjectItemTemplates**。 這些檔案都有遵循以下格式的名稱：

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>預設的序列化配置

若要建立本主題的範例，請使用下列的 DSL 定義中。

![DSL 定義圖&#45;家譜模型](../modeling/media/familyt_person.png)

此 DSL 來建立模型，在螢幕上有下列的外觀。

![家譜圖表、工具箱和總管](../modeling/media/familyt_instance.png)

此模型已儲存，然後再重新開啟 XML 文字編輯器中：

```xml
<?xml version="1.0" encoding="utf-8"?>
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">
  <people>
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">
      <children>
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />
      </children>
    </person>
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />
  </people>
</familyTreeModel>
```

請注意下列有關序列化的模型的重點：

-   每個 XML 節點具有網域類別名稱相同的名稱，不同之處在於首字母是小寫。 例如，`familyTreeModel` 和 `person`。

-   網域屬性，例如名稱和生日年份會序列化為 XML 節點內的屬性。 同樣地，屬性名稱之初始字元會轉換成小寫。

-   每個關聯性會序列化為 XML 節點在來源端的關聯性的巢狀。 節點有相同的名稱為來源角色屬性，但大小寫的起始字元。

     例如，在 DSL 定義中，名為角色**人**源自**列舉 FamilyTree**類別。  在 XML 中，這名為節點所代表`people`巢狀於`familyTreeModel`節點。

-   每個內嵌關聯性的目標末端會序列化為巢狀於關聯性之下的節點。 例如，`people`節點包含數個`person`節點。

-   每個參考關聯性的目標端序列化成*moniker*，這會將編碼的目標項目參考。

     例如，在`person`節點，可以有`children`關聯性。 這個節點包含 moniker，例如：

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>了解 Moniker

Moniker 用來代表的模型和圖表檔案的不同部分之間的交互參考。 它們也可以用在`.diagram`檔案來參考的模型檔案中的節點。 有兩種形式的 moniker:

-   *識別碼 moniker*加上引號的目標項目的 GUID。 例如: 

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

-   *完整金鑰 moniker*呼叫的 moniker 索引鍵指定的網域屬性的值所識別的目標項目。 Moniker 的目標項目加上其父項目，在樹狀目錄中的內嵌關聯性的 moniker。

     下列範例會從在其中 DSL 有是名為 Album，有一個內嵌關聯性的網域類別具名的 Song 的網域類別：

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     如果目標類別，有網域屬性，就會使用完整的索引鍵 moniker 選項**是 Moniker 索引鍵**設為`true`中**Xml 序列化行為**。 在範例中，名為"Title"，"Album"和"Song"的網域類別中的網域屬性會設定這個選項。

完整的索引鍵 moniker 是比識別碼 moniker 所讀取的工作變得更容易。 如果您想要的模型檔案的 XML，人可閱讀，請考慮使用完整索引鍵的 moniker。 不過，就可以讓使用者可用來設定具有相同的 moniker 索引鍵的多個項目。 重複的索引鍵可能會導致不是要重新載入正確的檔案。 因此，如果您定義網域類別，使用完整索引鍵的 moniker 參考時，您應該考慮儲存重複的 moniker 的檔案時，防止使用者的方式。

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>若要設定網域類別 ID moniker 所要參考

1.  請確定**是 Moniker 索引鍵**是`false`類別和其基底類別中的每個網域屬性。

    1.  在 [DSL 總管] 中，展開**Xml 序列化 Behavior\Class 資料\\\<網域類別 > \Element 資料**。

    2.  確認**是 Moniker 索引鍵**是`false`的每個網域屬性。

    3.  如果網域類別的基底類別，重複該類別中的程序。

2.  設定**序列化 Id**  =  `true`領域類別。

     這個屬性可以在下找到**Xml 序列化行為**。

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>若要設定完整索引鍵的 moniker 所要參考的網域類別

-   設定**是 Moniker 索引鍵**針對現有的網域類別的領域屬性。 屬性的型別必須是`string`。

    1.  在 DSL 總管 中，展開**Xml 序列化 Behavior\Class 資料\\\<網域類別 > \Element 資料**，然後選取 網域屬性。

    2.  在 [屬性] 視窗中，設定**是 Moniker 索引鍵**至`true`。

-   \-或-

     建立新的網域類別使用**具名網域類別**工具。

     此工具會建立新的類別具有名為名稱的網域屬性。 **Is Element Name**並**是 Moniker 索引鍵**此網域屬性的屬性會初始化為`true`。

-   \-或-

     建立從網域類別的繼承關係，至另一個具有 moniker 索引鍵屬性的類別。

### <a name="avoid-duplicate-monikers"></a>Avoid Duplicate Monikers

如果您使用完整的索引鍵 moniker 時，就可以在使用者的模型中的兩個項目，可以擁有相同的值中的索引鍵屬性。 例如，如果您的 DSL 的類別都具有屬性名稱的人員，使用者可以設定兩個項目的名稱相同。 雖然模型可能是儲存至檔案，它會重新載入正確。

有數種方法，協助您避免這種情況：

-   設定**Is Element Name**  =  `true`索引鍵的領域屬性。 選取在 DSL 定義圖上的 [網域] 屬性，然後在 [屬性] 視窗中設定值。

     當使用者建立之類別的新執行個體時，這個值會導致網域屬性，以自動指派不同的值。 預設行為會將類別名稱的結尾中的數字。 這不會防止使用者將名稱變更為重複項目，但它可協助在案例中當使用者不會儲存模型之前設定的值。

-   啟用驗證的 dsl。 在 DSL 總管 中，請選取 編輯器 \ 驗證，並設定**使用...** 屬性，以`true`。

     沒有自動產生的驗證方法，以檢查模稜兩可。 方法是在`Load`驗證類別目錄。 這可確保，使用者將會收到警告，它可能無法重新開啟檔案。

     如需詳細資訊，請參閱 <<c0> [ 定義域專屬語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)。

### <a name="moniker-paths-and-qualifiers"></a>Moniker 路徑和限定詞

限定的索引鍵 moniker 結尾的 moniker 索引鍵，並加上內嵌的樹狀結構中的父代的 moniker。 比方說，如果 Album 的 moniker 為：

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

然後在該專輯歌曲的其中一個可能是：

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

不過，如果專輯改為參考的識別碼，則 moniker 會，如下所示：

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

請注意，GUID 是唯一的因為它永遠不會加上其父代的 moniker。

如果您知道特定的網域屬性永遠會在模型內的唯一值，您可以設定**是 Moniker 限定詞**至`true`該屬性。 這會導致它用作辨識符號，而不使用父代的 moniker。 例如，如果您同時設定**是 Moniker 限定詞**並**是 Moniker 索引鍵**專輯類別的 Title 網域屬性，該模型的名稱或識別碼並不使用 moniker 中的專輯和其內嵌子系：

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>自訂 XML 的結構

若要進行下列自訂，展開**Xml 序列化行為**DSL 總管 中的節點。 在網域類別，展開項目資料節點以查看清單的內容和關聯性，也就源自於此類別。 選取關聯性，並調整其 [屬性] 視窗中的選項。

-   設定**省略的項目**為 true 來省略離開的目標項目清單的來源角色節點。 如果來源和目標類別之間有一個以上的關聯性，您不應該設定這個選項。

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

-   設定**使用完整格式**代表關聯性執行個體的節點中內嵌的目標節點。 當您將網域屬性加入至網域關聯性時，會自動設定此選項。

    ```xml
    <familyTreeModel ...>
      <people>
        <!-- The following node is inserted by using Use Full Form: -->
        <familyTreeModelHasPeople myRelationshipProperty="x1">
          <person name="Henry VIII" .../>
        </familyTreeModelHasPeople>
        <familyTreeModelHasPeople myRelationshipProperty="x2">
          <person name="Elizabeth I" .../>
        </familyTreeModelHasPeople>
      </people>
    </familyTreeModel>
    ```

-   設定**表示法** = **項目**具有另存為元素，而不是做為屬性值的網域屬性。

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

-   若要變更序列化屬性和關聯性的順序，以滑鼠右鍵按一下項目資料下的項目，並使用**下移**或是**下移**功能表命令。

## <a name="major-customization-using-program-code"></a>使用程式碼的主要自訂

您可以取代部分或全部的序列化演算法。

我們建議您先研究中的程式碼**Dsl\Generated Code\Serializer.cs**並**SerializationHelper.cs**。

### <a name="to-customize-the-serialization-of-a-particular-class"></a>若要自訂特定類別的序列化

1.  設定**Is Custom**中該類別，其下的節點**Xml 序列化行為**。

2.  轉換所有範本、 建置方案，並調查造成編譯錯誤的結果。 幾乎每個錯誤的註解會說明您必須提供哪些程式碼。

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>若要提供您自己的序列化整個模型

1.  覆寫中 Dsl\GeneratedCode\SerializationHelper.cs 方法

## <a name="options-in-xml-serialization-behavior"></a>在 Xml 序列化行為的選項

在 DSL 總管 中，Xml 序列化行為 節點會包含每個網域類別、 關聯性、 圖形、 連接器和圖表類別的子節點。 在每個節點是一份內容和來源為該元素的關聯性。 在自己的權限和其來源類別下，會表示關聯性。

下表摘要說明您可以在 DSL 定義中的這一節中設定的選項。 在每個案例中，在 [DSL 總管] 中，選取項目，並在 [屬性] 視窗中設定的選項。

### <a name="xml-class-data"></a>Xml 類別資料

這些項目底下的 [DSL 總管] 中找到**Xml 序列化 Behavior\Class 資料**。

|||
|-|-|
|屬性|描述|
|具有自訂項目結構描述|如果為 True，表示網域類別具有自訂項目結構描述|
|為 Custom|將此設為 **，則為 True**如果您想要撰寫自己的這個網域類別的序列化和還原序列化程式碼。<br /><br /> 建置方案，並調查的錯誤，若要探索的詳細的指示。|
|網域類別|此類別的資料節點所套用的網域類別。 唯讀。|
|元素名稱|此類別的元素的 Xml 節點名稱。 預設值是網域類別名稱的小寫版本。|
|Moniker 屬性名稱|Moniker 元素中用來包含參考之屬性的名稱。 如果空白，則會使用的索引鍵屬性的識別碼名稱。<br /><br /> 在此範例中，它可以是"name":  `<personMoniker name="/Mike Nash"/>`|
|Moniker 元素名稱|用於參考項目，這個類別的 moniker 之 xml 項目的名稱。<br /><br /> 預設值是類別名稱加上"Moniker"的小寫版本。 例如， `personMoniker` 。|
|Moniker 的型別名稱|產生的項目，這個類別的 moniker 的 xsd 型別名稱。 XSD 處於**Dsl\Generated 程式碼\\\*Schema.xsd**|
|序列化識別碼|如果為 True，在檔案中包含的項目 GUID。 這必須是 true，如果沒有任何屬性來標示**是 Moniker 索引鍵**和 DSL 定義參考關聯性，這個類別。|
|類型名稱|在 指定的領域類別從 xsd 產生的 xml 型別的名稱。|
|注意|這個項目相關聯的非正式附註|

### <a name="xml-property-data"></a>Xml 屬性資料

[類別] 節點下找到的 Xml 屬性節點。

|||
|-|-|
|屬性|描述|
|網域屬性|Xml 序列化組態資料所套用的屬性。 唯讀。|
|是的 Moniker 索引鍵|如果為 True，此屬性可做為建立參考這個領域類別的執行個體的 moniker 索引鍵。|
|是 Moniker 限定詞|如果為 True，屬性用於建立 moniker 中的限定詞。 如果為 false，而且 SerializeId 不適用於此領域類別，moniker 會限定內嵌樹狀結構中的父元素的 moniker。|
|表示法|如果屬性，將屬性序列化為 xml 屬性;如果項目，它會序列化為元素;如果略過，它不是序列化。|
|Xml 名稱|用於 xml 屬性或項目代表之屬性的名稱。 根據預設，這可以是網域屬性名稱的小寫版本。|
|注意|這個項目相關聯的非正式附註|

### <a name="xml-role-data"></a>Xml 角色資料

來源類別節點下找到角色資料節點。

|屬性|描述|
|-|-|
|有自訂 Moniker|設定為 true，如果您想要提供自己的程式碼產生及解決周遊此關聯性的 moniker。<br /><br /> 如需詳細指示，請建置方案，，，然後按兩下 錯誤訊息。|
|網域關聯性|指定要套用這些選項的關係。 唯讀。|
|省略項目|如果為 true，XML 節點對應至來源角色會省略結構描述。<br /><br /> 如果來源和目標類別之間有一個以上的關聯性，此角色的節點會區分屬於兩個關聯性的連結。 因此，建議您不要設定此選項在此情況下。|
|角色項目名稱|指定 XML 項目衍生自來源角色名稱。 預設值是角色屬性名稱。|
|使用完整的表單|如果為 true，每個目標項目或 moniker 住代表關聯性的 XML 節點。 這應該設定為 true 的關聯性具有自己的網域屬性。|

## <a name="see-also"></a>另請參閱

- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)