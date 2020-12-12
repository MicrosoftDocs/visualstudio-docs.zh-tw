---
title: 逐步解說：使用文字範本產生程式碼
description: 瞭解程式碼產生可讓您產生強型別的程式碼，但在來源模型變更時，也可以輕鬆地變更程式碼。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a39630f8a12ad2c1d7d2bc89f6830fc694e89087
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360984"
---
# <a name="walkthrough-generate-code-by-using-text-templates"></a>逐步解說：使用文字範本產生程式碼

程式碼產生可讓您產生強類型的程式碼，而且可以在來源模型變更時輕鬆地進行變更。 這與撰寫可接受組態檔的完全泛型程式的替代技術相反，它更具彈性，但不容易讀取和變更程式碼，也不會有這樣的良好效能。 本逐步解說示範這項優點。

## <a name="typed-code-for-reading-xml"></a>讀取 XML 的類型程式碼

System.Xml 命名空間提供各種工具來載入 XML 文件，然後在記憶體中自由進行巡覽。 不幸的是，所有節點的類型都相同，即 XmlNode。 因此，很容易產生程式設計錯誤，例如預期會有錯誤類型的子節點，或錯誤的屬性。

在此範例專案中，範本會讀取範例 XML 檔案，並產生對應到每個節點類型的類別。 在手動撰寫的程式碼中，您可以使用這些類別來巡覽 XML 檔案。 您也可以在使用相同節點類型的任何其他檔案上執行應用程式。 範例 XML 檔案的目的是要提供您想要應用程式處理之所有節點類型的範例。

> [!NOTE]
> 包含在 Visual Studio 中的應用程式 [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe)可從 XML 檔案產生強型別類別。 這裡示範的範本僅當成範例使用。

以下是範例檔案：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<catalog>
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>
  </artist>
  <artist id ="Euan%20Garden" name="Euan Garden">
    <song id ="GardenScottishCountry">Scottish Country Garden</song>
  </artist>
</catalog>
```

在此逐步解說所建構的專案中，您可以撰寫如下的程式碼，而且 IntelliSense 會在您輸入時提示您使用正確的屬性和子名稱︰

```csharp
Catalog catalog = new Catalog(xmlDocument);
foreach (Artist artist in catalog.Artist)
{
  Console.WriteLine(artist.name);
  foreach (Song song in artist.Song)
  {
    Console.WriteLine("   " + song.Text);
  }
}
```

這與您可以不使用範本撰寫的不具類型程式碼相反︰

```csharp
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");
foreach (XmlNode artist in catalog.SelectNodes("artist"))
{
    Console.WriteLine(artist.Attributes["name"].Value);
    foreach (XmlNode song in artist.SelectNodes("song"))
    {
         Console.WriteLine("   " + song.InnerText);
     }
}
```

在強型別版本中，XML 架構的變更會導致類別的變更。 編譯器會反白顯示必須變更的應用程式程式碼部分。 在使用泛型 XML 程式碼的不具類型版本中，沒有這類支援。

在此專案中，單一範本檔案是用來產生可產生類型版本的類別。

## <a name="set-up-the-project"></a>設定專案

### <a name="create-or-open-a-c-project"></a>建立或開啟 C# 專案

您可以將這項技術套用至任何程式碼專案。 此逐步解說使用 C# 專案，並且基於測試，我們會使用主控台應用程式。

1. 在 [檔案] 功能表 **上，按一下** [ **新增** ]，然後按一下 [ **專案**]。

2. 按一下 []  節點，然後按一下 [範本]  窗格中的 [主控台應用程式] 

### <a name="add-a-prototype-xml-file-to-the-project"></a>將原型 XML 檔案新增至專案

此檔案的目的是要提供您想要應用程式可讀取之 XML 節點類型的範例。 它可以是將用於測試應用程式的檔案。 範本會為此檔案中的每個節點類型產生 C# 類別。

此檔案應該是專案的一部分，讓範本可以讀取它，但它不會內建到編譯的應用程式中。

1. 在 **方案總管** 中，以滑鼠右鍵按一下專案，按一下 [ **加入** ]，然後按一下 [ **新增專案**]。

2. 在 [加入新項目]  對話方塊中，從 [範本]  窗格中選取 [XML 檔案]  。

3. 將範例內容新增至檔案。

4. 在這個逐步解說中，將檔案命名為 `exampleXml.xml`。 將檔案的內容設定成上一節中所示範的 XML。

### <a name="add-a-test-code-file"></a>新增測試程式碼檔案

將 C# 檔案新增至您的專案，並在其中撰寫您可撰寫的程式碼範例。 例如：

```csharp
using System;
namespace MyProject
{
  class CodeGeneratorTest
  {
    public void TestMethod()
    {
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");
      foreach (Artist artist in catalog.Artist)
      {
        Console.WriteLine(artist.name);
        foreach (Song song in artist.Song)
        {
          Console.WriteLine("   " + song.Text);
} } } } }
```

在這個階段，無法編譯此程式碼。 當您撰寫範本時，會產生可讓它成功的類別。

更完整的測試可以針對範例 XML 檔案的已知內容，檢查這個測試函式的輸出。 但在本逐步解說中，只要編譯測試方法即可。

### <a name="add-a-text-template-file"></a>新增文字範本檔案

新增文字模板檔案，並將輸出延伸模組設定為 *.cs*。

1. 在方案總管 中，以滑鼠右鍵按一下專案，並按一下 [加入] ，然後按一下 [新項目] 。

2. 在 [加入新項目]  對話方塊中，從 [範本]  窗格中選取 [文字範本]  。

    > [!NOTE]
    > 請確定您新增的是「文字範本」，而非「前置處理過的文字範本」。

3. 在檔案的範本指示詞中，將 `hostspecific` 屬性變更為 `true`。

     這種變更可讓範本程式碼取得 Visual Studio 服務的存取權。

4. 在輸出指示詞中，將擴充屬性變更為 ".cs"，讓範本產生 C# 檔案。 在 Visual Basic 專案中，您會將它變更 ".vb"。

5. 儲存檔案。 在這個階段，文字範本檔案應該會包含這幾行︰

    ```
    <#@ template debug="false" hostspecific="true" language="C#" #>
    <#@ output extension=".cs" #>
    ```

請注意，.cs 檔案會以範本檔案的子項目形式出現在方案總管中。 按一下範本檔案名稱旁邊的 [+]，就可以看到它。 只要儲存或將焦點移離範本檔案，就會從範本檔案產生此檔案。 產生的檔案將會編譯為專案的一部分。

為了方便起見，在您開發範本檔案時，請排列範本檔案和所產生檔案的時間範圍，讓您可以看到它們彼此相鄰。 這可讓您立即看到範本的輸出。 您也會發現在範本產生無效的 C# 程式碼時，錯誤就會出現在錯誤訊息視窗中。

只要儲存範本檔案，就會遺失您直接在所產生檔案中執行的任何編輯。 因此，您應該避免編輯所產生的檔案，或只在簡短實驗時進行編輯。 IntelliSense 運作時，有時適合在產生的檔案中嘗試簡短的程式碼片段，然後將它複製至範本檔案。

## <a name="develop-the-text-template"></a>開發文字模板

除非正確地編譯並執行測試程式碼，否則我們都會遵循敏捷式開發的最佳建議，透過較少的步驟來開發範本、清除每個增量的一些錯誤。

### <a name="prototype-the-code-to-be-generated"></a>要產生之程式碼的原型

測試程式碼需要檔案中每個節點的類別。 因此，如果您將這幾行附加至範本並儲存，某些編譯錯誤將會消失︰

```csharp
class Catalog {}
class Artist {}
class Song {}
```

這可協助您了解所需的項目，但宣告應該是從範例 XML 檔案的節點類型所產生。 刪除範本中的這些實驗行。

### <a name="generate-application-code-from-the-model-xml-file"></a>從模型 XML 檔案產生應用程式碼

若要讀取 XML 檔案，並產生類別宣告，請將範本內容取代為下列範本程式碼︰

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#
 XmlDocument doc = new XmlDocument();
 // Replace this file path with yours:
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
#>
  public partial class <#= node.Name #> {}
<#
 }
#>
```

將檔案路徑取代為您專案的正確路徑。

請注意程式碼區塊分隔符號 `<#...#>`。 這些分隔符號會括住產生文字的程式碼片段。 運算式區塊分隔符號 `<#=...#>` 會括住可評估為字串的運算式。

當您撰寫可產生應用程式之原始程式碼的範本時，將會處理兩個個別的程式文字。 每次儲存範本或將焦點移至另一個視窗時，都會執行程式碼區塊分隔符號內的程式。 它所產生的文字 (出現在分隔符號外部) 會複製到所產生的檔案，並成為應用程式碼的一部分。

`<#@assembly#>` 指示詞與參考的行為類似，即讓範本程式碼可以使用組件。 範本所看到的組件清單，與應用程式專案中的參考清單不同。

`<#@import#>` 指示詞的作用就像 `using` 陳述式，可讓您在匯入的命名空間中使用類別的簡短名稱。

遺憾的是，雖然此範本會產生程式碼，但是會針對範例 XML 檔案中的每個節點產生類別宣告，因此，如果有數個 `<song>` 節點執行個體，則會出現數個類別宣告。

### <a name="read-the-model-file-then-generate-the-code"></a>讀取模型檔案，然後產生程式碼

許多文字範本都遵循範本第一個部分讀取原始程式檔的模式，而第二個部分會產生範本。 我們需要讀取整個範例檔案來彙總它所包含的節點類型，然後產生類別宣告。 需要另一個 `<#@import#>`，讓我們可以使用 `Dictionary<>:`

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
<#
 // Read the model file
 XmlDocument doc = new XmlDocument();
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 Dictionary <string, string> nodeTypes =
        new Dictionary<string, string>();
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   nodeTypes[node.Name] = "";
 }
 // Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= nodeName #> {}
<#
 }
#>
```

### <a name="add-an-auxiliary-method"></a>新增輔助方法

類別功能控制區塊是您可在其中定義輔助方法的區塊。 區塊是以 `<#+...#>` 進行區隔，而且必須顯示為檔案中的最後一個區塊。

如果您偏好使用以大寫字母開頭的類別名稱，則可以將範本的最後一個部分取代為下列範本程式碼︰

```
// Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= UpperInitial(nodeName) #> {}
<#
 }
#>
<#+
 private string UpperInitial(string name)
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }
#>
```

在這個階段中，產生的 *.cs* 檔案包含下列宣告：

```csharp
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

您可以使用相同的方法新增更多詳細資料 (例如子節點、屬性和內部文字的屬性)。

### <a name="access-the-visual-studio-api"></a>存取 Visual Studio API

設定指示詞的 `hostspecific` 屬性 `<#@template#>` 可讓範本取得 Visual Studio API 的存取權。 範本可以使用此項目來取得專案檔的位置，以避免在範本程式碼中使用絕對檔案路徑。

```
<#@ template debug="false" hostspecific="true" language="C#" #>
...
<#@ assembly name="EnvDTE" #>
...
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
// Open the prototype document.
XmlDocument doc = new XmlDocument();
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
```

## <a name="complete-the-text-template"></a>完成文字模板

下列範本內容會產生允許編譯和執行測試程式碼的程式碼。

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{
<#
 // Map node name --> child name --> child node type
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();

 // The Visual Studio host, to get the local file path.
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
 // Open the prototype document.
 XmlDocument doc = new XmlDocument();
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
 // Inspect all the nodes in the document.
 // The example might contain many nodes of the same type,
 // so make a dictionary of node types and their children.
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   Dictionary<string, XmlNodeType> subs = null;
   if (!nodeTypes.TryGetValue(node.Name, out subs))
   {
     subs = new Dictionary<string, XmlNodeType>();
     nodeTypes.Add(node.Name, subs);
   }
   foreach (XmlNode child in node.ChildNodes)
   {
     subs[child.Name] = child.NodeType;
   }
   foreach (XmlNode child in node.Attributes)
   {
     subs[child.Name] = child.NodeType;
   }
 }
 // Generate a class for each node type.
 foreach (string className in nodeTypes.Keys)
 {
    // Capitalize the first character of the name.
#>
    partial class <#= UpperInitial(className) #>
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }

<#
    // Generate a property for each child.
    foreach (string childName in nodeTypes[className].Keys)
    {
      // Allow for different types of child.
      switch (nodeTypes[className][childName])
      {
         // Child nodes:
         case XmlNodeType.Element:
#>
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }
<#
         break;
         // Child attributes:
         case XmlNodeType.Attribute:
#>
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }
<#
         break;
         // Plain text:
         case XmlNodeType.Text:
#>
      public string Text  { get { return thisNode.InnerText; } }
<#
         break;
       } // switch
     } // foreach class child
  // End of the generated class:
#>
   }
<#
 } // foreach class

   // Add a constructor for the root class
   // that accepts an XML filename.
   string rootClassName = doc.SelectSingleNode("*").Name;
#>
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}
<#+
   private string UpperInitial(string name)
   {
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);
   }
#>
```

### <a name="run-the-test-program"></a>執行測試程式

在主控台應用程式的 main 中，下列數行會執行 test 方法。 請按 F5 以偵錯模式執行程式：

```csharp
using System;
namespace MyProject
{
  class Program
  {
    static void Main(string[] args)
    {
      new CodeGeneratorTest().TestMethod();
      // Allow user to see the output:
      Console.ReadLine();
    }
  }
}
```

### <a name="write-and-update-the-application"></a>撰寫和更新應用程式

應用程式現在可以使用產生的類別透過強類型樣式進行撰寫，而不是使用泛型 XML 程式碼。

XML 結構描述變更時，可以輕鬆地產生新的類別。 編譯器會告訴開發人員必須更新的應用程式碼。

若要在變更範例 XML 檔案時重新產生類別，請按一下 [ **轉換所有範本** ] **方案總管** 工具列。

## <a name="conclusion"></a>結論

本逐步解說示範數個技術以及程式碼產生的優點︰

- *「程式碼產生」* (code generation) 是從 *「模型」*(model) 建立應用程式之原始程式碼的各個部分。 此模型以適合應用程式網域的表單來包含資訊，而且可能會隨著應用程式的存留期變更。

- 強類型是程式碼產生的一個優點。 雖然此模型以更適合使用者的表單來呈現資訊，但是產生的程式碼可讓應用程式的其他部分使用一組類型資訊來處理資訊。

- 撰寫新程式碼以及更新結構描述時，IntelliSense 和編譯器都可以協助您建立遵守模型結構描述的程式碼。

- 將單一簡單範本檔案新增至專案，可以提供這些優點。

- 文字範本可以更快速且漸進地進行開發和測試。

在此逐步解說中，實際上是從模型執行個體產生程式碼，這是應用程式將處理之 XML 檔案的代表性範例。 在更正式的方法中，XML 結構描述會是範本的輸入，而形式為 .xsd 檔案或網域特定語言定義。 該方法可讓範本更輕鬆地判斷特性 (例如關聯性的多重性)。

## <a name="troubleshoot-the-text-template"></a>對文字模板進行疑難排解

如果您在 [錯誤清單] 中看到範本轉換或編譯錯誤，或未正確地產生輸出檔案，則可以使用[使用 TextTransform 公用程式產生檔案](../modeling/generating-files-with-the-texttransform-utility.md)中所述的技術對文字範本進行疑難排解。

## <a name="see-also"></a>請參閱

- [使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)
