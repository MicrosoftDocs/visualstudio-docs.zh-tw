---
title: 在 UML 擴充功能上執行單元測試 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cf83fdf92133284271ea696bccef31af1bd72dbd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701710"
---
# <a name="run-unit-tests-on-uml-extensions"></a>在 UML 擴充功能上執行單元測試
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

為了協助在連續變更之後保持您程式碼的穩定，建議您撰寫單元測試，並在一般建置流程時執行它們。 如需詳細資訊，請參閱[對程式碼進行單元測試](../test/unit-test-your-code.md)。 若要設定 Visual Studio 模型擴充功能的測試，您需要一些重要資訊。 歸納起來：  
  
- [設定 VSIX 擴充功能的單元測試](#Host)  
  
   使用 VS IDE 主機介面卡執行測試。 在每種測試方法的前面加上 `[HostType("VS IDE")]`。 當您執行測試時，這個主機介面卡會啟動 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
- [存取 DTE 和 ModelStore](#DTE)  
  
   您通常需要開啟模型和其圖表，並在測試初始化時存取 `IModelStore` 。  
  
- [開啟模型圖](#Opening)  
  
   `EnvDTE.ProjectItem` 可以轉換為 `IDiagramContext`，反之亦然。  
  
- [在 UI 執行緒中執行變更](#UiThread)  
  
   變更模型存放區的測試必須在 UI 執行緒中執行。 您可以針對這個目的使用 `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` 。  
  
- [測試命令、 手勢和其他 MEF 元件](#MEF)  
  
   若要測試 MEF 元件，您必須將其匯入的屬性明確地連接至值。  
  
  下列各節會詳細說明這些重點。  
  
  您可以在程式碼範例庫的 [UML - 使用文字快速輸入](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)中找到進行過單元測試的 UML 擴充功能範例。  
  
## <a name="requirements"></a>需求  
 請參閱 [需求](../modeling/extend-uml-models-and-diagrams.md#Requirements)。  
  
 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="Host"></a> 設定 VSIX 擴充功能的單元測試  
 模型擴充功能中的方法通常會使用已開啟的圖表。 這些方法使用 MEF 匯入，例如 **IDiagramContext** 和 **ILinkedUndoContext**。 執行測試之前，您的測試環境必須先設定這個內容。  
  
#### <a name="to-set-up-a-unit-test-that-executes-in-includevsprvsincludesvsprvs-mdmd"></a>設定在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中執行的單元測試  
  
1. 建立 UML 擴充功能專案和單元測試專案。  
  
    1. **UML 擴充功能專案。** 您通常會使用命令、手勢或驗證專案範本，來建立這個專案。 例如，請參閱[在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)。  
  
    2. **單元測試專案。** 如需詳細資訊，請參閱[對程式碼進行單元測試](../test/unit-test-your-code.md)。  
  
2. 建立含有 UML 模型專案的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案。 您將會使用這個方案做為測試的初始狀態。 它應該與您在其中撰寫 UML 擴充功能和其單元測試的方案區隔開來。 如需詳細資訊，請參閱 <<c0> [ 建立 UML 模型專案和圖表](../modeling/create-uml-modeling-projects-and-diagrams.md)。  
  
3. **在 UML 擴充功能專案中**，編輯 .csproj 檔案做為文字，並確定下列各行顯示 `true`：  
  
    ```  
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>  
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>  
    ```  
  
     若要編輯 .csproj 檔案做為文字，請在方案總管的專案捷徑功能表上選擇 [卸載專案]  。 然後選擇 [編輯 ….csproj] 。 在您編輯過文字之後，請選擇 [重新載入專案] 。  
  
4. 在 UML 擴充功能專案中，於 **Properties\AssemblyInfo.cs**中加入下行。 這樣可讓單元測試存取您想要測試的方法：  
  
    ```csharp  
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
    ```  
  
5. **在單元測試專案中**，加入下列組件 References：  
  
    - *您的 UML 擴充功能專案*  
  
    - **EnvDTE.dll**  
  
    - **Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll**  
  
    - **Microsoft.VisualStudio.ComponentModelHost.dll**  
  
    - **Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll**  
  
    - **Microsoft.VisualStudio.Uml.Interfaces.dll**  
  
    - **Microsoft.VSSDK.TestHostFramework.dll**  
  
6. 在每種測試方法 (包括初始化方法) 的前面加上 `[HostType("VS IDE")]` 屬性。  
  
     這樣可確定測試將在 Visual Studio 的試驗執行個體中執行。  
  
## <a name="DTE"></a> 存取 DTE 和 ModelStore  
 撰寫方法，以在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中開啟模型專案。 在每個測試回合中，您通常只會想要開啟方案一次。 若只要執行此方法一次，請在此方法的前面加上 `[AssemblyInitialize]` 屬性。 請不要忘記，每種測試方法上也需要 [HostType("VS IDE")] 屬性。  例如:   
  
```csharp  
using EnvDTE;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
  
namespace UnitTests  
{  
  [TestClass]  
  public static class TestSetup  
  {  
  
    // Location of a VS Solution that defines an initial state for your tests:  
    private const string testSolutionFilePath = @"C:\MyTestFolder\TestModelSln\TestModel.sln";  
    // Name of a modeling project within the test solution:  
    private const string testModelingProjectName = "MyTestModel";  
  
    // Make Solution and IModelStore available to test methods:  
    public static Solution ModelSolution = null;  
    public static IModelingProject ModelingProject = null;  
    public static IModelStore ModelStore = null;  
  
    // This method will be performed once to initialize tests for this assembly:  
    [AssemblyInitialize]   
    [HostType("VS IDE")]  
    public static void OpenTestModelingProject(TestContext testContext)  
    {  
      // To make sure that we always start the tests in the same state,  
      // copy the test solution from a read-only directory:  
      // TODO: copy test solution folder.  
  
      // Open a solution that is the initial state for your tests:  
      ModelSolution = VsIdeTestHostContext.Dte.Solution;  
      ModelSolution.Open(testSolutionFilePath);  
  
      // Find the ModelingProject and IModelStore:  
      foreach (Project project in ModelSolution.Projects)  
      {  
        // https://msdn.microsoft.com/library/ee791691.aspx  
        ModelingProject = project as IModelingProject;  
        if (ModelingProject != null)  
        {  
          // This is a modeling project.  
          ModelStore = ModelingProject.Store;  
          break;  
        }  
        // else this is another kind of project.  
      }  
  
      Assert.IsNotNull(ModelSolution, "VS solution not found");  
      Assert.IsNotNull(ModelStore, "Modeling store not found");  
    }  
    [AssemblyCleanup]  
    public static void RemoveTestSolution ()  
    {  
      // TODO: Remove copied test solution directory.  
    }  
  }  
}  
  
```  
  
 如果 <xref:EnvDTE.Project?displayProperty=fullName> 執行個體代表模型專案，則可以將它轉換為 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.IModelingProject>，反之亦然。  
  
## <a name="Opening"></a> 開啟模型圖  
 針對每個測試或測試類別，您通常會想要使用已開啟的圖表。 下列範例使用 `[ClassInitialize]` 屬性，而該屬性會在這個測試類別中的其他方法之前執行這種方法。 再次提醒，請不要忘記，每種測試方法上也需要 [HostType("VS IDE")] 屬性：  
  
```csharp  
//   
private IDiagram diagram;  
// This class contains unit tests:  
[TestClass]  
public class MyTestClass  
{  
  // Map filenames to open diagram files:  
  private static Dictionary<string, IDiagram> diagrams = new Dictionary<string, IDiagram>();  
  
  // This method will be called once for this test class:  
  [ClassInitialize]  
  [HostType("VS IDE")]  
  public static void TestClassInitialize(TestContext testContext)  
  {  
    // Open all the diagrams in the model:  
    foreach (ProjectItem item in (TestSetup.ModelingProject as Project).ProjectItems)  
    {  
      // Get the filename of the principal file (not the .layout subsidiary):  
      string fileName = item.FileNames[0];  
      // If this is a model diagram file, it can be cast to IDiagramContext:  
      IDiagramContext modelingItem = item as IDiagramContext;  
      if (modelingItem != null)  
      {  
        IDiagram diagram = modelingItem.CurrentDiagram;  
        if (diagram == null)  
        {  
          // Diagram is closed. Open it:  
          item.Open().Activate();  
          diagram = modelingItem.CurrentDiagram;  
        }  
        diagrams[fileName] = diagram;  
      }  
      // else item is not a model diagram.  
    }  
    Assert.IsTrue(diagrams.Count>0, "UML diagram not found");  
  }  
// Insert test methods here ...  
}  
  
```  
  
## <a name="UiThread"></a> 在 UI 執行緒中執行模型變更  
 如果您的測試或正在測試的方法變更模型存放區，則必須在使用者介面執行緒中執行它們。 如果您沒有這麼做，則可能會看到 `AccessViolationException`。 使用 Invoke 的呼叫，括住測試方法的程式碼：  
  
```  
using System.Windows.Forms;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
 ...  
    [TestMethod]  
    [HostType("VS IDE")]  
    public void MyTest1()  
    {  
      // Store operations must run in the UI thread:  
      UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
        SetupTestState(TestSetup.ModelStore, diagram);  
        ExecuteMethodUnderTest(TestSetup.ModelStore, diagram);  
      });  
    }  
```  
  
## <a name="MEF"></a> 測試命令、 手勢和其他 MEF 元件  
 MEF 元件使用具有 `[Import]` 屬性且由其主機設定其值的屬性宣告。 這類屬性通常會包括 IDiagramContext、SVsServiceProvider 和 ILinkedUndoContext。 當您測試使用上述任何屬性的方法時，需要先設定其值，再執行測試中方法。 例如，如果您已撰寫與下列程式碼類似的命令擴充功能：  
  
```  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class MyCommand : ICommandExtension  
  {  
    [Import] IDiagramContext context { get; set; }  
    [Import]   
Microsoft.VisualStudio.Shell.SVsServiceProvider  
serviceProvider {get;set;}  
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      DoCommand();  
    }  
    private void DoCommand()  
    {  
      IDiagram diagram = context.CurrentDiagram;  
      using (ILinkedUndoTransaction t = linkedUndoContext.BeginTransaction("go"))  
      { ... }}}  
  
```  
  
 然後，您可以設定匯入的屬性，如下所示：  
  
```  
  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ComponentModelHost;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
...  
    [TestMethod]   
    [HostType("VS IDE")]  
    public void Test1()  
    {  
      // Create an instance of the class under test:  
      MyCommand myCommand = new MyCommand();  
      // Get the components service:  
      IComponentModel components = VsIdeTestHostContext.ServiceProvider  
        .GetService(typeof(SComponentModel)) as IComponentModel;  
      // Set the imported properties of the instance under test:  
      // Extension requires "using System.ComponentModel.Composition;" :  
      components.DefaultCompositionService.SatisfyImportsOnce(myCommand);  
      // Call method(s) under test:  
      UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
        myCommand.DoCommand();  
      });  
...}  
```  
  
 如果您想要測試的方法採用匯入的屬性做為參數，則可以將屬性匯入至測試類別，並將 `SatisfyImportsOnce` 套用至測試執行個體。 例如:   
  
```  
  
using System.ComponentModel.Composition;  
...  
  [TestClass]  
  public class MyTestClass  
  {  
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called before each test method:  
    [TestInitialize, HostType("VS IDE")]   
    public void TestInitializer()  
    {  
      IComponentModel components = VsIdeTestHostContext.ServiceProvider  
            .GetService(typeof(SComponentModel)) as IComponentModel;  
      // Extension requires "using System.ComponentModel.Composition;" :  
      components.DefaultCompositionService.SatisfyImportsOnce(this);  
    }  
    [TestMethod, HostType("VS IDE")]  
    public void Test2()  
    {   
     UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
      // Pass context items to class under test:  
      Class1 item1 = new Class1(this.linkedUndoContext);  
      item1.Method1(); // Can use linkedUndoContext  
     });  
   }  
}  
  
```  
  
 在這個範例中，為求方便使用，將每種測試方法上的這兩個屬性合併為一行。  
  
## <a name="access-from-tests-to-private-methods-and-variables"></a>從測試到私用方法和變數的存取  
 有時，在您執行測試中方法之前和之後，會想要測試私用方法，或者想要確認私用欄位的狀態。 因為測試是在與測試下類別不同的組件中，所以這會造成困難。 您可以考慮數種做法，包括：  
  
 僅使用公用和內部項目進行測試  
 撰寫您的測試，使其只使用公用 (或內部) 類別和成員。 這是最佳方式。 即使您重構測試中組件的內部實作，您的測試還是會繼續進行。 透過在變更之前和之後套用相同的測試，就可以確定您的變更並未改變組件的行為。  
  
 若要進行這項作業，則可能需要重新建構您的程式碼。 例如，您可能需要將一些方法區隔為另一個類別。  
  
 藉由認真考量這種方式，您通常會發現您的程式碼更容易讀取和變更，而且在需要進行變更時，較不容易發生錯誤。  
  
 在要測試之專案的 **Properties\AssemblyInfo.cs** 中加入屬性，即可允許測試組件存取內部項目：  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 定義測試介面  
 定義介面，而此介面包括要測試之類別的公用成員，以及您想要測試能夠使用之私用成員的其他屬性和方法。 將這個介面加入要測試的專案。 例如：  
  
```csharp  
internal interface MyClassTestInterface {  
  void PublicMethod1();  
  string PublicProperty1 { get; }  
  string privateField1_Accessor { get; }  
  int privateMethod1_Accessor (string p1);   
 }  
```  
  
 將方法加入要測試的類別，以明確地實作存取子方法。 將這些其他方法與主要類別分隔開來，方法是在不同檔案的部分類別定義中撰寫這些方法。 例如:   
  
```csharp  
partial public class MyClass  
{  
  string MyClassTestInterface.privateField1_Accessor  
  { get { return privateField1; } }  
  int MyClassTestInterface.privateMethod1_Accessor (string p1)  
  { return privateMethod1(p1); }  
}  
  
```  
  
 將這個屬性加入您正在測試的組件，以允許測試組件使用測試介面：  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 在單元測試方法中，使用測試介面。 例如:   
  
```csharp  
MyClassTestInterface testInstance = new MyClass();  
testInstance.PublicMethod1();  
Assert.AreEqual("hello", testInstance.privateField1_Accessor);  
```  
  
 使用反映來定義存取子  
 這是我們最不建議的方式。 舊版 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 已提供公用程式，來自動建立每種私用方法的存取子方法。 雖然這十分方便，但是我們的經驗告訴我們這樣可能會導致單元測試與其正在測試之應用程式的內部結構極緊密地結合。 因為測試需要與實作一起變更，所以這樣會在需求或架構變更時導致額外工作。 而且，實作設計中的任何錯誤假設也會內建至測試，因此，測試會找不到錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [單元測試的結構](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)   
 [在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [UML – 使用文字快速輸入](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)
