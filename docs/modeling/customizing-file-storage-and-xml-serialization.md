---
title: 自訂檔案儲存體和 XML 序列化
description: 瞭解當您在 Visual Studio 中將特定領域語言的實例或模型儲存 (DSL) 時，所建立或更新的 XML 檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 019f77320e9118d5f3d31e647a59c71bb474d204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935530"
---
# <a name="customize-file-storage-and-xml-serialization"></a>自訂檔案儲存體和 XML 序列化

當使用者將特定領域語言的實例或 *模型* 儲存 (DSL) Visual Studio 中，就會建立或更新 XML 檔案。 您可以重載該檔案，以在存放區中重新建立模型。

您可以在 [DSL Explorer] 中，藉由調整 **Xml 序列化行為** 底下的設定來自訂序列化配置。 每個網域類別、屬性和關聯性的 **Xml 序列化行為** 底下都有一個節點。 關聯性位於其來源類別之下。 也有對應到圖形、連接器和圖表類別的節點。

您也可以撰寫程式碼來進行更先進的自訂。

> [!NOTE]
> 如果您想要以特定格式儲存模型，但不需要從該表單重載，請考慮使用文字模板來產生模型的輸出，而不是自訂序列化配置。 如需詳細資訊，請參閱 [從 Domain-Specific 語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

## <a name="model-and-diagram-files"></a>模型和圖表檔案

每個模型通常會儲存在兩個檔案中：

- 模型檔案的名稱如 **Model1. mydsl**。 它會儲存模型專案和關聯性及其屬性。 副檔名（ **mydsl** ）是由 DSL 定義中 **編輯器** 節點的 **FileExtension** 屬性所決定。

- 圖表檔案的名稱如 **Model1. mydsl**。 它會儲存圖形、連接器及其位置、色彩、線條粗細，以及圖表外觀的其他詳細資料。 如果使用者刪除了 **圖表** 檔，則不會遺失模型中的基本資訊。 只有圖表的版面配置會遺失。 當模型檔案開啟時，將會建立一組預設的圖形和連接器。

### <a name="to-change-the-file-extension-of-a-dsl"></a>變更 DSL 的副檔名

1. 開啟 DSL 定義。 在 [DSL Explorer] 中，按一下 [編輯器] 節點。

2. 在屬性視窗中，編輯 **FileExtension** 屬性。 請勿包含副檔名的初始 "."。

3. 在方案總管中，變更 **DslPackage\ProjectItemTemplates** 中兩個專案範本檔案的名稱。 這些檔案的名稱會遵循此格式：

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>預設的序列化配置

若要建立本主題的範例，請使用下列 DSL 定義。

![DSL 定義圖 &#45; 系列樹狀結構模型](../modeling/media/familyt_person.png)

此 DSL 用來建立在螢幕上具有下列外觀的模型。

![家譜圖表、工具箱和總管](../modeling/media/familyt_instance.png)

已儲存此模型，然後在 XML 文字編輯器中重新開啟：

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

請注意下列有關序列化模型的重點：

- 每個 XML 節點的名稱與網域類別名稱相同，不同之處在于初始字母是小寫。 例如 `familyTreeModel` 和 `person`。

- 網域屬性（例如 Name 和 BirthYear）會序列化為 XML 節點中的屬性。 同樣地，會將屬性名稱的初始字元轉換成小寫。

- 每個關聯性都會序列化為內嵌于關聯性之來源端內的 XML 節點。 節點與來源角色屬性具有相同的名稱，但使用小寫的初始字元。

     例如，在 DSL 定義中，名為「 **人員** 」的角色是以 **FamilyTree** 類別為來源。  在 XML 中，這是由節點內名為 nested 的節點所代表 `people` `familyTreeModel` 。

- 每個內嵌關聯性的目標端都會序列化為在關聯性底下嵌套的節點。 例如， `people` 節點包含數個 `person` 節點。

- 每個參考關聯性的目標端都會序列化為一個 *標記*，以編碼對目標專案的參考。

     例如，在節點下 `person` ，可以有 `children` 關聯性。 此節點包含如下的名字：

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>瞭解名字

標記是用來表示模型和圖表檔案的不同部分之間的交互參考。 它們也會用在檔案中， `.diagram` 以參考模型檔案中的節點。 有兩種形式的標記：

- *識別碼* 標記會以目標元素的 GUID 括住。 例如：

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- *合格* 的索引鍵標記會以指定之網域屬性的值來識別目標元素，稱為「標記索引鍵」。 目標專案的標記會在內嵌關聯性樹狀結構中的父元素的標記前面加上名字。

     下列範例取自具有名為專輯之網域類別的 DSL，與名為 Song 的網域類別具有內嵌關聯性：

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     如果目標類別具有網域屬性，而該屬性的選項為 [  `true` **Xml 序列化行為**]，則會使用合格的索引鍵標記。 在此範例中，會針對網域類別 "專輯" 和 "Song" 中名為 "Title" 的網域屬性設定此選項。

限定的索引鍵標記比識別碼名字更容易讀取。 如果您想要讓人員讀取模型檔案的 XML，請考慮使用限定索引鍵的名字。 不過，使用者可以將多個元素設定為具有相同的標記索引鍵。 重複的索引鍵可能會導致檔案無法正確重載。 因此，如果您定義了使用限定金鑰標記所參考的網域類別，您應該考慮防止使用者儲存具有重複的標記之檔案的方式。

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>若要將網域類別設定為由識別碼名字組所參考

1. 請確定 `false` 類別和其基類中的每個網域屬性都是 [是] 索引鍵。

    1. 在 [DSL Explorer] 中，展開 [ **Xml 序列化 Behavior\Class 資料 \\ \<the domain class> \Element 資料**]。

    2. 確認每個網域屬性的 **是 [是** ] 索引鍵 `false` 。

    3. 如果網域類別具有基類，請在該類別中重複此程式。

2. 設定  =  `true` 網域類別的序列化識別碼。

     這個屬性可以在 **Xml 序列化行為** 下找到。

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>若要將網域類別設定為由合格的索引鍵標記所參考

- 針對現有網域類別的網域屬性 **，Set 是「標記** 」索引鍵。 屬性的類型必須是 `string` 。

    1. 在 [DSL Explorer] 中，展開 [ **Xml 序列化 Behavior\Class 資料 \\ \<the domain class> \Element 資料**]，然後選取 [網域] 屬性。

    2. 在屬性視窗中，set **為的是** `true` 。

- \- 或 -

     使用 **命名網域類別** 工具來建立新的網域類別。

     此工具會建立新的類別，該類別具有名為 Name 的網域屬性。 **是元素名稱**，而且這個網域屬性的 [標記] 索引 **鍵** 屬性會初始化為 `true` 。

- \- 或 -

     從網域類別建立繼承關聯性至另一個具有 [標記索引鍵] 索引鍵屬性的類別。

### <a name="avoid-duplicate-monikers"></a>避免重複的名字

如果您使用限定索引鍵的標記，則使用者模型中的兩個元素可能在索引鍵屬性中具有相同的值。 例如，如果您的 DSL 具有具有屬性名稱的類別人員，則使用者可以將兩個元素的名稱設定為相同。 雖然可以將模型儲存至檔案，但是它不會正確重載。

有數種方法可協助您避免這種情況：

- Set **為**  =  `true` key 網域屬性的元素名稱。 在 DSL 定義圖上選取 [網域] 屬性，然後在屬性視窗中設定值。

     當使用者建立類別的新實例時，這個值會讓網域屬性自動指派不同的值。 預設行為會在類別名稱的結尾加上一個數位。 這並不會防止使用者將名稱變更為重複的名稱，但在使用者未于儲存模型之前設定值的情況下，這會有所説明。

- 啟用 DSL 的驗證。 在 [DSL Explorer] 中選取 [Editor\Validation]，然後將 [ **使用 ...** ] 屬性設定為 `true` 。

     自動產生的驗證方法會檢查是否有歧義。 方法位於 `Load` 驗證分類中。 這可確保使用者會收到警告，指出可能無法重新開啟檔案。

     如需詳細資訊，請參閱 [以 Domain-Specific 語言進行驗證](../modeling/validation-in-a-domain-specific-language.md)。

### <a name="moniker-paths-and-qualifiers"></a>標記路徑和限定詞

限定索引鍵的標記結尾為「標記」索引鍵，而且在內嵌樹狀結構中的父代為其父系的標記。 例如，如果專輯的標記為：

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

然後，專輯中的其中一個歌曲可能是：

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

但是，如果改為依識別碼參考專輯，則名字標記會如下所示：

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

請注意，因為 GUID 是唯一的，所以永遠不會加上其父系的名字標記。

如果您知道特定的網域屬性在模型中一律會有唯一的值，您可以為該屬性設定為 [ **是的標記辨識符號** ] `true` 。 這會將它當做限定詞使用，而不需使用父系的標記。 例如，如果您同時設定 **了「標記辨識符號** 」和「為專輯」類別之 Title 網域屬性的「名字」索引 **鍵** ，則該模型的名稱或識別碼不會用於專輯的名字或其內嵌的子系：

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>自訂 XML 的結構

若要進行下列自訂，請在 [DSL Explorer] 中展開 [ **Xml 序列化行為** ] 節點。 在網域類別下，展開 [專案資料] 節點，以查看源自于此類別的屬性和關聯性清單。 選取關聯性，並在屬性視窗中調整其選項。

- 將 [ **省略** 專案] 設定為 [true] 以省略來源角色節點，只留下目標元素的清單。 如果來源和目標類別之間有多個關聯性，您就不應該設定此選項。

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- 設定 [ **使用完整格式** ]，在代表關聯性實例的節點中內嵌目標節點。 當您將網域屬性加入至網域關聯性時，會自動設定這個選項。

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

- 將 [**標記法**]  =  **元素** 設定為將 [網域] 屬性儲存為專案，而不是屬性值。

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- 若要變更屬性和關聯性序列化的順序，請以滑鼠右鍵按一下 [專案資料] 底下的專案，然後使用 [ **上移** ] 或 [ **下移** ] 功能表命令。

## <a name="major-customization-using-program-code"></a>使用程式碼的主要自訂

您可以取代部分或所有序列化演算法。

我們建議您研究 **Dsl\Generated Code\Serializer.cs** 和 **SerializationHelper.cs** 中的程式碼。

### <a name="to-customize-the-serialization-of-a-particular-class"></a>自訂特定類別的序列化

1. 在 **Xml 序列化行為** 下，Set 在該類別的節點中 **是自訂** 的。

2. 轉換所有範本、建立方案，以及調查產生的編譯錯誤。 每個錯誤附近的批註會說明您必須提供的程式碼。

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>為整個模型提供您自己的序列化

1. 覆寫 Dsl\GeneratedCode\SerializationHelper.cs 中的方法

## <a name="options-in-xml-serialization-behavior"></a>Xml 序列化行為中的選項

在 [DSL Explorer] 中，[Xml 序列化行為] 節點包含每個網域類別、關聯性、圖形、連接器和圖表類別的子節點。 在每個節點下，都是以該元素為來源的屬性和關聯性清單。 關聯性會以自己的許可權，以及其來源類別來表示。

下表摘要說明您可以在 DSL 定義的這個區段中設定的選項。 在每個案例中，選取 [DSL Explorer] 中的元素，並在 [屬性視窗] 中設定選項。

### <a name="xml-class-data"></a>Xml 類別資料

這些元素可在 [DSL Explorer] 中的 **Xml 序列化 Behavior\Class 資料** 下找到。

|屬性|描述|
|-|-|
|具有自訂元素架構|若為 True，表示網域類別具有自訂元素架構|
|為自訂|如果您想要為此網域類別撰寫自己的序列化和還原序列化程式碼，請將此值設定為 **True** 。<br /><br /> 建立解決方案並調查錯誤，以探索詳細的指示。|
|領域類別|此類別資料節點適用的網域類別。 唯讀。|
|元素名稱|這個類別之元素的 Xml 節點名稱。 預設值是網域類別名稱的小寫版本。|
|標記屬性名稱|要包含參考之「標記」元素中使用的屬性名稱。 如果空白，則會使用索引鍵屬性或識別碼的名稱。<br /><br /> 在此範例中為 "name"：  `<personMoniker name="/Mike Nash"/>`|
|標記元素名稱|Xml 專案的名稱，此專案是用來參考這個類別的專案的名字標記。<br /><br /> 預設值是以 "名字" 尾碼的類別名稱的小寫版本。 例如： `personMoniker` 。|
|標記類型名稱|為此類別的專案產生的 xsd 型別名稱。 XSD 位於 Dsl\Generated 程式 **代碼 \\ \* 架構 .xsd** 中|
|序列化識別碼|若為 True，則表示專案 GUID 包含在檔案中。 如果沒有標示 **為「標記為** 」的屬性，而且 DSL 定義此類別的參考關聯性，則必須為 true。|
|類型名稱|在 xsd 中，從指定的網域類別產生的 xml 型別名稱。|
|備註|與此元素相關的非正式附注|

### <a name="xml-property-data"></a>Xml 屬性資料

Xml 屬性節點可在類別節點下找到。

|屬性|描述|
|-|-|
|網域屬性|套用 xml 序列化設定資料的屬性。 唯讀。|
|是標記索引鍵|若為 True，則會使用屬性做為索引鍵，以建立參考這個網域類別之實例的名字標記。|
|為標記辨識符號|若為 True，則會使用屬性在名字標記中建立限定詞。 如果為 false，且此網域類別的 SerializeId 不是 true，則會以內嵌樹狀結構中父元素的標記來限定專案名稱。|
|表示法|如果是屬性，則會將屬性序列化為 xml 屬性;如果專案，則會將它序列化為元素;如果忽略，則不會序列化。|
|Xml 名稱|用於表示屬性之 xml 屬性或元素的名稱。 根據預設，這是網域屬性名稱的小寫版本。|
|備註|與此元素相關的非正式附注|

### <a name="xml-role-data"></a>Xml 角色資料

角色資料節點可在來源類別節點下找到。

|屬性|描述|
|-|-|
|具有自訂的標記|如果您想要提供自己的程式碼來產生及解析可跨越此關聯性的名字組，請將此設為 true。<br /><br /> 如需詳細指示，請建立解決方案，然後按兩下錯誤訊息。|
|領域關聯|指定套用這些選項的關聯性。 唯讀。|
|省略元素|若為 true，則會從架構中省略對應至來源角色的 XML 節點。<br /><br /> 如果來源和目標類別之間有多個關聯性，此角色節點會區分屬於這兩個關聯性的連結。 因此，在此情況下，建議您不要設定此選項。|
|角色元素名稱|指定衍生自來源角色之 XML 元素的名稱。 預設值為角色屬性名稱。|
|使用完整格式|若為 true，則會在代表關聯性的 XML 節點中包含每個目標元素或標記。 如果關聯性有自己的網域屬性，則應該設定為 true。|

## <a name="see-also"></a>另請參閱

- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [從特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)
