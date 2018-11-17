---
title: 在模型圖上定義功能表命令 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c211c37817ba996105d7496dc49e91db9fa9298e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809099"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>在模型圖上定義功能表命令
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，您可以定義 UML 圖表之捷徑功能表上的額外功能表項目。 您可以控制是否在圖表上任何項目的捷徑功能表上顯示和啟用功能表命令，而且您可以撰寫在使用者選擇功能表項目時所執行的程式碼。 您可以將這些擴充功能封裝成 Visual Studio 整合擴充功能 ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780))，以及將這些整合擴充功能散發給其他 Visual Studio 使用者。  

## <a name="requirements"></a>需求  
 請參閱 [需求](../modeling/extend-uml-models-and-diagrams.md#Requirements)。  

 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  

## <a name="defining-the-menu-command"></a>定義功能表命令  
 若要建立 UML 設計工具的功能表命令，您必須建立一個類別來定義命令行為，並且將該類別內嵌在 Visual Studio 整合擴充功能 (VSIX)。 VSIX 會做為容器，可安裝該命令。 定義功能表命令有兩個替代方法：  

-   **在它自己使用的專案範本的 VSIX 中建立功能表命令。** 這是較快速的方法。 它適用於您不想合併您的功能表命令與其他類型的擴充功能時，例如驗證擴充功能、自訂工具箱項目或軌跡處理常式。  

-   **建立個別的功能表命令和 VSIX 專案。** 如果您想要將數種類型的擴充功能結合成相同的 VSIX，則請使用這個方法。 例如，如果您的功能表命令預期模型要觀察特定的條件約束，可以將它內嵌至與驗證方法相同的 VSIX。  

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>在自己的 VSIX 中建立功能表命令  

1. 在 [新增專案]  對話方塊中，於 [模型專案] 之下，選取 [命令擴充功能] 。  

2. 在新的專案中開啟 **.cs** 檔案，並修改 `CommandExtension` 類別來實作命令。  

    如需詳細資訊，請參閱 [實作功能表命令](#Implementing)。  

3. 定義新的類別，即可將額外命令加入這個專案。  

4. 按 F5 測試功能表命令。 如需詳細資訊，請參閱 [執行功能表命令](#Executing)。  

5. 另一部電腦上安裝功能表命令，將檔案複製**筒\\\*\\\*.vsix**專案建置。 如需詳細資訊，請參閱 [安裝和解除安裝擴充功能](#Installing)。  

   以下是替代程序：  

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>在不同的類別庫 (DLL) 專案中建立功能表命令  

1. 在新的 Visual Studio 方案或現有的方案中，建立類別庫專案。  

   1.  在 [檔案]  功能表上，依序選擇 [新增] 和 [專案] 。  

   2.  在 [已安裝的範本] 下，選取 [Visual C#]  或 [Visual Basic] 。 在中間欄中，選擇 [類別庫] 。  

   3.  設定 [方案]  以表示您是要建立新的方案，還是將元件加入已經開啟的 VSIX 方案。  

   4.  設定專案名稱和位置，然後按一下 [確定]。  

2. 將下列參考加入您的專案。  


   |                                                                                                    參考資料                                                                                                    |                                                                                                  這可讓您執行                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System.ComponentModel.Composition                                                                                        |                                         使用 [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)定義元件。                                          |
   |                                                                                      Microsoft.VisualStudio.Uml.Interfaces                                                                                      |                                                                                        讀取和變更模型項目的屬性。                                                                                         |
   |                                                                             Microsoft.VisualStudio.ArchitectureTools.Extensibility                                                                              |                                                                                      建立模型項目、修改圖表上的圖形。                                                                                       |
   |                                                                                  Microsoft.VisualStudio.Modeling.Sdk.[version]                                                                                  | 定義模型事件處理常式。<br /><br /> 將一系列的變更封裝至您的模型。 如需詳細資訊，請參閱 <<c0> [ 藉由使用異動連結 UML 模型更新](../modeling/link-uml-model-updates-by-using-transactions.md)。 |
   |                                                            Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[版本]<br /><br /> (不一定是必要項目)                                                             |                                                                                   存取軌跡處理常式的其他圖表項目。                                                                                   |
   | Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer<br /><br /> 只有分層圖上的命令才為必要項目。 如需詳細資訊，請參閱 <<c0> [ 擴充圖層圖表](../modeling/extend-layer-diagrams.md)。 |                                                                                             在分層圖上定義命令。                                                                                              |


3. 將類別檔案加入專案，並將其內容設定為下列程式碼。  

   > [!NOTE]
   >  將命名空間、類別名稱以及 `Text` 所傳回的值變更為您的喜好設定。  
   >   
   >  如果您定義多個命令，則它們會以類別名稱的字母順序出現在功能表上。  

   ```  
   using System.ComponentModel.Composition;     
   using System.Linq;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
   using Microsoft.VisualStudio.Uml.Classes;   
       // ADD other UML namespaces if required  

   namespace UMLmenu1 // CHANGE  
   {  
     // DELETE any of these attributes if the command  
     // should not appear in some types of diagram.  
     [ClassDesignerExtension]  
     [ActivityDesignerExtension]  
     [ComponentDesignerExtension]  
     [SequenceDesignerExtension]  
     [UseCaseDesignerExtension]   
     // [LayerDesignerExtension]  

     // All menu commands must export ICommandExtension:  
     [Export (typeof(ICommandExtension))]  
     // CHANGE class name – determines order of appearance on menu:  
     public class Menu1 : ICommandExtension  
     {  
       [Import]  
       public IDiagramContext DiagramContext { get; set; }  

       public void QueryStatus(IMenuCommand command)  
       { // Set command.Visible or command.Enabled to false  
         // to disable the menu command.  
         command.Visible = command.Enabled = true;  
       }  

       public string Text  
       {  
         get { return "MENU COMMAND LABEL"; }  
       }  

       public void Execute(IMenuCommand command)  
       {  
         // A selection of starting points:  
         IDiagram diagram = this.DiagramContext.CurrentDiagram;  
         foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
         { IElement element = shape.Element; }  
         IModelStore modelStore = diagram.ModelStore;  
         IModel model = modelStore.Root;  
         foreach (IElement element in modelStore.AllInstances<IClass>())   
         { }  
       }  
     }  
   }  
   ```  

    如需要在方法中置入哪些項目的詳細資訊，請參閱 [實作功能表命令](#Implementing)。  

   您必須將功能表命令加入 VSIX 專案，期將會做為安裝命令的容器。 如果您想要，可以在相同的 VSIX 中包含其他元件。  

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>將功能表命令加入 VSIX 專案  

1.  如果您已經建立具有自己的 VSIX 的功能表命令，便不需要這項程序。  

2.  除非您的方案已經包含 VSIX 專案，否則請建立一個。  

    1.  在方案總管 中，於方案的捷徑功能表上，選擇 [新增] 和 [新增專案] 。  

    2.  在 [已安裝的範本] 下，展開 [Visual C#]  或 [Visual Basic] ，然後選擇 [擴充性] 。 在中間欄中，選擇 [VSIX 專案] 。  

3.  在方案總管中，於 VSIX 專案的捷徑功能表上，選擇 [設定為啟始專案] 。  

4.  開啟 **source.extension.vsixmanifest**。  

    1.  在 [中繼資料]  索引標籤上，設定 VSIX 的名稱。  

    2.  在 [安裝目標]  索引標籤上，設定 Visual Studio 版本做為目標。  

    3.  在 [資產]  索引標籤上，選擇 [新增] ，然後在對話方塊中設定：  

          =   

          =   

          =   

##  <a name="Implementing"></a> 實作功能表命令  
 功能表命令類別會實作 <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> 所需的方法。  

|||  
|-|-|  
|`string Text { get; }`|傳回功能表項目的標籤。|  
|`void QueryStatus(IMenuCommand command);`|使用者在圖表中按一下滑鼠右鍵時呼叫。<br /><br /> 這個方法不應該變更模型。<br /><br /> 使用 `DiagramContext.CurrentDiagram.SelectedShapes` 來判斷是否要顯示和啟用命令。<br /><br /> 設定：<br /><br /> -   `command.Visible` 若要`true`如果，命令必須出現在功能表中，當使用者以滑鼠右鍵按一下圖表中<br />-   `command.Enabled` 若要`true`如果使用者可以按一下功能表命令<br />-   `command.Text` 若要動態設定功能表標籤|  
|`void Execute (IMenuCommand command);`|使用者按一下您的功能表項目時呼叫 (如果顯示並啟用功能表項目)。|  

### <a name="accessing-the-model-in-code"></a>使用程式碼存取模型  
 在您的功能表命令類別中包括下列宣告：  

```  
[Import] public IDiagramContext DiagramContext { get; set; }  
```  

 ...  

 宣告 `IDiagramContext` 可讓您在方法中撰寫程式碼，存取圖表、目前的選取範圍，以及模型：  

```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
{ IElement element = shape.Element; ... }  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}  
```  

### <a name="navigating-and-updating-the-model"></a>巡覽和更新模型  
 透過 API 可以使用 UML 模型的項目。 從目前的選取範圍或模型的根目錄，您可以存取所有其他項目。 如需詳細資訊，請參閱 <<c0> [ 巡覽 UML 模型](../modeling/navigate-the-uml-model.md)並[使用 UML API 進行程式設計](../modeling/programming-with-the-uml-api.md)。  

 如果您正在處理循序圖，請參閱[使用 UML API 編輯 UML 循序圖](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)。  

 此 API 也可讓您變更項目的屬性、刪除項目和關聯性，以及建立新的項目和關聯性。  

 根據預設，將在不同的異動中執行您在 Execute 方法中進行的每個變更。 使用者將可以個別復原每個變更。 如果您想要將變更分組到單一交易，使用<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction>中所述[藉由使用異動連結 UML 模型更新](../modeling/link-uml-model-updates-by-using-transactions.md)。  

### <a name="use-the-ui-thread-for-updates"></a>使用 UI 執行緒進行更新  
 在某些情況下，可透過背景執行緒來更新模型。 例如，如果您的命令從慢速資源載入資料，則可以在背景執行緒中執行載入，讓使用者看到進行中的變更，並視需要取消作業。  

 不過，您應該注意模型存放區未具有執行緒安全功能。 您永遠應該利用使用者介面 (UI) 執行緒進行更新，可能的話，也應該防止使用者在進行背景作業時進行編輯。 如需範例，請參閱[更新 UML 模型，從背景執行緒](../modeling/update-a-uml-model-from-a-background-thread.md)。  

##  <a name="Executing"></a> 執行功能表命令  
 基於測試目的，請在偵錯模式中執行命令。  

#### <a name="to-test-the-menu-command"></a>測試功能表命令  

1.  按 **F5**，或在 [偵錯]  功能表上，選擇 [開始偵錯] 。  

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗執行個體隨即啟動。  

     **疑難排解**：如果新的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 未啟動：  

    -   您如有多個專案，請確定已將 VSIX 專案設定為解決方案的啟始專案。  

    -   在方案總管的啟始專案或唯一專案的捷徑功能表上，選擇 [屬性] 。 在專案屬性編輯器中，選取 [偵錯]  索引標籤。請確定 [啟動外部程式] ** 欄位中的字串是 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的完整路徑名稱，通常是：  

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  

2.  在實驗性 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中，開啟或建立模型專案，並開啟或建立模型圖表。 使用圖表，而圖表屬於功能表命令類別之屬性中所列的其中一種類型。  

3.  開啟圖表上任何位置的捷徑功能表。 您的命令應該會出現在功能表中。  

     **疑難排解**：如果命令未出現在功能表上，請確定：  

    -   在 VSIX 專案之 **source.extensions.manifest** 的 [資產]  索引標籤中，功能表命令專案會列為 MEF 元件。  

    -   `Import` 和 `Export` 屬性的參數有效。  

    -   `QueryStatus`方法未將`command`。`Enabled` 或是`Visible`欄位`false`。  

    -   您正在使用的模型圖類型 (UML 類別、順序等) 會列為下列其中一個功能表命令類別屬性： `[ClassDesignerExtension]`、 `[SequenceDesignerExtension]` 等。  

##  <a name="Installing"></a> 安裝及解除安裝擴充功能  
 您可以同時在自己的電腦和其他電腦上安裝 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 擴充功能。  

#### <a name="to-install-an-extension"></a>安裝擴充功能  

1.  在您的電腦中，尋找 VSIX 專案所建置的 **.vsix** 檔案。  

    1.  在方案總管 中，於 VSIX 專案的捷徑功能表上，選擇 [在 Windows 檔案總管中開啟資料夾] 。  

    2.  找出檔案**筒\\\*\\**_YourProject_**.vsix**  

2.  將 **.vsix** 檔案複製到要安裝擴充功能的目標電腦。 這可以是您自己的電腦或另一部電腦。  

     目標電腦必須具有其中一個版本[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]中所指定**source.extension.vsixmanifest**。  

3.  在目標電腦上，開啟 **.vsix** 檔案 (例如，按兩下該檔案)。  

     [Visual Studio 擴充功能安裝程式] 會隨即開啟並安裝擴充功能。  

4.  啟動或重新啟動 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]。  

#### <a name="to-uninstall-an-extension"></a>解除安裝擴充功能  

1. 在 [工具]  功能表中選擇 [擴充功能和更新] 。  

2. 展開 [已安裝的擴充功能] 。  

3. 選取擴充功能，然後選擇 [解除安裝] 。  

   在很少見的情況下，故障的擴充功能無法載入並且會在錯誤視窗中建立報告，但不會顯示在擴充管理員中。 在此情況下，您可以藉由從下列位置刪除檔案來移除擴充功能：  

   *%Localappdata%* **\Local\Microsoft\VisualStudio\\[version] \Extensions**  

##  <a name="MenuExample"></a> 範例  
 下列範例顯示功能表命令的程式碼，以在類別圖表上交換兩個項目的名稱。 這段程式碼必須在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 擴充功能專案中進行建置和安裝 (如先前章節所述)。  

```  
using System.Collections.Generic; // for IEnumerable  
using System.ComponentModel.Composition;  
  // for [Import], [Export]  
using System.Linq; // for IEnumerable extensions  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
  // for IDiagramContext  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
  // for designer extension attributes  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  // for ShapeElement  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  // for IGestureExtension, ICommandExtension, ILinkedUndoContext  
using Microsoft.VisualStudio.Uml.Classes;  
  // for class diagrams, packages  

/// <summary>  
/// Extension to swap names of classes in a class diagram.  
/// </summary>  
namespace SwapClassNames  
{  
  // Declare the class as an MEF component:  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  // Add more ExportMetadata attributes to make  
  // the command appear on diagrams of other types.  
  public class NameSwapper : ICommandExtension  
  {  
  // MEF required interfaces:  
  [Import]  
  public IDiagramContext Context { get; set; }  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  

  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  /// <param name="command"></param>  
  public void Execute(IMenuCommand command)  
  {  
    // Get selected shapes that are IClassifiers -  
    // IClasses, IInterfaces, IEnumerators.  
    var selectedShapes = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  

    // Get model elements displayed by shapes.  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  

    // Do the swap in a transaction so that user  
    // cannot undo one change without the other.  
    using (ILinkedUndoTransaction transaction =  
    LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
    string firstName = firstElement.Name;  
    firstElement.Name = lastElement.Name;  
    lastElement.Name = firstName;  
    transaction.Commit();  
    }  
  }  

  /// <summary>  
  /// Called by Visual Studio to determine whether  
  /// menu item should be visible and enabled.  
  /// </summary>  
  public void QueryStatus(IMenuCommand command)  
  {   
    int selectedClassifiers = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>().Count();  
    command.Visible = selectedClassifiers > 0;  
    command.Enabled = selectedClassifiers == 2;  
  }  

  /// <summary>  
  /// Name of the menu command.  
  /// </summary>  
  public string Text  
  {  
    get { return "Swap Names"; }  
  }  
  }  

}  
```  

## <a name="see-also"></a>另請參閱  
 [定義與安裝模型擴充功能](../modeling/define-and-install-a-modeling-extension.md)   
 [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)   
 [在模型圖上定義軌跡處理常式](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [定義自訂模型工具箱項目](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)   
 [使用 UML API 編輯 UML 順序圖表](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)   
 [使用 UML API 進行程式設計](../modeling/programming-with-the-uml-api.md)   
 [範例： UML 圖表上對齊圖形的命令](http://go.microsoft.com/fwlink/?LinkID=213809)



