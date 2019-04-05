---
title: 從 UML 模型產生檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 03b2cf5b03ea7f2cfc2d8fa90346ac47c1e4ae84
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930617"
---
# <a name="generate-files-from-a-uml-model"></a>透過 UML 模型產生檔案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

從 UML 模型中，您可以產生程式碼、結構描述、文件、資源以及其他任何類型的成品。 從 UML 模型產生文字檔案的一種便利的方法是使用[文字範本](../modeling/code-generation-and-t4-text-templates.md)。 這些可讓您將程式碼內嵌在您想要產生的文字中。  
  
 有三種主要案例：  
  
- [從功能表命令產生檔案](#Command)或軌跡。 您可以定義 UML 模型上可用的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 命令。  
  
- [從應用程式產生檔案](#Application)。 您可以撰寫可讀取 UML 模型並產生檔案的應用程式。  
  
- [在設計階段產生](#Design)。 您可以使用模型來定義一些應用程式功能，並在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案內產生程式碼、資源等。  
  
  本主題結尾的討論[如何使用文字產生](#What)。 如需詳細資訊，請參閱 <<c0> [ 程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)。  
  
##  <a name="Command"></a> 從功能表命令產生檔案  
 您可以在 UML 功能表命令內使用前置處理文字範本。 在文字範本的程式碼或不同的部分類別中，您可以讀取圖表所檢視的模型。  
  
 如需這些功能的詳細資訊，請閱讀下列主題：  
  
- [在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [使用 T4 文字範本在執行階段產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)  
  
- [巡覽 UML 模型](../modeling/navigate-the-uml-model.md)  
  
  下列範例中所示範的方法適用於從其中一個模型圖起始作業時，透過單一模型產生文字。 若要處理個別的內容中的模型，請考慮使用[Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md)存取模型和其項目。  
  
### <a name="example"></a>範例  
 若要執行這個範例，請建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組 (VSIX) 專案。 此範例中使用的專案名稱是`VdmGenerator`。 在  **source.extension.vsixmanifest**檔案中，按一下**加入內容**並將 類型 欄位設定為**MEF 元件**以及參考目前專案的來源路徑。 如需如何設定這種類型的專案的詳細資訊，請參閱[在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)。  
  
 將包含下列程式碼的 C# 檔案加入專案。 此類別定義將在 UML 類別圖上出現的功能表命令。  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace VdmGenerator  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  public class GenerateVdmFromClasses : ICommandExtension  
  {  
    [Import] public IDiagramContext DiagramContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      // Initialize the template with the Model Store.  
      VdmGen generator = new VdmGen(  
             DiagramContext.CurrentDiagram.ModelStore);  
      // Generate the text and write it.  
      System.IO.File.WriteAllText  
        (System.IO.Path.Combine(  
            Environment.GetFolderPath(  
                Environment.SpecialFolder.Desktop),  
            "Generated.txt")   
         , generator.TransformText());  
    }  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
    public string Text  
    { get { return "Generate VDM"; } }  
  }  
}  
```  
  
 下列檔案是文字範本。 它會為模型中的每個 UML 類別產生一行文字，並為每個類別中的每個屬性產生一行文字。 用於讀取模型的程式碼內嵌在文字中 (以 `<# ... #>` 區隔)。  
  
 若要建立此檔案，以滑鼠右鍵按一下方案總管 中的專案，指向**新增**，然後按一下**新項目**。 選取 **前置處理過的文字範本**。 此範例中的檔案名稱應該是**VdmGen.tt**。 **自訂工具**檔案的屬性應**TextTemplatingFilePreprocessor**。 如需有關前置處理過的文字範本的詳細資訊，請參閱 <<c0> [ 執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
```  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#   
   foreach (IClass classElement in store.AllInstances<IClass>())   {  
#>  
Type <#= classElement.Name #> ::  
<#  
     foreach (IProperty attribute in classElement.OwnedAttributes)     {  
#>  
       <#= attribute.Name #> : <#=   
           attribute.Type == null ? ""  
                                  : attribute.Type.Name #>   
<#  
     }   }  
#>  
```  
  
 文字範本會產生成為 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案一部分的 C# 部分類別。 在不同的檔案中，加入相同類別的另一個部分宣告。 這個程式碼提供具有 UML 模型存放區存取權的範本：  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
namespace VdmGenerator  
{  
    public partial class VdmGen  
    {  
        private IModelStore store;  
        public VdmGen(IModelStore s)  
        { store = s; }  
    }  
}  
```  
  
 若要測試的專案，請按**F5**。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的新執行個體隨即啟動 。 在這個執行個體中，開啟或建立包含類別圖的 UML 模型。 將部分類別加入圖表中，並將部分屬性加入每個類別中。 在圖表中以滑鼠右鍵按一下，然後按一下 範例命令`Generate VDM`。 此命令會建立檔案`C:\Generated.txt`。 檢查這個檔案。 其內容應該與下列文字類似，但它會列出您自己的類別和屬性：  
  
```  
Type Class1 ::  
          Attribute1 : int   
          Attribute2 : string   
Type Class2 ::   
          Attribute3 : string   
```  
  
##  <a name="Application"></a> 從應用程式產生檔案  
 您可以從讀取 UML 模型的應用程式產生檔案。 基於此目的，是最具彈性且完善方法存取模型和其項目[Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md)。  
  
 您也可以使用基本 API 來載入模型中，並使用與前一節相同的技術將模型傳遞給文字範本。 如需有關載入模型的詳細資訊，請參閱 <<c0> [ 讀取程式碼中的 UML 模型](../modeling/read-a-uml-model-in-program-code.md)。  
  
##  <a name="Design"></a> 在設計階段產生檔案  
 如果您的專案具有將 UML 解譯為程式碼的標準方法，則可以建立文字範本，讓您透過 UML 模型產生您專案內的程式碼。 通常，您會有包含 UML 模型專案的方案。以及應用程式碼的一個或多個專案。 根據模型的內容，每個程式碼專案都可以包含數個產生程式碼、資源和組態檔的範本。 開發人員可以執行所有範本，即可**轉換所有範本**在 方案總管 工具列中。 通常會以部分類別的形式產生程式碼，輕鬆地整合手動撰寫的組件。  
  
 這類 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案皆可透過範本的形式進行配送，因此小組的每個成員都可以建立專案，以使用相同的方式透過模型產生程式碼。 一般而言，範本是內含模型驗證條件約束之擴充套件的一部分，確保符合產生程式碼的前置條件。  
  
### <a name="outline-procedure-for-generating-files"></a>產生檔案的大綱程序  
  
-   若要加入的專案範本，請選取**文字範本**在加入新檔案 對話方塊中。 您可以將範本加入大部分類型的專案，但模型專案除外。  
  
-   範本檔案的 [自訂工具] 屬性應**TextTemplatingFileGenerator**，和檔案名稱的副檔名應該是.tt。  
  
-   範本應該至少有一個輸出指示詞：  
  
     `<#@ output extension=".cs" #>`  
  
     根據您專案的語言，設定副檔名欄位。  
  
-   若要允許範本中的產生程式碼存取模型，請撰寫讀取 UML 模型所需組件的 `<#@ assembly #>` 指示詞。 使用 `ModelingProject.LoadReadOnly()` 開啟模型。 如需詳細資訊，請參閱 <<c0> [ 讀取程式碼中的 UML 模型](../modeling/read-a-uml-model-in-program-code.md)。  
  
-   當您儲存它，並當您按一下時，會執行範本**轉換所有範本**在 [方案總管] 工具列中。  
  
-   如需這種類型的範本的詳細資訊，請參閱[使用 T4 文字範本在設計階段的程式碼產生](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
-   在典型專案中，您會有數個範本可透過相同的模型產生不同的檔案。 每個範本的第一個部分都會相同。 若要減少這種重複狀況，請將通用部分移至不同的文字檔，然後在每個範本中使用 `<#@include file="common.txt"#>` 指示詞叫用它。  
  
-   您也可以定義特殊指示詞處理器，以讓您提供文字產生程序的參數。 如需詳細資訊，請參閱 <<c0> [ 自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)。  
  
### <a name="example"></a>範例  
 這個範例會產生來源模型中每個 UML 類別的 C# 類別。  
  
##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>針對這個範例設定 Visual Studio 方案  
  
1. 在新方案的模型專案中建立 UML 類別圖。  
  
   1.  在 **架構**功能表上，按一下**新圖表**。  
  
   2.  選取  **UML 類別圖**。  
  
   3.  遵循提示以建立新的方案和模型專案。  
  
   4.  從工具箱拖曳「UML 類別」工具，以將一些類別加入圖表。  
  
   5.  儲存檔案。  
  
2. 在相同的方案中，建立 C# 或 Visual Basic 專案。  
  
   -   在 [方案總管] 中，以滑鼠右鍵按一下方案，指向**新增**，然後按一下**新的專案**。 底下**已安裝的範本**，按一下**Visual Basic**或是**Visual C#** ，然後選取 專案類型這類**主控台應用程式**。  
  
3. 將純文字檔加入 C# 或 Visual Basic 專案。 這個檔案將包含您要撰寫數個文字範本時共用的程式碼。  
  
   - 在 [方案總管] 中，以滑鼠右鍵按一下專案，指向**新增**，然後按一下**新項目**。 選取 **文字檔**。  
  
     插入下列區段中顯示的文字。  
  
4. 將文字範本檔案加入 C# 或 Visual Basic 專案。  
  
   - 在 [方案總管] 中，以滑鼠右鍵按一下專案，指向**新增**，然後按一下**新項目**。 選取 **文字範本**。  
  
     將後面的程式碼插入文字範本檔案中。  
  
5. 儲存文字範本檔案。  
  
6. 檢查附屬檔案中的程式碼。 它應該包含模型中每個 UML 類別的類別。  
  
   1.  在 Visual Basic 專案中，按一下**顯示所有檔案**在 [方案總管] 工具列中。  
  
   2.  展開方案總管中的範本檔案節點。  
  
#### <a name="content-of-the-shared-text-file"></a>共用文字檔的內容  
 在這個範例中，檔案稱為 SharedTemplateCode.txt，而且位於與文字範本相同的資料夾中。  
  
```  
<# /* Common material for inclusion in my model templates */ #>  
<# /* hostspecific allows access to the Visual Studio API */ #>  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>  
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>  
<#+  // Note this is a Class Feature Block  
///<summary>  
/// Text templates are run in a common AppDomain, so   
/// we can cache the model store that we find.  
///</summary>  
private IModelStore StoreCache  
{  
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }  
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }   
}  
private bool CacheIsOld()  
{  
    DateTime? dt = AppDomain.CurrentDomain  
           .GetData("latestAccessTime") as DateTime?;  
    DateTime t = dt.HasValue ? dt.Value : new DateTime();   
    DateTime now = DateTime.Now;  
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);  
    return now.Subtract(t).Seconds > 3;  
}  
  
///<summary>  
/// Find the UML modeling project in this solution,  
/// and load the model.  
///</summary>  
private IModelStore ModelStore  
{  
  get   
  {  
    // Avoid loading the model for every template:  
    if (StoreCache == null || CacheIsOld())  
    {  
      // Use Visual Studio API to find modeling project:  
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
      EnvDTE.Project project = null;  
      foreach (EnvDTE.Project p in dte.Solution.Projects)  
      {  
        if (p.FullName.EndsWith(".modelproj"))  
        {  
          project = p;  
          break;  
        }              
      }  
      if (project == null) return null;  
  
      // Load UML model into this AppDomain  
      // and access model store:  
      IModelingProjectReader reader =   
           ModelingProject.LoadReadOnly(project.FullName);  
      StoreCache = reader.Store;  
    }  
    return StoreCache;  
  }  
}  
#>  
```  
  
#### <a name="content-of-the-text-template-file"></a>文字範本檔案的內容  
 下列文字會置於 **.tt**檔案。 這個範例會透過模型中的 UML 類別在 C# 檔案中產生類別。 不過，您可以產生任何類型的檔案。 所產生檔案的語言與用來撰寫文字範本程式碼的語言無關。  
  
```  
<#@include file="SharedTemplateCode.txt"#>  
<#@ output extension=".cs" #>  
namespace Test{  
<#  
      foreach (IClass c in ModelStore.AllInstances<IClass>())  
      {  
#>  
   public partial class <#=c.Name#>  
   {   }  
<#  
      }  
#>  
}  
```  
  
##  <a name="What"></a> 如何使用文字產生  
 在需求或架構層級使用模型進行設計時，即可取得模型化的真正威力。 您可以使用文字範本來執行將高階想法轉換成程式碼的一些工作。 在許多情況下，這不會在 UML 模型中的項目與類別或程式碼的其他部分之間導致一對一對應關係。  
  
 甚至，轉換取決於您的問題網域；模型與程式碼之間沒有通用對應。  
  
 以下是透過模型產生程式碼的一些範例：  
  
-   **產品線**。 Fabrikam，Inc.建置和安裝機場行李處理系統。 在某個安裝與下一個安裝之間，大部分的軟體都極為類似，但是軟體組態取決於安裝的行李處理機制，以及這些組件如何透過傳送帶互連。 在合約開始，Fabrikam 分析師會討論機場管理需求，以及使用 UML 活動圖擷取硬體計劃。 在這個模型中，開發小組會產生組態檔、程式碼、計劃和使用者文件。 他們透過對程式碼進行手動加入和調整來完成工作。 隨著積累不同工作的經驗，即可擴充所產生資料的範圍。  
  
-   **模式**。 Contoso, Ltd 開發人員通常會建置網站，並使用 UML 類別圖來設計巡覽配置。 每個網頁都是由一個類別代表，關聯則代表巡覽連結。 開發人員會透過模型產生網站的大部分程式碼。 每個網頁都會對應至數個類別和資源檔項目。  這種方法的優點是每個網頁的建構都符合單一模式，因此會比手動撰寫的程式碼更為可靠並具彈性。 模式是在產生範本中，模型則是用來擷取變數層面。  
  
-   **結構描述**。 Humongous Insurance 全球有數千個系統。 這些系統都使用不同的資料庫、語言和介面。 中央架構小組會在內部發行商務概念和流程的模型。 在這些模型中，本地小組會產生其資料庫的各部分，並交換結構描述、程式碼中的宣告等。 模型的圖形化呈現可協助小組討論提案。 小組會建立多個圖表，以顯示套用至不同商務區域的模型子集。 他們也會使用色彩來反白顯示隨時可能變更的區域。  
  
## <a name="important-techniques-for-generating-artifacts"></a>產生成品的重要技術  
 在上一個範例中，模型用於不同的商務相關用途，以及解譯模型項目 (例如類別和活動會根據應用程式而不同)。 透過模型產生成品時，下列技術十分有用。  
  
-   **設定檔**。 甚至，在一個商務區域內，項目類型的解譯可能會不同。 例如，在網站圖上，有些類別可能代表網頁，其他類別則代表內容區塊。 若要讓使用者更方便記錄這些差異，請定義造型。 造型也可能會附加套用至該類型之項目的其他屬性。 造型會封裝在設定檔內。 如需詳細資訊，請參閱 <<c0> [ 定義要擴充 UML 的設定檔](../modeling/define-a-profile-to-extend-uml.md)。  
  
     在範本程式碼中，可以輕鬆地存取物件上所定義的造型。 例如:   
  
    ```  
    public bool HasStereotype(IClass c, string profile, string stereo)  
    { return c.AppliedStereotypes.Any  
       (s => s.Profile == profile && s.Name == stereo ); }  
    ```  
  
-   **條件約束的模型**。 並非所有您可以建立的模型都適用於每種用途。 例如，在 Fabrikam 的機場行李模型中，報到櫃檯沒有外送傳送帶是不正確的。 您可以定義驗證函式，幫助使用者觀察這些條件約束。 如需詳細資訊，請參閱 <<c0> [ 定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)。  
  
-   **保留手動變更**。 只有一些方案檔才能透過模型產生。 在大部分情況下，您需要可以手動加入或調整產生的內容。 不過，重新執行範本轉換時，一定要保留這些手動變更。  
  
     您的範本產生的程式碼[!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]語言，它們應該產生部分類別，好讓開發人員可以加入方法和程式碼。 它也可用來將每個類別產生為一個配對：包含方法的抽象基底類別，以及只包含建構函式的繼承類別。 這可讓開發人員覆寫方法。 為了允許覆寫初始化，這項作業是在不同的方法中進行，而不是在建構函式中。  
  
     只要範本產生 XML 和其他類型的輸出，就可能很難區隔手動內容與產生的內容。 其中一種方法是在建置程序中建立合併兩個檔案的工作。 另一種方法是讓開發人員調整產生範本的本機複本。  
  
-   **將程式碼移到不同的組件**。 不建議在範本中撰寫大型程式碼主體。 最好保持區隔產生的內容不進行運算，而且編輯程式碼時也不支援文字範本。  
  
     而是，如果您需要執行大量運算來產生文字，請在不同的組件建置這些函式，並透過範本呼叫其方法。
