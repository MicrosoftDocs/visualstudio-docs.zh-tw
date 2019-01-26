---
title: 網域指定的語言中的驗證
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 16ff6a60182ec6f3cbaff45bac54a4bec3ffbd52
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932320"
---
# <a name="validation-in-a-domain-specific-language"></a>網域指定的語言中的驗證
身為網域指定的語言 (DSL) 的作者，您可以定義驗證條件約束，以驗證使用者建立的模型是否有意義。 例如，如果您的 DSL 允許使用者繪製人們與其祖先的家譜，您可以撰寫條件約束，確保孩子的出生日期晚於父母的出生日期。

 您可以在儲存模型，它會開啟，以及使用者明確執行時執行驗證條件約束**驗證**功能表命令。 您也可以在程式控制下執行驗證。 例如，您可以執行驗證，以回應屬性值或關聯性的變更。

 驗證是特別重要，如果您正在撰寫文字範本或其他工具來處理使用者的模型。 驗證可確保模型滿足這些工具假設的前置條件。

> [!WARNING]
>  除了擴充功能的功能表命令和軌跡處理常式之外，您也可以將驗證條件約束定義為 DSL 的個別擴充功能。 當使用者安裝 DSL 時，可以另外選擇安裝這些擴充功能。 如需詳細資訊，請參閱 <<c0> [ 藉由使用 MEF 擴充您的 DSL](../modeling/extend-your-dsl-by-using-mef.md)。

## <a name="running-validation"></a>執行驗證
 當使用者編輯模型 (亦即網域指定的語言執行個體) 時，下列動作會執行驗證：

- 以滑鼠右鍵按一下圖表，然後選取**全部驗證**。

- 以滑鼠右鍵按一下您的 DSL，然後選取 [總管] 中的最上層節點**全部驗證**

- 儲存模型。

- 開啟模型。

- 此外，您可以撰寫執行驗證的程式碼，以做為功能表命令的一部分或回應變更。

  任何驗證錯誤會出現在**錯誤清單**視窗。 使用者可以按兩下錯誤訊息，選取造成錯誤的模型項目。

## <a name="defining-validation-constraints"></a>定義驗證條件約束
 您可以將驗證方法加入至 DSL 的網域類別或關聯性，藉此定義驗證條件約束。 當使用者執行驗證或在程式控制下執行驗證時，即會執行部分或所有驗證方法。 每個方法都會套用至其類別的每個執行個體，並且每個類別中可以有數個驗證方法。

 每個驗證方法會報告找到的任何錯誤。

> [!NOTE]
>  驗證方法會報告錯誤，但不會變更模型。 如果您想要調整或避免特定變更，請參閱[驗證的替代方法](#alternatives)。

#### <a name="to-define-a-validation-constraint"></a>定義驗證條件約束

1. 啟用中的驗證**於**節點：

   1.  開啟**Dsl\DslDefinition.dsl**。

   2.  在 [DSL 總管] 中，展開**編輯器**節點，然後選取**驗證**。

   3.  在 [屬性] 視窗中，設定**會使用**屬性，以`true`。 最方便的做法是設定所有屬性。

   4.  按一下 [**轉換所有範本**中**方案總管] 中**工具列。

2. 撰寫一個或多個網域類別或網域關聯性的部分類別定義。 新的程式碼檔案中撰寫這些定義**Dsl**專案。

3. 在每個類別的前面加上下列屬性：

   ```csharp
   [ValidationState(ValidationState.Enabled)]
   ```

   -   根據預設，這個屬性也會啟用衍生類別的驗證。 如果您要停用特定衍生類別的驗證，您可以使用 `ValidationState.Disabled`。

4. 將驗證方法加入至類別。 每個驗證方法可以命名為任何名稱，但只能有一個 <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext> 類型的參數。

    此方法的前面必須加上一個或多個 `ValidationMethod` 屬性：

   ```csharp
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]
   ```

    ValidationCategories 指定何時執行方法。

   例如：

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;

// Allow validation methods in this class:
[ValidationState(ValidationState.Enabled)]
// In this DSL, ParentsHaveChildren is a domain relationship
// from Person to Person:
public partial class ParentsHaveChildren
{
  // Identify the method as a validation method:
  [ValidationMethod
  ( // Specify which events cause the method to be invoked:
    ValidationCategories.Open // On file load.
  | ValidationCategories.Save // On save to file.
  | ValidationCategories.Menu // On user menu command.
  )]
  // This method is applied to each instance of the
  // type (and its subtypes) in a model:
  private void ValidateParentBirth(ValidationContext context)
  {
    // In this DSL, the role names of this relationship
    // are "Child" and "Parent":
     if (this.Child.BirthYear < this.Parent.BirthYear
        // Allow user to leave the year unset:
        && this.Child.BirthYear != 0)
      {
        context.LogError(
             // Description:
                       "Child must be born after Parent",
             // Unique code for this error:
                       "FAB001ParentBirthError",
              // Objects to select when user double-clicks error:
                       this.Child,
                       this.Parent);
    }
  }
```

 請注意有關這個程式碼的下列重點：

- 您可以將驗證方法加入至網域類別或網域關聯性。 針對這些類型的程式碼位於**Dsl\Generated Code\Domain\*.cs**。

- 每個驗證方法會套用至其類別和子類別的每一個執行個體。 在網域關聯性的案例中，每個執行個體是兩個模型項目之間的連結。

- 您無法依任何指定的順序套用驗證方法，也無法依任何預期的順序將每個方法套用至其類別的執行個體。

- 讓驗證方法更新存放區內容通常不是很好的做法，因為這會導致不一致的結果。 相反地，此方法應呼叫 `context.LogError`、`LogWarning` 或 `LogInfo` 來報告任何錯誤。

- 在 LogError 呼叫中，您可以提供模型項目或關聯性連結的清單，以供使用者按兩下錯誤訊息時選取。

- 如需如何讀取程式碼中的模型詳細資訊，請參閱[巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

  此範例會套用至下列網域模型。 ParentsHaveChildren 關聯性具有名為 Child 和 Parent 的角色。

  ![DSL 定義圖&#45;家譜模型](../modeling/media/familyt_person.png)

## <a name="validation-categories"></a>驗證分類
 在 <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> 屬性中，您可以指定何時應執行驗證方法。

|分類|執行|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|使用者叫用 [驗證] 功能表命令時。|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|開啟模型檔時。|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|儲存檔案時。 如果發生驗證錯誤，使用者可以選擇取消儲存作業。|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|儲存檔案時。 如果此分類的方法發生錯誤，則會警告使用者可能無法重新開啟檔案。<br /><br /> 使用此分類的驗證方法，來測試是否有重複的名稱或 ID，或者是否有可能造成載入錯誤的其他情況。|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|呼叫 ValidateCustom 方法時。 此分類的驗證只能從程式碼叫用。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 自訂驗證分類](#custom)。|

## <a name="where-to-place-validation-methods"></a>驗證方法的位置
 對不同的類型套用驗證方法，通常可以達到相同的效果。 例如，您可以將方法加入至 Person 類別，而不是 ParentsHaveChildren 關聯性，再讓方法逐一查看連結：

```
[ValidationState(ValidationState.Enabled)]
public partial class Person
{[ValidationMethod
 ( ValidationCategories.Open
 | ValidationCategories.Save
 | ValidationCategories.Menu
 )
]
  private void ValidateParentBirth(ValidationContext context)
  {
    // Iterate through ParentHasChildren links:
    foreach (Person parent in this.Parents)
    {
        if (this.BirthYear <= parent.BirthYear)
        { ...
```

 **彙總驗證條件約束。** 若要套用驗證可預測的順序，請定義一個驗證方法的擁有者類別，這類的根項目模型上。 這個方法也可讓您將多份錯誤報告彙總成一個訊息。

 其缺點在於合併的方法比較難管理，並且條件約束必須具有相同的 `ValidationCategories`。 因此，建議您盡可能以不同的方法來保留每個條件約束。

 **您可以將值傳入內容快取。** 內容參數具有的字典，您可以在其中放置任意值。 在執行驗證期間都可以使用此字典。 例如，某個驗證方法可能會將錯誤計數保留在內容中，然後使用該內容以避免錯誤視窗中出現太多重複的訊息。 例如：

```csharp
List<ParentsHaveChildren> erroneousLinks;
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))
erroneousLinks = new List<ParentsHaveChildren>();
erroneousLinks.Add(this);
context.SetCacheValue("erroneousLinks", erroneousLinks);
if (erroneousLinks.Count < 5) { context.LogError( ... ); }
```

## <a name="validation-of-multiplicities"></a>多重性驗證
 您的 DSL 會自動產生用於檢查最小多重性的驗證方法。 撰寫程式碼**Dsl\Generated Code\MultiplicityValidation.cs**。 這些方法會啟用驗證時，才會生效**於**DSL 總管 中的節點。

 如果將網域關聯性角色的多重性設定為 1..* 或 1..1，但使用者未建立此關聯性的連結，則會出現驗證錯誤訊息。

 比方說，如果您的 DSL 具有類別 Person 和 Town 和關聯性的關聯性 PersonLivesInTown **1..\\*** 在 Town 角色中，然後針對每個沒有 town 的 Person 會出現錯誤訊息。

## <a name="running-validation-from-program-code"></a>從程式碼執行驗證
 您可以存取或建立 ValidationController 來執行驗證。 如果您想要在錯誤視窗中對使用者顯示的錯誤，請使用 附加至您的圖表之 DocData 的 ValidationController。 例如，如果您要撰寫功能表命令，可以使用命令集類別中的 `CurrentDocData.ValidationController`：

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
partial class MyLanguageCommandSet
{
  private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
  {
   ValidationController controller = this.CurrentDocData.ValidationController;
...
```

 如需詳細資訊，請參閱[＜How to：將命令加入至捷徑功能表](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)。

 您也可以建立獨立的驗證控制器，自行管理錯誤。 例如：

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
Store store = ...;
VsValidationController validator = new VsValidationController(s);
// Validate all elements in the Store:
if (!validator.Validate(store, ValidationCategories.Save))
{
  // Deal with errors:
  foreach (ValidationMessage message in validator.ValidationMessages) { ... }
}
```

## <a name="running-validation-when-a-change-occurs"></a>發生變更時執行驗證
 如果您要確保在模型無效時立即警告使用者，您可以定義執行驗證的存放區事件。 如需存放區事件的詳細資訊，請參閱[事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

 除了驗證程式碼中，自訂程式碼將檔案新增至您**DslPackage**專案，其內容類似下列的範例。 這個程式碼使用連結至文件的 `ValidationController`。 此控制器會顯示驗證錯誤，在 Visual Studio 錯誤清單。

```csharp
using System;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
namespace Company.FamilyTree
{
  partial class FamilyTreeDocData // Change name to your DocData.
  {
    // Register the store event handler:
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded();
      DomainClassInfo observedLinkInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(ParentsHaveChildren));
      DomainClassInfo observedClassInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(Person));
      EventManagerDirectory events = this.Store.EventManagerDirectory;
      events.ElementAdded
         .Add(observedLinkInfo, new EventHandler<ElementAddedEventArgs>(ParentLinkAddedHandler));
      events.ElementDeleted.Add(observedLinkInfo, new EventHandler<ElementDeletedEventArgs>(ParentLinkDeletedHandler));
      events.ElementPropertyChanged.Add(observedClassInfo, new EventHandler<ElementPropertyChangedEventArgs>(BirthDateChangedHandler));
    }
    // Handler will be called after transaction that creates a link:
    private void ParentLinkAddedHandler(object sender,
                                ElementAddedEventArgs e)
    {
      this.ValidationController.Validate(e.ModelElement,
           ValidationCategories.Save);
    }
    // Called when a link is deleted:
    private void ParentLinkDeletedHandler(object sender,
                                ElementDeletedEventArgs e)
    {
      // Don't apply validation to a deleted item!
      // - Validate store to refresh the error list.
      this.ValidationController.Validate(this.Store,
           ValidationCategories.Save);
    }
    // Called when any property of a Person element changes:
    private void BirthDateChangedHandler(object sender,
                      ElementPropertyChangedEventArgs e)
    {
      Person person = e.ModelElement as Person;
      // Not interested in changes in other properties:
      if (e.DomainProperty.Id != Person.BirthYearDomainPropertyId)
          return;

      // Validate all parent links to and from the person:
      this.ValidationController.Validate(
        ParentsHaveChildren.GetLinksToParents(person)
        .Concat(ParentsHaveChildren.GetLinksToChildren(person))
        , ValidationCategories.Save);
    }
  }
}
```

 在影響連結或項目的復原或取消復原作業之後，也會呼叫處理常式。

## <a name="custom"></a> 自訂驗證分類
 除了標準驗證分類 (例如功能表和開啟) 之外，您還可以定義自己的分類。 您可以從程式碼叫用這些分類。 使用者無法直接叫用這些分類。

 自訂分類的一般用法是，定義一個分類以測試模型是否滿足特定工具的前置條件。

 若要將驗證方法加入至特定分類，請在此方法的前面加上類似如下的屬性：

```csharp
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]
[ValidationMethod(ValidationCategory.Menu)]
private void TestForCircularLinks(ValidationContext context)
{...}
```

> [!NOTE]
>  您可以視需要在方法前面加上任意數目的 `[ValidationMethod()]` 屬性。 您可以同時將一個方法加入至自訂分類和標準分類。

 若要叫用自訂驗證：

```csharp

// Invoke all validation methods in a custom category:
validationController.ValidateCustom
  (store, // or a list of model elements
   "PreconditionsForGeneratePartsList");
```

## <a name="alternatives"></a> 驗證的替代方法
 驗證條件約束會報告錯誤，但不會變更模型。 如果您想避免模型無效，可以使用其他方法。

 但是，不建議使用這些方法。 通常比較好的做法是，讓使用者決定如何修正無效的模型。

 **調整變更，以還原至有效的模型。** 例如，如果使用者設定的屬性超過允許的上限，您無法將屬性重設的最大值。 若要達成目標，請定義規則。 如需詳細資訊，請參閱 <<c0> [ 規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。

 **回復交易如果嘗試無效的變更。** 您也可以針對此目的，來定義規則，但在某些情況下是可以覆寫屬性處理常式**onvaluechanging （)**，或覆寫某個方法時，這類`OnDeleted().`若要回復的交易，使用`this.Store.TransactionManager.CurrentTransaction.Rollback().`如需詳細資訊詳細資訊，請參閱[網域屬性值變更處理常式](../modeling/domain-property-value-change-handlers.md)。

> [!WARNING]
> 確定使用者知道已調整或已復原變更。 例如，使用 `System.Windows.Forms.MessageBox.Show("message").`

## <a name="see-also"></a>另請參閱

- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)