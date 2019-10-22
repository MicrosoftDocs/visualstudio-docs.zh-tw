---
title: 自訂檔案儲存體和 XML 序列化 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9df1a954c2ae090e57341d489878d15d6f3f1867
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654993"
---
# <a name="customizing-file-storage-and-xml-serialization"></a>自訂檔案儲存體和 XML 序列化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當使用者在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中儲存特定領域語言（DSL）的實例或*模型*時，就會建立或更新 XML 檔案。 您可以重載該檔案，以在存放區中重新建立模型。

 您可以在 [DSL Explorer] 中調整 [ **Xml 序列化行為**] 底下的設定，以自訂序列化配置。 在**Xml 序列化行為**下，每個網域類別、屬性和關聯性都有一個節點。 關聯性位於其來源類別之下。 還有對應于圖形、連接器和圖表類別的節點。

 您也可以撰寫程式碼，以進行更先進的自訂。

> [!NOTE]
> 如果您想要以特定格式儲存模型，但不需要從該表單重載，請考慮使用文字模板來產生模型的輸出，而不是自訂的序列化配置。 如需詳細資訊，請參閱[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

## <a name="model-and-diagram-files"></a>模型和圖表檔案
 每個模型通常會儲存在兩個檔案中：

- 模型檔案的名稱如下： **Model1. mydsl**。 它會儲存模型元素和關聯性及其屬性。 副檔名（例如 **. mydsl** ）是由 DSL 定義中 [**編輯器**] 節點的 [ **FileExtension** ] 屬性所決定。

- 圖表檔案的名稱如下： **Model1. mydsl. 圖表**。 它會儲存圖形、連接器和其位置、色彩、線條粗細，以及圖表外觀的其他詳細資料。 如果使用者刪除了**圖表**檔案，就不會遺失模型中的重要資訊。 只有圖表的版面配置會遺失。 當模型檔案開啟時，將會建立一組預設的圖形和連接器。

#### <a name="to-change-the-file-extension-of-a-dsl"></a>變更 DSL 的副檔名

1. 開啟 DSL 定義。 在 [DSL Explorer] 中，按一下 [編輯器] 節點。

2. 在 屬性視窗中，編輯**FileExtension**屬性。 請勿包含副檔名的初始 "."。

3. 在方案總管中，變更**DslPackage\ProjectItemTemplates**中兩個專案範本檔案的名稱。 這些檔案的名稱會遵循此格式：

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>預設的序列化配置
 若要建立本主題的範例，請使用下列 DSL 定義。

 ![DSL 定義圖表&#45;系列樹狀結構模型](../modeling/media/familyt-person.png "FamilyT_Person")

 此 DSL 是用來建立在畫面上具有下列外觀的模型。

 ![系列樹圖表、工具箱和 explorer](../modeling/media/familyt-instance.png "FamilyT_Instance")

 此模型已儲存，然後在 XML 文字編輯器中重新開啟：

```
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

 請注意下列有關序列化模型的要點：

- 每個 XML 節點的名稱都與網域類別名稱相同，不同之處在于初始字母是小寫。 例如，`familyTreeModel` 和 `person`。

- [名稱] 和 [BirthYear] 之類的網域屬性會序列化為 XML 節點中的屬性。 同樣地，屬性名稱的初始字元會轉換成小寫。

- 每個關聯性會序列化為 XML 節點，並嵌套在關聯性的來源端內。 節點與來源角色屬性的名稱相同，但有小寫的初始字元。

     例如，在 DSL 定義中，名為**人員**的角色是源自于**FamilyTree**類別。  在 XML 中，這是由名為 `people` 嵌套于 `familyTreeModel` 節點內的節點所表示。

- 每個內嵌關聯性的目標端會序列化為在關聯性之下的節點。 例如，`people` 節點包含數個 `person` 節點。

- 每個參考關聯性的目標端會序列化為一個*標記*，以將目標元素的參考編碼。

     例如，在 `person` 節點底下，可能會有 `children` 關聯性。 此節點包含如下的名字：

    ```
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understanding-monikers"></a>瞭解名字
 標記是用來表示模型和圖表檔案的不同部分之間的交互參考。 它們也會在 `.diagram` 檔案中用來參考模型檔案中的節點。 有兩種形式的名字標記：

- *Id 名字*標記會括住目標元素的 GUID。 例如:

  ```
  <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />

  ```

- *限定*的索引鍵標記會依據指定的網域屬性值（稱為「名字」索引鍵）來識別目標元素。 Target 元素的名字元前面會加上內嵌關聯性樹狀結構中其父元素的名字標記。

   下列範例取自一個 DSL，其中有名為專輯的網域類別，它與名為 Song 的網域類別具有內嵌關聯性：

  ```
  <albumMoniker title="/My Favorites/Jazz after Teatime" />
  <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />

  ```

   如果目標類別具有網域屬性，而該屬性的選項**為 [標記索引鍵**]，則會使用限定的索引鍵名稱，並在**Xml 序列化行為**中 `true`。 在此範例中，此選項會設定為網域類別「專輯」和「歌曲」中名為「標題」的網域屬性。

  限定的金鑰名字標記比識別碼名字標記更容易閱讀。 如果您想要讓人員讀取模型檔案的 XML，請考慮使用限定的金鑰名字。 不過，使用者可以設定一個以上的元素，使其具有相同的名字標記索引鍵。 重複的索引鍵可能會導致檔案無法正確重載。 因此，如果您定義使用限定金鑰名字名稱所參考的網域類別，您應該考慮防止使用者儲存具有重複名字標記的檔案。

#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>若要設定要由識別碼名字項參考的網域類別

1. 請確定在類別及其基類中，每個網域屬性都 `false` [**是名字標記索引鍵**]。

    1. 在 [DSL Explorer] 中，展開 [ **Xml 序列化] Behavior\Class 資料 \\** _\<the 網域類別 >_ [ **\Element 資料**]。

    2. 確認每個網域屬性的**都是 `false` 的名字標記索引鍵**。

    3. 如果網域類別具有基類，請重複該類別中的程式。

2. 為網域類別設定**序列化識別碼** =  `true`。

     這個屬性可以在**Xml 序列化行為**下找到。

#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>設定限定的索引鍵標記所參考的網域類別

- 針對現有網域類別的網域屬性，Set**是「名字**」索引鍵。 屬性的類型必須是 `string`。

    1. 在 [DSL Explorer] 中，展開 [ **Xml 序列化] Behavior\Class 資料 \\** _\<the 網域類別 >_ [ **\Element 資料**]，然後選取 [網域] 屬性。

    2. 在屬性視窗中，將 [**是名字標記索引鍵**] 設定為 `true`。

- \-或-

     使用**命名網域類別**工具，建立新的網域類別。

     此工具會建立新的類別，其具有名為 Name 的網域屬性。 **是元素名稱**，而這個網域屬性的**是名字標記索引鍵**屬性會初始化為 `true`。

- \-或-

     建立從網域類別到具有 [名字標記索引鍵] 屬性之另一個類別的繼承關聯性。

### <a name="avoiding-duplicate-monikers"></a>避免重複的名字
 如果您使用限定的索引鍵名字，則使用者模型中的兩個專案可能會在索引鍵屬性中有相同的值。 例如，如果您的 DSL 具有具有屬性名稱的類別人員，則使用者可以將兩個元素的名稱設定為相同。 雖然可以將模型儲存至檔案，但無法正確重載。

 有數種方法可協助避免這種情況：

- Set 是 key domain 屬性的**元素名稱** =  `true`。 選取 DSL 定義圖表上的 網域 屬性，然後在 屬性視窗中設定值。

     當使用者建立類別的新實例時，這個值會自動將不同的值指派給網域屬性。 預設行為會在類別名稱的結尾加上一個數位。 這不會防止使用者將名稱變更為重複的，但在使用者不會在儲存模型之前設定值時，它會有説明。

- 啟用 DSL 的驗證。 在 [DSL Explorer] 中，選取 [Editor\Validation]，然後將 [**使用 ...** ] 屬性設定為 [`true`]。

     有一個自動產生的驗證方法，可檢查是否有多義性。 方法位於 `Load` 驗證類別目錄中。 這可確保使用者會收到警告，表示可能無法重新開啟檔案。

     如需詳細資訊，請參閱[使用特定領域語言進行驗證](../modeling/validation-in-a-domain-specific-language.md)。

### <a name="moniker-paths-and-qualifiers"></a>名字標記路徑和限定詞
 限定的索引鍵標記會以名字標記索引鍵結尾，並在內嵌樹狀結構中以其父系的名字標記做為首碼。 例如，如果專輯的標記為：

```
<albumMoniker title="/My Favorites/Jazz after Teatime" />

```

 該專輯的其中一個歌曲可能是：

```
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

 不過，如果改為依識別碼參考專輯，則名字標記會如下所示：

```
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

 請注意，因為 GUID 是唯一的，所以絕對不會加上其父系的名字標記。

 如果您知道特定的網域屬性在模型中一律會有唯一的值，您可以設定**為**該屬性的 `true`。 這會使其當做辨識符號使用，而不使用父系的標記。 例如，如果您將兩者都設定**為 [標記辨識符號**]，而針對 [專輯] 類別的 [標題網域] 屬性設為 [名字] 索引**鍵**，則模型的名稱或識別碼不會用於專輯的名字和其內嵌的子系：

```
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />

```

## <a name="customizing-the-structure-of-the-xml"></a>自訂 XML 的結構
 若要進行下列自訂，請展開 [DSL Explorer] 中的 [ **Xml 序列化行為**] 節點。 在網域類別底下，展開 [元素資料] 節點以查看來源為此類別的屬性和關聯性清單。 選取關聯性，然後在 屬性視窗中調整其選項。

- 將 [**省略**專案] 設為 true 以省略來源角色節點，只留下目標元素的清單。 如果來源和目標類別之間有多個關聯性，則不應該設定此選項。

    ```

    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>

    ```

- 設定 [**使用完整表單**]，將目標節點內嵌在代表關聯性實例的節點中。 當您將網域屬性加入至網域關聯性時，會自動設定這個選項。

    ```

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

- 將**標記法**設定  = **元素**，讓網域屬性儲存為元素，而不是屬性值。

    ```
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- 若要變更屬性和關聯性序列化的順序，請以滑鼠右鍵按一下 [元素資料] 底下的專案，然後使用 [**上移** **] 或 [下移]** 功能表命令。

## <a name="major-customization-using-program-code"></a>使用程式碼進行主要自訂
 您可以取代部分或所有的序列化演算法。

 我們建議您在**Dsl\Generated Code\Serializer.cs**和**SerializationHelper.cs**中研究程式碼。

#### <a name="to-customize-the-serialization-of-a-particular-class"></a>自訂特定類別的序列化

1. 在**Xml 序列化行為**下，在該類別的節點中，設定**為 Custom** 。

2. 轉換所有範本、建立方案，以及調查產生的編譯錯誤。 每個錯誤附近的批註說明您必須提供的程式碼。

#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>為整個模型提供您自己的序列化

1. 覆寫 Dsl\GeneratedCode\SerializationHelper.cs 中的方法

## <a name="options-in-xml-serialization-behavior"></a>Xml 序列化行為中的選項
 在 [DSL Explorer] 中，[Xml 序列化行為] 節點包含每個網域類別、關聯性、圖形、連接器和圖表類別的子節點。 在每個節點底下，都是源自該元素的屬性和關聯性清單。 關聯性會以自己的許可權和其來源類別來表示。

 下表摘要說明您可以在 DSL 定義的這個區段中設定的選項。 在每個案例中，選取 DSL Explorer 中的專案，然後在 屬性視窗中設定選項。

### <a name="xml-class-data"></a>Xml 類別資料
 這些元素會在 [DSL Explorer] 中的**Xml 序列化 Behavior\Class 資料**下找到。

|||
|-|-|
|屬性|描述|
|有自訂元素架構|若為 True，表示網域類別具有自訂元素架構|
|為自訂|如果您想要為此網域類別撰寫自己的序列化和還原序列化程式碼，請將此設為**True** 。<br /><br /> 建立解決方案並調查錯誤，以探索詳細的指示。|
|領域類別|此類別資料節點套用的網域類別。 唯讀。|
|元素名稱|這個類別之元素的 Xml 節點名稱。 預設值是網域類別名稱的小寫版本。|
|名字屬性名稱|要包含參考之標記專案中所使用屬性的名稱。 如果空白，則會使用索引鍵屬性或識別碼的名稱。<br /><br /> 在此範例中，它是 "name"： `<personMoniker name="/Mike Nash"/>`|
|標記元素名稱|Xml 專案的名稱，用於參考此類別之元素的名字。<br /><br /> 預設值是以小寫版本的類別名稱，並以 "名字" 作為尾碼。 例如，`personMoniker`。|
|標記類型名稱|為此類別的專案所產生的 xsd 型別名稱。 XSD 位於 Dsl\Generated 程式**代碼 \\ \*Schema .xsd**|
|序列化識別碼|如果為 True，則表示專案 GUID 包含在檔案中。 如果沒有任何屬性標示為名字標記索引**鍵**，而且 DSL 定義此類別的參考關聯性，則必須為 true。|
|類型名稱|Xsd 中所指定網域類別所產生的 xml 類型名稱。|
|備註|與此元素相關聯的非正式附注|

### <a name="xml-property-data"></a>Xml 屬性資料
 Xml 屬性節點可以在類別節點底下找到。

|||
|-|-|
|屬性|描述|
|網域屬性|套用 xml 序列化設定資料的屬性。 唯讀。|
|為名字標記索引鍵|若為 True，則會使用屬性做為索引鍵，以建立參考此網域類別之實例的名字。|
|為標記辨識符號|若為 True，則會使用屬性來建立名字標記中的限定詞。 如果為 false，而且如果此網域類別的 SerializeId 不是 true，則會以內嵌樹狀結構中父項目的標記來限定名字項。|
|表示|如果屬性，則會將屬性序列化為 xml 屬性;如果專案，則會將它序列化為元素;如果忽略，則不會序列化。|
|Xml 名稱|用於代表屬性之 xml 屬性或元素的名稱。 根據預設，這是網域屬性名稱的小寫版本。|
|備註|與此元素相關聯的非正式附注|

### <a name="xml-role-data"></a>Xml 角色資料
 角色資料節點可在來源類別節點底下找到。

|屬性|描述|
|--------------|-----------------|
|有自訂的名字標記|如果您想要提供自己的程式碼來產生及解析流經此關聯性的名字，請將此值設定為 true。<br /><br /> 如需詳細指示，請建立解決方案，然後按兩下錯誤訊息。|
|領域關聯|指定這些選項適用的關聯性。 唯讀。|
|省略元素|若為 true，則會從架構中省略對應至來源角色的 XML 節點。<br /><br /> 如果來源和目標類別之間有多個關聯性，此角色節點可區別屬於這兩個關聯性的連結。 因此，我們建議您不要在此情況下設定此選項。|
|角色元素名稱|指定衍生自來源角色之 XML 元素的名稱。 預設值為角色屬性名稱。|
|使用完整格式|若為 true，則每個目標專案或名字標記會括在代表關聯性的 XML 節點中。 如果關聯性有自己的網域屬性，這應該設定為 true。|

## <a name="see-also"></a>請參閱
 [在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)[從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)
