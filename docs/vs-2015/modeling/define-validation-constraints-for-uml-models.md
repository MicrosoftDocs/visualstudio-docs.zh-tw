---
title: 定義 UML 模型的驗證條件約束 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 258fc138f032d34e57df69386b6849fc3a0650a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547585"
---
# <a name="define-validation-constraints-for-uml-models"></a>定義 UML 模型的驗證條件約束
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以定義驗證條件約束，測試模型是否符合您所指定的條件。 例如，您可以定義條件約束，確保使用者不會建立繼承關聯性的迴圈。 當使用者嘗試開啟或儲存模型時，會叫用該條件約束；該條件約束也可手動叫用。 如果條件約束失敗，您定義的錯誤訊息會加入錯誤視窗。 您可以將這些條件約束封裝成 Visual Studio 整合擴充功能 ([VSIX](https://msdn.microsoft.com/library/dd393694(VS.100).aspx))，然後將它散發給其他的 Visual Studio 使用者。

 您也可以定義條件約束，對照外部資源 (例如資料庫) 來驗證模型。 如果您想要針對分層圖驗證程式代碼，請參閱 [將自訂架構驗證新增至分層](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)圖。

 若要查看哪些 Visual Studio 版本支援 UML 模型，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="requirements"></a>需求
 請參閱 [需求](../modeling/extend-uml-models-and-diagrams.md#Requirements)。

 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="applying-validation-constraints"></a>套用驗證條件約束
 下列三種狀況會套用驗證條件約束：儲存模型時、開啟模型時，以及按一下 [架構] **** 功能表上的 [驗證 UML 模型] 時 **** 。 儘管您通常會將每個條件約束定義成套用到多個案例，但在每個案例中，將只會套用為該案例所定義的條件約束。

 驗證錯誤會在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 錯誤視窗中回報，您可以按兩下錯誤，以選取錯誤的模型項目。

 如需套用驗證的詳細資訊，請參閱 [驗證 UML 模型](../modeling/validate-your-uml-model.md)。

## <a name="defining-a-validation-extension"></a>定義驗證擴充功能
 若要建立 UML 設計工具的驗證擴充功能，您必須建立一個類別來定義驗證約束條件，並且將該類別內嵌在 Visual Studio 整合擴充功能 (VSIX)。 VSIX 會做為容器，可安裝該條件約束。 定義驗證擴充功能有兩個替代方法：

- **使用專案範本在其特有的 VSIX 中建立驗證擴充功能。** 這是較快的方法。 當您不想合併您的處理驗證條件約束與其他類型的擴充功能 (例如功能表命令、自訂工具箱項目或軌跡處理常式) 時，即可使用此方法。 您可以在一個類別中定義多個條件約束。

- **建立個別的驗證類別及 VSIX 專案。** 如果您想要將數種類型的擴充功能合併成相同的 VSIX，即可使用此方法。 例如，如果您的功能表命令預期模型要觀察特定的條件約束，可以將它內嵌至與驗證方法相同的 VSIX。

#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>在自己的 VSIX 建立驗證擴充功能

1. 在 [新增專案] **** 對話方塊的 [模型專案] **** 之下，選取 [驗證擴充功能] ****。

2. 在新的專案中開啟 **.cs** 檔案，並修改類別來實作您的驗證條件約束。

    如需詳細資訊，請參閱 [評估驗證條件約束](#Implementing)。

   > [!IMPORTANT]
   > 請確定您的 **.cs** 檔案包含下列 `using` 陳述式：
   >
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

3. 您可以藉由定義新的方法來加入其他條件約束。 若要指定某方法做為驗證方法，必須和初始驗證方法一樣標記屬性。

4. 按 F5 來測試您的條件約束。 如需詳細資訊，請參閱 [執行驗證條件約束](#Executing)。

5. 複製您的專案所建立的檔案**bin \\ \* \\ \* ** ，以在另一部電腦上安裝功能表命令。 如需詳細資訊，請參閱 [安裝和解除安裝擴充功能](#Installing)。

   當您新增其他 **.cs** 檔案時，通常會需要下列 `using` 陳述式：

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Uml.Classes;

```

 以下是替代程序：

#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>在類別庫專案中建立個別的驗證條件約束

1. 建立類別庫專案，將它加入現有的 VSIX 方案，或是建立新的方案。

    1. 在 [檔案]**** 功能表，選擇 [新增]****、[專案]****。

    2. 在 [已安裝的範本] **** 下，展開 [Visual C#] **** 或 [Visual Basic] ****，然後在中間的資料行中選擇 [類別庫] ****。

2. 除非您的方案已經包含 VSIX 專案，否則請建立一個：

    1. 在 **方案總管**中，在解決方案的捷徑功能表上，選擇 [加入]  **** 和 [新增專案] ****。

    2. 在 [已安裝的範本] **** 下，展開 [Visual C#] **** 或 [Visual Basic] ****，然後選擇 [擴充性] ****。 在中間的資料行中，按一下 [VSIX 專案] ****。

3. 將 VSIX 專案設定為方案的啟始專案。

    - 在方案總管中，在 VSIX 專案的快捷方式功能表上，選擇 [ **設定為啟始專案**]。

4. 在 **source.extension.vsixmanifest**的 [內容] **** 下，加入類別庫專案做為 MEF 元件：

    1. 在 [中繼資料] **** 索引標籤上，設定 VSIX 的名稱。

    2. 在 [安裝目標] **** 索引標籤上，設定 Visual Studio 版本做為目標。

    3. 在 [資產] **** 索引標籤上，選擇 [新增] ****，然後在對話方塊中設定：

         **類型**  = **MEF 元件**

         **來源**  = **目前方案中的專案**

         **專案**  = *您的類別庫專案*

#### <a name="to-define-the-validation-class"></a>定義驗證類別

1. 如果您已經從驗證專案範本使用其特有的 VSIX，建立了驗證類別，就無須執行此程序。

2. 在驗證類別專案中，在下列 [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] 組件中加入參考：

     `Microsoft.VisualStudio.Modeling.Sdk.[version]`

     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

     `Microsoft.VisualStudio.Uml.Interfaces`

     `System.ComponentModel.Composition`

3. 在包含類似下列範例之程式碼的類別庫專案中加入檔案。

    - 每個驗證條件約束都會包含在標記有特定屬性的方法中。 該方法會接受模型項目類型的參數。 當叫用驗證時，驗證架構會將每個驗證方法套用到所有符合其參數類型的模型項目。

    - 您可以將這些方法置入任何類別及命名空間中。 依您的喜好變更這些方法。

    ```
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using Microsoft.VisualStudio.Modeling.Validation;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.Uml.Classes;
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.

    namespace Validation
    {
      public class MyValidationExtensions
      {
        // SAMPLE VALIDATION METHOD.
        // All validation methods have the following attributes.
        [Export(typeof(System.Action<ValidationContext, object>))]
        [ValidationMethod(
           ValidationCategories.Save
         | ValidationCategories.Open
         | ValidationCategories.Menu)]
        public void ValidateClassNames
          (ValidationContext context,
           // This type determines what elements
           // will be validated by this method:
           IClass elementToValidate)
        {
          // A validation method should not change the model.

          List<string> attributeNames = new List<string>();
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)
          {
            string name = attribute.Name;
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))
            {
              context.LogError(
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),
                "001", elementToValidate);
            }
            attributeNames.Add(name);
          }

        }
        // Add more validation methods for different element types.
      }
    }
    ```

## <a name="executing-a-validation-constraint"></a><a name="Executing"></a> 執行驗證條件約束
 若為測試用途，請在偵錯模式中執行您的驗證方法。

#### <a name="to-test-the-validation-constraint"></a>測試驗證條件約束

1. 按 **F5**，或在 [偵錯] **** 功能表上，選擇 [開始偵錯] ****。

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗執行個體隨即啟動。

     **疑難排解**：如果新的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 未啟動：

    - 您如有多個專案，請確定已將 VSIX 專案設定為解決方案的啟始專案。

    - 在方案總管的啟始專案或唯一專案的捷徑功能表上，選擇 [屬性] ****。 在專案屬性編輯器中，選取 [ **調試** ] 索引標籤。請確定 [ **啟動外部程式** ] 欄位中的字串是的完整路徑名稱 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，通常是：

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. 在實驗性 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中，開啟或建立模型專案，並開啟或建立模型圖表。

3. 若要為上節中的範例條件約束設定測試：

    1. 開啟類別圖。

    2. 建立類別，並加入兩個同名的屬性。

4. 在圖表上任何位置的捷徑功能表上，選擇 [驗證] ****。

5. 模型中的任何錯誤都會在錯誤視窗中回報。

6. 按兩下錯誤報告。 如果報告中提到的項目顯示在畫面上，會以反白顯示。

     **疑難排解**：如果 [驗證] **** 命令未出現在功能表上，請確定：

    - 驗證專案在 VSIX 專案 **source.extensions.manifest** 的 [資產] **** 索引標籤中列為 MEF 元件。

    - 正確的 `Export` 和 `ValidationMethod` 屬性會附加至驗證方法。

    - `ValidationCategories.Menu` 會包含在屬性的引數中 `ValidationMethod` ，並使用邏輯 OR ( # A0) 來與其他值組成。

    - 所有 `Import` 和 `Export` 屬性的參數都有效。

## <a name="evaluating-the-constraint"></a><a name="Implementing"></a> 評估條件約束
 驗證方法應指定您要套用的驗證條件約束是 true 或 false。 如果是 true，將不會執行任何動作。 如果是 false，應使用 `ValidationContext` 參數所提供的方法報告錯誤。

> [!NOTE]
> 驗證方法不應該變更模型。 無法保證條件約束的執行時間或執行順序。 如果您必須在同一驗證回合中連續執行的驗證方法之間傳遞資訊，可以使用 [協調多個驗證](#ContextCache)下所述的內容快取。

 例如，如果要確定每種類型 (類別、介面或列舉) 的名稱長度至少有三個字元，可以使用這個方法：

```
public void ValidateTypeName(ValidationContext context, IType type)
{
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)
  {
    context.LogError(
      string.Format("Type name {0} is too short", type.Name),
               "001", type);
   }
 }
```

 如需可以用來巡覽和讀取模型之方法與類型的相關資訊，請參閱 [Programming with the UML API](../modeling/programming-with-the-uml-api.md) 。

### <a name="about-validation-constraint-methods"></a>關於驗證條件約束方法
 每個驗證條件約束由下列形式的方法定義：

```
[Export(typeof(System.Action<ValidationContext, object>))]
 [ValidationMethod(ValidationCategories.Save
  | ValidationCategories.Menu
  | ValidationCategories.Open)]
public void ValidateSomething
  (ValidationContext context, IClassifier elementToValidate)
{...}
```

 每個驗證方法的參數與屬性如下：

|簽名|描述|
|-|-|
|`[Export(typeof(System.Action <ValidationContext, object>))]`|使用 Managed Extensibility Framework (MEF) 將方法定義為驗證條件約束。|
|`[ValidationMethod (ValidationCategories.Menu)]`|指定驗證的執行時機。 如果您想要結合一個以上的選項，請使用位或 ( # A0) 。<br /><br /> `Menu` = 由 [驗證] 功能表叫用。<br /><br /> `Save` = 儲存模型時叫用。<br /><br /> `Open` = 開啟模型時叫用。 `Load` = 儲存模型時叫用，但如有違反，將會警告使用者，其無法重新開啟此模型。 這也會在剖析模型前的載入時呼叫。|
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|以條件約束所要套用的目標項目類型取代第二個參數 `IElement` 。 指定類型的所有項目將會叫用此條件約束方法。<br /><br /> 方法的名稱並不重要。|

 您可以在第二個參數中，以各種不同類型定義所需數量的驗證方法。 叫用驗證時，會對所有符合參數類型的模型項目，呼叫每個驗證方法。

### <a name="reporting-validation-errors"></a>報告驗證錯誤
 如果要建立錯誤報告，請使用 `ValidationContext`所提供的方法：

 `context.LogError("error string", errorCode, elementsWithError);`

- `"error string"` 會出現在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 錯誤清單中

- `errorCode` 為字串，是錯誤的唯一識別碼

- `elementsWithError` 可指出模型中的項目。 當使用者按兩下錯誤報告時，會選取代表該項目的圖形。

  `LogError(),``LogWarning()`並 `LogMessage()` 將訊息放在錯誤清單的不同區段中。

## <a name="how-validation-methods-are-applied"></a>如何套用驗證方法
 驗證會套用到模型中的每個項目，包括關聯性和較大項目的組件，例如類別的屬性及作業的參數。

 每個驗證方法會套用到符合其第二個參數中之類型的各個項目。 這表示，舉例來說，如果您以 `IUseCase` 的第二個參數及另一個具有其超級類型 `IElement`的參數來定義驗證方法，這兩種方法都會套用到模型中的每一個使用案例。

 型別的階層會在 [UML 模型專案類型](../modeling/uml-model-element-types.md)中摘要。

 您也可以透過下列關聯性存取項目。 例如，如果您要定義 `IClass`的驗證方法，可以重複使用其所具有的屬性：

```
public void ValidateTypeName(ValidationContext context, IClass c)
{
   foreach (IProperty property in c.OwnedAttributes)
   {
       if (property.Name.Length < 3)
       {
            context.LogError(
                 string.Format(
                        "Property name {0} is too short",
                        property.Name),
                 "001", property);
        }
   }
}
```

### <a name="creating-a-validation-method-on-the-model"></a>建立模型的驗證方法
 如果要確保驗證方法在每個驗證回合都只會呼叫一次，可以驗證 `IModel`：

```
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{  foreach (IElement element in model.OwnedElements)
   { ...
```

### <a name="validating-shapes-and-diagrams"></a>驗證圖形及圖表
 因為驗證方法的主要目的在驗證模型，所以不會對顯示項目 (例如圖表及圖形) 叫用。 但您可以使用圖表內容存取目前的圖表。

 在您的驗證類別中，將 `DiagramContext` 宣告為匯入的屬性：

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
...
[Import]
public IDiagramContext DiagramContext { get; set; }
```

 在驗證方法中，您可以使用 `DiagramContext` 存取目前的焦點圖表 (如有提供)：

```
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;
  if (focusDiagram != null)
  {
    foreach (IShape<IUseCase> useCaseShape in
              focusDiagram.GetChildShapes<IUseCase>())
    { ...
```

 如果要記錄錯誤，因為您無法將圖形傳遞給 `LogError`，所以必須取得圖形所代表的模型項目：

```
IUseCase useCase = useCaseShape.Element;
context.LogError(... , usecase);
```

### <a name="coordinating-multiple-validations"></a><a name="ContextCache"></a> 協調多個驗證
 舉例來說，當使用者從 [圖表] 功能表中叫用驗證時，會將每個驗證方法套用到各個模型項目。 這表示在一次引動驗證架構中，同一個方法可能會多次套用到不同的項目。

 這顯現出驗證在處理項目間之關連性方面的問題。 舉例來說，您撰寫了一個驗證，其先從使用案例開始，再周遊 **include** 關聯性，以驗證沒有迴圈。 但當此方法套用到具有許多 **include** 連結之模型中的各個使用案例時，可能會重複處理模型的同一個區域。

 為避免此情況，驗證回合中會有一個內容快取用來保留資訊。 您可以使用此內容快取，在驗證方法不同的執行回合之間傳遞資訊。 例如，您可以儲存已經在這個驗證回合中處理過之項目的清單。 此快取會在每個驗證回合開始時建立，無法用在不同的驗證回合之間傳遞資訊。

|語法|描述|
|-|-|
|`context.SetCacheValue<T> (name, value)`|儲存值|
|`context.TryGetCacheValue<T> (name, out value)`|取得值。 如果成功，會傳回 true。|
|`context.GetValue<T>(name)`|取得值。|
|`Context.GetValue<T>()`|取得指定類型的值。|

## <a name="installing-and-uninstalling-an-extension"></a><a name="Installing"></a> 安裝和卸載擴充功能
 您可以同時在自己的電腦和其他電腦上安裝 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 擴充功能。

#### <a name="to-install-an-extension"></a>安裝擴充功能

1. 在您的電腦中，尋找 VSIX 專案所建置的 **.vsix** 檔案。

    1. 在 **方案總管**之 VSIX 專案的捷徑功能表上，選擇 [在 Windows 檔案總管開啟資料夾] ****。

    2. 找出檔案**bin \\ \* \\ ** _yourproject。_**.vsix**

2. 將 **.vsix** 檔案複製到要安裝擴充功能的目標電腦。 這可以是您自己的電腦或其他電腦。

    - 目的電腦必須有 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 您在 **extension.vsixmanifest**中指定的其中一個版本。

3. 在目標電腦上開啟 **.vsix** 檔案。

     [Visual Studio 擴充功能安裝程式]**** 會隨即開啟並安裝擴充功能。

4. 啟動或重新啟動 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]。

#### <a name="to-uninstall-an-extension"></a>解除安裝擴充功能

1. 在 [ **工具** ] 功能表中選擇 [ **擴充功能和更新**]。

2. 展開 [已安裝的擴充功能] ****。

3. 選取擴充功能，然後選擇 [解除安裝] ****。

   在很少見的情況下，錯誤的擴充功能會無法載入，並且在錯誤視窗中建立報表，但不會顯示在擴充管理員中。 在這種情況下，您可以從下列位置刪除副檔名： *% LocalAppData%* 通常是*DriveName*： \Users \\ *UserName*\AppData\Local：

   *% LocalAppData%* **\Microsoft\VisualStudio \\ [version] \Extensions**

## <a name="example"></a><a name="Example"></a> 範例
 這個範例會在項目之間的相依性關聯性中尋找迴圈。

 它會在儲存及驗證功能表命令時執行驗證。

```
/// <summary>
/// Verify that there are no loops in the dependency relationsips.
/// In our project, no element should be a dependent of itself.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">Element to start validation from.</param>
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu
     | ValidationCategories.Save | ValidationCategories.Open)]
public void NoDependencyLoops(ValidationContext context, INamedElement element)
{
    // The validation framework will call this method
    // for every element in the model. But when we follow
    // the dependencies from one element, we will validate others.
    // So we keep a list of the elements that we don't need to validate again.
    // The list is kept in the context cache so that it is passed
    // from one execution of this method to another.
    List<INamedElement> alreadySeen = null;
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))
    {
       alreadySeen = new List<INamedElement>();
       context.SetCacheValue("No dependency loops", alreadySeen);
    }

    NoDependencyLoops(context, element,
                new INamedElement[0], alreadySeen);
}

/// <summary>
/// Log an error if there is any loop in the dependency relationship.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">The element to be validated.</param>
/// <param name="dependants">Elements we've followed in this recursion.</param>
/// <param name="alreadySeen">Elements that have already been validated.</param>
/// <returns>true if no error was detected</returns>
private bool NoDependencyLoops(ValidationContext context,
    INamedElement element, INamedElement[] dependants,
    List<INamedElement> alreadySeen)
{
    if (dependants.Contains(element))
    {
        context.LogError(string.Format("{0} should not depend on itself", element.Name),
        "Fabrikam.UML.NoGenLoops", // unique code for this error
        dependants.SkipWhile(e => e != element).ToArray());
            // highlight elements that are in the loop
        return false;
    }
    INamedElement[] dependantsPlusElement =
        new INamedElement[dependants.Length + 1];
    dependants.CopyTo(dependantsPlusElement, 0);
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;

    if (alreadySeen.Contains(element))
    {
        // We have already validated this when we started
        // from another element during this validation run.
        return true;
    }
    alreadySeen.Add(element);

    foreach (INamedElement supplier in element.GetDependencySuppliers())
    {
        if (!NoDependencyLoops(context, supplier,
             dependantsPlusElement, alreadySeen))
        return false;
    }
    return true;
}
```

## <a name="see-also"></a>另請參閱
 [使用 UML API](../modeling/programming-with-the-uml-api.md) [定義和安裝模型擴充](../modeling/define-and-install-a-modeling-extension.md)功能程式設計
