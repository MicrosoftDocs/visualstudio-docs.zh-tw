---
title: 使用 Modelbus 整合模型
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68482f9dcb88bd87c65f749c821f4afe92089a51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810668"
---
# <a name="integrating-models-by-using-visual-studio-modelbus"></a>使用 Visual Studio Modelbus 整合模型

Visual Studio ModelBus 提供方法來建立模型的模型之間，以及從其他工具的連結。 例如，您可以連結定義域專屬語言 (DSL) 模型和 UML 模型。 您可以建立一組整合的 DSL。

ModelBus 可讓您建立模型或模型內特定項目的唯一參考。 這個參考可以儲存在模型外，例如儲存在另一個模型的項目中。 在此情況下，工具需要取得項目的存取權，模型匯流排基礎結構會載入適當的模型並傳回項目。 如有需要，您可以向使用者顯示模型。 如果無法從先前的位置存取檔案，ModelBus 會請使用者尋找檔案。 如果使用者找到檔案，ModelBus 會修正該檔案的所有參考。

> [!NOTE]
> 在 ModelBus 目前 Visual Studio 實作中，連結的模型必須是相同的 Visual Studio 方案中的項目。

如需其他資訊和範例程式碼，請參閱：

- [如何：新增拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Modeling SDK for Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="provide"></a> 提供存取權給 DSL
 您必須定義用於 DSL 的 ModelBusAdapter，才能建立模型或其項目的 ModelBus 參考。 若要這樣做最簡單的方式是使用 Visual Studio 模型匯流排擴充功能，將命令加入至 DSL 設計工具。

### <a name="expose"></a> 若要公開 （expose） 給模型匯流排 DSL 定義

1. 除非您已安裝 Visual Studio 模型匯流排擴充功能，否則請下載並進行安裝。 如需詳細資訊，請參閱 < [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)。

2. 開啟 DSL 定義檔。 以滑鼠右鍵按一下設計介面，然後按一下**啟用 Modelbus**。

3. 在對話方塊中，選擇**我想要這個 DSL 公開給 ModelBus**。 如果您要將這個 DSL 公開給其模型，又要讓這個 DSL 使用其他 DSL 的參考，您可以選擇兩個選項。

4. 按一下 [確定 **Deploying Office Solutions**]。 新專案 "ModelBusAdapter" 會隨即加入至 DSL 方案。

5. 如果您要從文字範本存取 DSL，您必須修改新專案中的 AdapterManager.tt。 如果您要從其他程式碼 (例如命令和事件處理常式) 存取 DSL，請略過這個步驟。 如需詳細資訊，請參閱 <<c0> [ 文字範本中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。

   1. 將 AdapterManagerBase 的基底類別變更為 <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。

   2. 在接近檔案結尾處，將這個額外的屬性插入到類別 AdapterManager 的前面：

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. 在 ModelBusAdapter 專案的參考，加入**Microsoft.VisualStudio.TextTemplating.Modeling.11.0**。

      如果您要同時能夠從文字範本和其他程式碼存取 DSL，您需要一個已修改的配接器和一個未修改的配接器。

6. 按一下 **轉換所有範本**。

7. 重建方案。

   ModelBus 現在可以開啟這個 DSL 的執行個體。

   `ModelBusAdapters\bin\*` 資料夾包含 `Dsl` 專案和 `ModelBusAdapters` 專案建置的組件。 若要從另一個 DSL 參考這個 DSL，您應該匯入這些組件。

### <a name="ensure-that-elements-can-be-referenced"></a>請確定可以參考項目

Visual Studio ModelBus 配接器使用項目的 guid 來識別它，預設值。 因此，這些 ID 必須保存在模型檔中。

若要確定該識別碼會保存的項目：

1. 開啟 DslDefinition.dsl。

2. 在 [DSL 總管] 中，展開**Xml 序列化行為**，然後**類別資料**。

3. 針對您要建立模型匯流排參考的每個類別：

    按一下 [類別] 節點中，然後在 [屬性] 視窗中，請確定**序列化 Id**設定為`true`。

   或者，如果您要使用項目名稱 (而不是 GUID) 來識別項目，您可以覆寫產生之配接器的組件。 覆寫配接器類別中的下列方法：

- 覆寫 `GetElementId` 以傳回您要使用的 ID。 建立參考時，會呼叫這個方法。

- 覆寫 `ResolveElementReference` 以從模型匯流排參考中找到正確項目。

## <a name="editRef"></a> 從另一個 DSL 存取 DSL

您可以在 DSL 的網域屬性中儲存模型匯流排參考，以及撰寫自訂程式碼來使用這些參考。 您也可以讓使用者選擇模型檔和模型內的某個項目，藉此建立模型匯流排參考。

若要讓 DSL 使用另一個 DSL 的參考，您應該先將它*消費者*模型匯流排參考。

### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>允許 DSL 使用已公開 DSL 的參考

1. 在 DSL 定義圖表中，以滑鼠右鍵按一下圖表的主要部分，並再按**啟用 Modelbus**。

2. 在對話方塊中，選取**我想要啟用這個模型使用模型匯流排參考**。

3. 在使用 DSL 的 Dsl 專案中，將下列組件加入至專案參考。 您會發現這些組件 （.dll 檔案） 中 ModelBusAdapter\bin\\* 目錄公開的 DSL。

    - 公開的 DSL 組件，例如**Fabrikam.FamilyTree.Dsl.dll**

    - 已公開的模型匯流排配接器組件，例如**Fabrikam.FamilyTree.ModelBusAdapter.dll**

4. 將下列 .NET 組件加入至使用 DSL 專案的專案參考。

    1. **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2. **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>在網域屬性中儲存模型匯流排參考

1. 在使用 DSL 的 DSL 定義中，將網域屬性加入至網域類別並設定其名稱。

2. 在 [屬性] 視窗中，選取網域屬性將**型別**至`ModelBusReference`。

   在這個階段中，程式碼可設定此屬性值，但此屬性在 [屬性] 視窗中是唯讀的。

   您可以允許使用者使用專用 ModelBus 參考編輯器來設定此屬性。 有兩個版本，此編輯器或*選擇器：* 其中一個可讓使用者選擇模型檔，以及其他可讓使用者選擇模型檔和模型內的項目。

### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>允許使用者設定網域屬性中的模型匯流排參考

1. 以滑鼠右鍵按一下 網域屬性，然後按一下**編輯 ModelBusReference 特定屬性**。 對話方塊隨即開啟。 這是*Model Bus Picker*。

2. 選取適當**modelbusreference 類型**： 模型或模型內的項目。

3. 在檔案對話方塊篩選字串中，輸入字串 (例如 `Family Tree files |*.ftree`)。 替代已公開 DSL 的副檔名。

4. 如果您選擇模型內某個項目的參考，您可以加入使用者可選取的類型清單，例如 Company.FamilyTree.Person。

5. 按一下 [ **[確定]** ，然後按一下**轉換所有範本**中**方案總管] 中**工具列。

    > [!WARNING]
    > 如果您尚未選取有效的模型或實體，[確定] 按鈕即使可能顯示為已啟用，也不會有任何作用。

6. 如果您指定目標類型清單 (例如 Company.FamilyTree.Person)，則必須將組件參考加入至您的 DSL 專案，並參考目標 DSL 的 DLL (例如 Company.FamilyTree.Dsl.dll)。

### <a name="to-test-a-model-bus-reference"></a>測試模型匯流排參考

1. 建置已公開的 DSL 和使用 DSL。

2. 按 F5 鍵或 CTRL+F5，在實驗模式中執行其中一個 DSL。

3. 在 Visual Studio 的實驗執行個體中的偵錯專案，加入每個 DSL 的執行個體的檔案。

    > [!NOTE]
    > Visual Studio ModelBus 只可以解析參考模型的相同 Visual Studio 方案中的項目。 例如，您無法建立針對檔案系統其他部分之模型檔的參考。

4. 在已公開的 DSL 執行個體中建立一些項目和連結，並加以儲存。

5. 開啟使用 DSL 的執行個體，然後選取具有模型匯流排參考屬性的模型項目。

6. 在 [屬性] 視窗中，按兩下模型匯流排參考屬性。 選擇器對話方塊隨即開啟。

7. 按一下 **瀏覽**，然後選取 公開的 DSL 執行個體。

     如果已指定特定項目 (Element) 類型的模型匯流排參考，選擇器也可讓您選擇模型內的某個項目 (Item)。

## <a name="creating-references-in-program-code"></a>在程式碼中建立參考

當您要儲存模型或模型內某個項目的參考時，您可以建立 `ModelBusReference`。 `ModelBusReference` 的類型有兩種：模型參考和項目參考。

若要建立模型的參考，您需要的模型是一個執行個體，和檔案名稱或 Visual Studio 專案項目模型的 DSL 的 AdapterManager。

若要建立項目參考，您需要模型檔的配接器，以及所要參考的項目。

> [!NOTE]
> 使用 Visual Studio ModelBus，您可以建立項目的參考相同的 Visual Studio 方案中。

### <a name="import-the-exposed-dsl-assemblies"></a>匯入已公開的 DSL 組件

在使用專案中，將專案參考加入至 DSL 和已公開 DSL 的 ModelBusAdapter 組件。

例如，假設您要在 MusicLibrary DSL 的項目中儲存 ModelBus 參考。 ModelBus 參考會參考 FamilyTree DSL 的項目。 在 MusicLibrary 方案之 `Dsl` 專案的 [參考] 節點中，將參考加入至下列組件：

- Fabrikam.FamilyTree.Dsl.dll - 已公開的 DSL。

- Fabrikam.FamilyTree.ModelBusAdapters.dll - 已公開 DSL 的 ModelBus 配接器。

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0

  您可以在已公開 DSL 的 `ModelBusAdapters` 專案中找到這些組件 (位於 `bin\*` 下)。

  在要建立參考的程式碼檔案中，您通常必須匯入這些命名空間：

```csharp
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>建立模型的參考

若要建立模型參考，您可以存取已公開 DSL 的 AdapterManager，然後使用 AdapterManager 來建立模型的參考。 您可以指定檔案路徑，或 `EnvDTE.ProjectItem`。

您可以從 AdapterManager 取得配接器，以提供模型內個別項目的存取權。

> [!NOTE]
> 您必須在配接器使用完畢之後加以處置。 使用 `using` 陳述式是達成此目標的最便利方式。 下列範例將說明這點。

```csharp
// The file path of a model instance of the FamilyTree DSL:
string targetModelFile = "TudorFamilyTree.ftree";
// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Get an adapterManager for the target DSL:
FamilyTreeAdapterManager manager =
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)
     as FamilyTreeAdapterManager;
// or: (modelBus.FindAdapterManagers(targetModelFile).First())
// or could provide an EnvDTE.ProjectItem

// Create a reference to the target model:
// NOTE: the target model must be a file in this project.
ModelBusReference modelReference =
     manager.CreateReference(targetModelFile);
// or can use an EnvDTE.ProjectItem instead of the filename

// Get the root element of this model:
using (FamilyTreeAdapter adapter =
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)
{
  FamilyTree modelRoot = adapter.ModelRoot;
  // Access elements under the root in the usual way:
  foreach (Person p in modelRoot.Persons) {...}
  // You can create adapters for individual elements:
  ModelBusReference elementReference =
     adapter.GetElementReference(person);
  ...
} // Dispose adapter
```

如果您想在稍後能夠使用 `modelReference`，您可以將其儲存在具有外部類型 `ModelBusReference` 的網域屬性中：

```csharp
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

若要允許使用者編輯這個網域屬性，請使用 `ModelReferenceEditor` 做為編輯器屬性的參數。 如需詳細資訊，請參閱 <<c0> [ 允許使用者編輯參考](#editRef)。

### <a name="to-create-a-reference-to-an-element"></a>建立項目的參考

您針對模型建立的配接器可用來建立及解析參考。

```csharp
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

如果您想在稍後能夠使用 `elementReference`，您可以將其儲存在具有外部類型 `ModelBusReference` 的網域屬性中。 若要允許使用者進行編輯，請使用 `ModelElementReferenceEditor` 做為編輯器屬性的參數。 如需詳細資訊，請參閱 <<c0> [ 允許使用者編輯參考](#editRef)。

### <a name="resolving-references"></a>解析參考

如果您具有 `ModelBusReference` (MBR)，您可以取得其參考的模型或模型項目。 如果圖表或其他檢視上顯示此項目，您可以開啟檢視並選取此項目。

您可以從 MBR 建立配接器。 您可以從配接器取得模型根。 您也可以解析參考模型內特定項目的 MBR。

```csharp
using Microsoft.VisualStudio.Modeling.Integration; ...
ModelBusReference elementReference = ...;

// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Use a model reference or an element reference
// to obtain an adapter for the target model:
using (FamilyTreeAdapter adapter =
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)
   // or CreateAdapter(modelReference)
{
  // Get the root of the model:
  FamilyTree tree = adapter.ModelRoot;

  // Get a model element:
  MyDomainClass mel =
    adapter.ResolveElementReference<MyDomainClass>(elementReference);
  if (mel != null) {...}

  // Get the diagram or other view, if there is one:
  ModelBusView view = adapter.GetDefaultView();
  if (view != null)
  {
   view.Open();
   // Display the diagram:
   view.Show();
   // Attempt to select the shape that presents the element:
   view.SetSelection(elementReference);
  }
} // Dispose the adapter.
```

#### <a name="to-resolve-modelbus-references-in-a-text-template"></a>解析文字範本中的 ModelBus 參考

1. 您要存取的 DSL 必須具有已設定供文字範本存取的 ModelBus 配接器。 如需詳細資訊，請參閱 <<c0> [ 提供的存取權給 DSL](#provide)。

2. 一般而言，您會使用儲存在來源 DSL 中的模型匯流排參考 (MBR) 來存取目標 DSL。 因此，您的範本會包含來源 DSL 的指示詞，以及用於解析 MBR 的程式碼。 如需文字範本的詳細資訊，請參閱[特定領域語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。

   ```
   <#@ template debug="true" hostspecific="true"
   inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
   <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
   <#@ output extension=".txt" #>
   <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
   <#@ assembly name = "System.Core" #>
   <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>
   <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>
   <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
   <#@ import namespace="System.Linq" #>
   <#@ import namespace="Company.CompartmentDragDrop" #>
   <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>
   <# // Get source root from directive processor:
     ExampleModel source = this.ExampleModel;
     // This DSL has a MBR in its root:
   using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)
     {
     ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();
     ModelBusReference modelReference =
       manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));

     // Get the root element of this model:
     using (CompartmentDragDropAdapter adapter =
        this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)
     {
       ModelRoot root = adapter.ModelRoot;
   #>
   [[<#= root.Name #>]]
   <#
     }
   #>
   ```

   如需詳細資訊和逐步解說，請參閱[文字範本中使用 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

## <a name="serializing-a-modelbusreference"></a>序列化 ModelBusReference

如果您要以字串格式儲存 `ModelBusReference` (MBR)，您可以加以序列化：

```csharp
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

以此方式序列化的 MBR 不會影響內容。 如果您使用簡單檔案架構的模型匯流排配接器，MBR 會包含絕對檔案路徑。 這在永遠不會移動執行個體模型檔的情況下便已足夠。 不過，模型檔通常會在 Visual Studio 專案中的項目。 您的使用者必須能夠將整個專案移至檔案系統的不同部分。 使用者也必須能夠控制專案的原始檔，並在不同的電腦上開啟專案。 因此，檔案名稱應相對於包含檔案之專案的位置來進行序列化。

### <a name="serializing-relative-to-a-specified-file-path"></a>相對於指定的檔案路徑來進行序列化

A`ModelBusReference`包含`ReferenceContext`，這是您可以在其中儲存資訊，例如檔案路徑相對於應該要加以序列化的字典。

若要相對於路徑進行序列化：

```csharp
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

若要從字串擷取參考：

```csharp
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>其他配接器建立的 ModelBusReferences
 如果您要建立自己的配接器，下列資訊會很實用。

 `ModelBusReference` (MBR) 是由兩個組件所組成：由模型匯流排還原序列化的 MBR 標頭，以及特定配接器管理員處理的特定配接器。 因此，您可以提供自己的配接器序列化格式。 例如，您可以參考資料庫而不是檔案，或者您可以在配接器參考中儲存其他資訊。 您所擁有的配接器會在 `ReferenceContext` 中放置其他資訊。

 當您還原序列化 MBR 時，您必須提供 ReferenceContext，然後再將其儲存在 MBR 物件中。 當您序列化 MBR 時，配接器會使用儲存的 ReferenceContext 協助產生字串。 還原序列化的字串不包含 ReferenceContext 中的所有資訊。 例如，在簡單檔案架構的配接器中，ReferenceContext 包含根檔案路徑，此資訊不會儲存在序列化的 MBR 字串中。

 MBR 的還原序列化作業可分為兩個階段：

- `ModelBusReferencePropertySerializer` 是處理 MBR 標頭的標準序列化程式。 它使用標準 DSL `SerializationContext` 屬性封包，該封包使用 `ReferenceContext` 索引鍵儲存在 `ModelBusReferencePropertySerializer.ModelBusLoadContextKey` 中。 特別要提的是，`SerializationContext` 應包含 `ModelBus` 的執行個體。

- 您的 ModelBus 配接器處理配接器特有的 MBR 部分。 它可以使用儲存在 MBR 之 ReferenceContext 中的其他資訊。 簡單檔案架構的配接器會使用索引鍵的根檔案路徑`FilePathLoadContextKey`和`FilePathSaveContextKey`。

     模型檔中的配接器參考只有在使用時才可還原序列化。

## <a name="to-create-a-model"></a>建立模型

### <a name="creating-opening-and-editing-a-model"></a>建立、開啟及編輯模型
 下列片段取自 VMSDK 網站上的狀態機器範例。 此程式碼片段描述如何使用 ModelBusReferences 建立及開啟模型，以及取得與模型相關聯的圖表。

 在這個範例中，目標 DSL 的名稱為 StateMachine。 數個名稱會衍生自此名稱，例如模型類別的名稱和 ModelBusAdapter 的名稱。

```csharp
using Fabrikam.StateMachine.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Integration;
using Microsoft.VisualStudio.Modeling.Integration.Shell;
using Microsoft.VisualStudio.Modeling.Shell;
...
// Create a new model.
ModelBusReference modelReference =
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);
//Keep reference of new model in this model.
using (Transaction t = ...)
{
  myModelElement.ReferenceProperty = modelReference;
  t.Commit();
}
// Get the ModelBus service from Visual Studio.
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.
    GetGlobalService(typeof(SModelBus)) as IModelBus;
// Get a modelbus adapter on the new model.
ModelBusAdapter modelBusAdapter;
modelBus.TryCreateAdapter(modelReference,
    this.ServiceProvider, out modelBusAdapter);
using (StateMachineAdapter adapter =
      modelBusAdapter as StateMachineAdapter)
{
    if (adapter != null)
    {
        // Obtain a Diagram from the adapter.
        Diagram targetDiagram =
           ((StandardVsModelingDiagramView)
                 adapter.GetDefaultView()
            ).Diagram;

        using (Transaction t =
             targetDiagram.Store.TransactionManager
                .BeginTransaction("Update diagram"))
        {
            DoUpdates(targetDiagram);
            t.Commit();
        }

        // Display the new diagram.
        adapter.GetDefaultView().Show();
    }
}
```

## <a name="validating-references"></a>驗證參考
 BrokenReferenceDetector 會測試存放區中所有可儲存 ModelBusReferences 的網域屬性。 它會在找到您提供的任何動作時，呼叫此動作。 這對驗證方法特別有用。 下列驗證方法會在嘗試儲存模型時測試存放區，並在錯誤視窗中報告不完整的參考：

```csharp
[ValidationMethod(ValidationCategories.Save)]
public void ValidateModelBusReferences(ValidationContext context)
{
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,
    delegate(ModelElement element, // parent of property
             DomainPropertyInfo property, // identifies property
             ModelBusReference reference) // invalid reference
    {
      context.LogError(string.Format(INVALID_REF_FORMAT,
             property.Name,
             referenceState.Name,
             new ModelBusReferenceTypeConverter().
                 ConvertToInvariantString(reference)),
         "Reference",
         element);
      });
}}
private const string INVALID_REF_FORMAT =
    "The '{0}' domain property of ths ReferenceState instance "
  + "named '{1}' contains reference value '{2}' which is invalid";
```

## <a name="actions-performed-by-the-modelbus-extension"></a>ModelBus 擴充功能執行的動作

下列資訊並非必要，不過如果您要擴充使用 ModelBus，這些資訊可能會很實用。

ModelBus 擴充功能在 DSL 方案中進行了下列變更。

當您以滑鼠右鍵按一下 DSL 定義圖時，按一下**啟用 Modelbus**，然後選取**啟用這個 DSL 以使用 ModelBus**:

- 在 DSL 專案中，若要加入的參考**Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

- 在 DSL 定義中，會加入外部類型參考：`Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`。

   您可以看到在參考**DSL 總管**下方**網域類型**。 若要手動加入外部類型參考，請以滑鼠右鍵按一下根節點。

- 新增新的範本檔案時， **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**。

當您將網域屬性的類型設定為 ModelBusReference，然後以滑鼠右鍵按一下屬性並按一下**啟用 ModelBusReference 的特定屬性**:

- 數個 CLR 屬性會加入至網域屬性。 您會在 [屬性] 視窗的 [自訂屬性] 欄位中看到這些屬性。 在  **Dsl\GeneratedCode\DomainClasses.cs**，您可以看到屬性宣告上的屬性：

  ```csharp
  [System.ComponentModel.TypeConverter(typeof(
  Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]
  [System.ComponentModel.Editor(typeof(
    Microsoft.VisualStudio.Modeling.Integration.Picker
    .ModelReferenceEditor // or ModelElementReferenceEditor
    ), typeof(System.Drawing.Design.UITypeEditor))]
  [Microsoft.VisualStudio.Modeling.Integration.Picker
    .SupplyFileBasedBrowserConfiguration
    ("Choose a model file", "Target model|*.target")]
  ```

當您以滑鼠右鍵按一下 DSL 定義圖時，按一下**啟用 ModelBus**，然後選取**這個 DSL 公開給 ModelBus**:

- 新專案 `ModelBusAdapter` 會加入至方案。

- `ModelBusAdapter` 的參考會加入至 `DslPackage` 專案。 `ModelBusAdapter` 會參考 `Dsl` 專案。

- 在  **DslPackage\source.extention.tt**，`|ModelBusAdapter|`加入做為 MEF 元件。

## <a name="see-also"></a>另請參閱

- [如何：在程式碼中開啟檔案的模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [如何：新增拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [使用文字範本中的 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)