---
title: 將自訂架構驗證加入分層圖 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, adding custom validation
ms.assetid: fed7bc08-295a-46d6-9fd8-fb537f1f75f1
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9748f2f7b43426f7f981d027400f097b260bf23d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817512"
---
# <a name="add-custom-architecture-validation-to-layer-diagrams"></a>在分層圖中加入自訂架構驗證
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，使用者可以針對圖層模型驗證專案中的原始程式碼，以便他們可以確認原始碼符合分層圖上的相依性。 有標準的驗證演算法，但您可以定義自己的驗證擴充功能。  
  
 當使用者在分層圖上選取 [驗證架構]  命令時，會叫用標準驗證方法，後面接著任何已安裝的驗證擴充功能。  
  
> [!NOTE]
>  分層圖中的驗證與 UML 圖表中的驗證不同。 在分層圖中，主要目的是比較圖表與方案其他部分的程式碼。  
  
 您可以將圖層驗證擴充功能封裝成 Visual Studio 整合擴充功能 (VSIX)，您可將它散發給其他 Visual Studio 使用者。 您可以單獨將驗證程式放在 VSIX 中，或是在相同 VSIX 中將它與其他擴充功能結合。 您應該在單獨的 Visual Studio 專案中撰寫驗證程式的程式碼，而不是在與其他擴充功能相同的專案中。  
  
> [!WARNING]
>  建立驗證專案之後，請複製本主題結尾的 [範例程式碼](#example) ，然後視您的需要加以編輯。  
  
## <a name="requirements"></a>需求  
 請參閱 [需求](../modeling/extend-layer-diagrams.md#prereqs)。  
  
## <a name="defining-a-layer-validator-in-a-new-vsix"></a>在新的 VSIX 中定義圖層驗證程式  
 建立驗證程式最快速的方法是使用專案範本。 這樣做會將程式碼和 VSIX 資訊清單放入相同的專案中。  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>使用專案範本定義擴充功能  
  
1. 使用 [檔案]  功能表上的 [新增專案]  命令，在新的方案中建立專案。  
  
2. 在 [新增專案]  對話方塊中，於 [模型專案] 之下，選取 [圖層設計工具驗證擴充功能] 。  
  
    此範本隨即建立包含小型範例的專案。  
  
   > [!WARNING]
   >  Makethe 範本正常運作：  
   > 
   > - 編輯對 `LogValidationError` 的呼叫，移除選擇性引數 `errorSourceNodes` 和 `errorTargetNodes`。  
   >   -   如果您使用自訂屬性，套用更新中所述[將自訂屬性加入分層圖](../modeling/add-custom-properties-to-layer-diagrams.md)。  
  
3. 編輯程式碼以定義您的驗證。 如需詳細資訊，請參閱 [程式設計驗證](#programming)。  
  
4. 若要測試擴充功能，請參閱 [圖層驗證偵錯](#debugging)。  
  
   > [!NOTE]
   >  只有在特定情況下才會呼叫您的方法，且中斷點將不會自動運作。 如需詳細資訊，請參閱 [圖層驗證偵錯](#debugging)。  
  
5. 主要執行個體中安裝擴充功能[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，或其他電腦上，尋找 **.vsix**中的檔案*bin\\*。 將它複製到您要安裝它的電腦上，然後按兩下該檔案。 若要對其解除安裝，請使用 [工具]  功能表上的 [擴充功能和更新]  。  
  
## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>將圖層驗證程式加入個別的 VSIX 中  
 如果您想要建立一個包含圖層驗證程式、命令和其他擴充功能的 VSIX，建議您應建立單一專案來定義此 VSIX，並且針對處理常式建立個別專案。 如需其他類型的模型擴充功能資訊，請參閱[擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)。  
  
#### <a name="to-add-layer-validation-to-a-separate-vsix"></a>將圖層驗證加入個別的 VSIX  
  
1.  在新的或現有的 Visual Studio 方案中建立類別庫專案。 在 [新增專案]  對話方塊中，按一下 [Visual C#]  ，然後按一下 [類別庫] 。 這個專案會包含圖層驗證類別。  
  
2.  在您的方案中識別或建立 VSIX 專案。 VSIX 專案會包含名為 **source.extension.vsixmanifest**的檔案。 如果您必須加入 VSIX 專案，請遵循下列步驟：  
  
    1.  在 [新增專案]  對話方塊中，依序選擇 [Visual C#] 、[擴充性] 、[VSIX 專案] 。  
  
    2.  在 [方案總管] 中，在 VSIX 專案的捷徑功能表上，選擇 [設定為啟始專案] 。  
  
3.  在 **source.extension.vsixmanifest**的 [資產] 下，加入圖層驗證專案做為 MEF 元件：  
  
    1.  選擇 [新增] 。  
  
    2.  在 [加入新的資產]  對話方塊中，設定：  
  
          =   
  
          =   
  
          = *您的驗證程式專案*  
  
4.  您也必須將它加入做為圖層驗證：  
  
    1.  選擇 [新增] 。  
  
    2.  在 [加入新的資產]  對話方塊中，設定：  
  
         **Type** = **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. 這不是下拉式清單的其中一個選項。 您必須從鍵盤輸入。  
  
          =   
  
          = *您的驗證程式專案*  
  
5.  返回圖層驗證專案，然後加入下列專案參考：  
  
    |**參考資料**|**這可讓您執行**|  
    |-------------------|------------------------------------|  
    |Microsoft.VisualStudio.GraphModel.dll|讀取架構圖形|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|讀取與圖層相關聯的程式碼 DOM|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|讀取圖層模型|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|讀取和更新圖形和圖表。|  
    |System.ComponentModel.Composition|使用 Managed Extensibility Framework (MEF) 定義驗證元件|  
    |Microsoft.VisualStudio.Modeling.Sdk.[版本]|定義模型擴充功能|  
  
6.  將本主題結尾處的範例程式碼複製到驗證程式庫專案中的類別檔案，以包含您的驗證程式碼。 如需詳細資訊，請參閱 [程式設計驗證](#programming)。  
  
7.  若要測試擴充功能，請參閱 [圖層驗證偵錯](#debugging)。  
  
    > [!NOTE]
    >  只有在特定情況下才會呼叫您的方法，且中斷點將不會自動運作。 如需詳細資訊，請參閱 [圖層驗證偵錯](#debugging)。  
  
8.  若要在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的主要執行個體或其他電腦上安裝此擴充功能，請在 **bin\*** 目錄中尋找 **.vsix** 檔案。 將它複製到您想要安裝 VSIX 的電腦。 在 Windows 檔案總管中按兩下 VSIX 檔案。 (Windows 8 中為檔案總管。)  
  
     若要對其解除安裝，請使用 [工具]  功能表上的 [擴充功能和更新]  。  
  
##  <a name="programming"></a> 程式設計驗證  
 若要定義圖層驗證擴充功能，您可以定義具有下列特性的類別：  
  
- 宣告的整體形式如下：  
  
  ```  
  
  using System.ComponentModel.Composition;  
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;  
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
  using Microsoft.VisualStudio.GraphModel;  
  ...  
   [Export(typeof(IValidateArchitectureExtension))]  
    public partial class Validator1Extension :  
                    IValidateArchitectureExtension  
    {  
      public void ValidateArchitecture(Graph graph)  
      {  
         GraphSchema schema = graph.DocumentSchema;  
        ...  
    } }  
  ```  
  
- 當您發現錯誤時，可以使用 `LogValidationError()`回報。  
  
  > [!WARNING]
  >  請不要使用 `LogValidationError`的選擇性參數。  
  
  當使用者叫用 [驗證架構]  功能表命令時，圖層執行階段系統會分析圖層及其成品，以產生圖形。 圖形包含四個部分：  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案的圖層模型，在圖形中以節點和連結表示。  
  
- 定義在方案中並以節點表示的程式碼、專案項目和其他成品，以及代表分析程序所探索到之相依性的連結。  
  
- 從圖層節點到程式碼成品節點的連結。  
  
- 代表驗證程式所發現之錯誤的節點。  
  
  建構好圖形後，會呼叫標準驗證方法。 完成時，任何已安裝的擴充驗證方法會依未指定的順序呼叫。 圖形會傳遞至每個 `ValidateArchitecture` 方法，它可以掃描圖形並報告其所找到的任何錯誤。  
  
> [!NOTE]
>  這與套用至 UML 圖表的驗證程序不同，而且與可以用於定義域專屬語言的驗證程序不同。  
  
 驗證方法不應該變更圖層模型或正在驗證的程式碼。  
  
 圖形模型定義於 <xref:Microsoft.VisualStudio.GraphModel>。 其主體類別是 <xref:Microsoft.VisualStudio.GraphModel.GraphNode> 和 <xref:Microsoft.VisualStudio.GraphModel.GraphLink>。  
  
 每個節點和每個連結都有一個或多個類別，此類別會指定其所代表的項目或關聯性的類型。 典型圖形的節點有下列類別：  
  
- Dsl.LayerModel  
  
- Dsl.Layer  
  
- Dsl.Reference  
  
- CodeSchema_Type  
  
- CodeSchema_Namespace  
  
- CodeSchema_Type  
  
- CodeSchema_Method  
  
- CodeSchema_Field  
  
- CodeSchema_Property  
  
  從圖層到程式碼中之項目的連結具有「代表」的類別。  
  
##  <a name="debugging"></a> 驗證偵錯  
 若要對您的圖層驗證擴充功能進行偵錯，請按 CTRL + F5。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗執行個體隨即開啟。 在本執行個體中，開啟或建立圖層模型。 此模型必須與程式碼相關聯，而且必須有至少一個相依性。  
  
### <a name="test-with-a-solution-that-contains-dependencies"></a>測試包含相依性的方案  
 除非有下列特性，否則不會執行驗證：  
  
- 在分層圖上有至少一個相依性連結。  
  
- 在模型中有與程式碼項目相關聯的圖層。  
  
  第一次啟動 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗執行個體測試驗證擴充功能時，請開啟或建立具有下列特性的方案。  
  
### <a name="run-clean-solution-before-validate-architecture"></a>在驗證架構之前執行清除方案  
 每當您更新驗證程式碼時，請使用實驗性方案中 [建置]  功能表上的 [清除方案]  命令，然後再測試驗證命令。 這是必要的，因為會快取驗證結果。 如果您未更新測試分層圖或其程式碼，將不會執行驗證方法。  
  
### <a name="launch-the-debugger-explicitly"></a>明確地啟動偵錯工具  
 驗證會在個別的處理序中執行。 因此，不會觸發驗證方法中的中斷點。 驗證開始時，您必須明確地將偵錯工具附加到處理序。  
  
 若要將偵錯工具附加到驗證處理序，請在驗證方法的開頭，插入對 `System.Diagnostics.Debugger.Launch()` 的呼叫。 偵錯對話方塊出現時，選取 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的主要執行個體。  
  
 或者，您可以插入對 `System.Windows.Forms.MessageBox.Show()`的呼叫。 訊息方塊出現時，請移至 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的主要執行個體，並在 [偵錯]  功能表上，按一下 [附加至處理序] 。 選取名為 **Graphcmd.exe**的處理序。  
  
 一律藉由按 CTRL + F5 ([啟動但不偵錯]) 來啟動實驗執行個體。  
  
### <a name="deploying-a-validation-extension"></a>部署驗證擴充功能  
 若要在已安裝 Visual Studio 適當版本的電腦上安裝您的驗證擴充功能，請在目標電腦上開啟 VSIX 檔案。 若要在已安裝 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 的電腦上安裝，您必須手動將 VSIX 內容解壓縮到 [擴充功能] 資料夾。 如需詳細資訊，請參閱 <<c0> [ 部署圖層模型擴充功能](../modeling/deploy-a-layer-model-extension.md)。  
  
##  <a name="example"></a> Example code  
  
```csharp  
using System;  
using System.ComponentModel.Composition;  
using System.Globalization;  
using System.Linq;  
using System.Text.RegularExpressions;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.GraphModel;  
  
namespace Validator3  
{  
    [Export(typeof(IValidateArchitectureExtension))]  
    public partial class Validator3Extension : IValidateArchitectureExtension  
    {  
        /// <summary>  
        /// Validate the architecture  
        /// </summary>  
        /// <param name="graph">The graph</param>  
        public void ValidateArchitecture(Graph graph)  
        {  
            if (graph == null) throw new ArgumentNullException("graph");  
  
            // Uncomment the line below to debug this extension during validation  
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);  
  
            // Get all layers on the diagram  
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))  
            {  
                System.Threading.Thread.Sleep(100);  
                // Get the required regex property from the layer node  
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;  
                if (!string.IsNullOrEmpty(regexPattern))  
                {  
                    Regex regEx = new Regex(regexPattern);  
  
                    // Get all referenced types in this layer including those from nested layers so each  
                    // type is validated against all containing layer constraints.  
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))  
                    {  
                        // Check the type name against the required regex                          
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);  
                        string typeName = builder.Type.Name;  
                        if (!regEx.IsMatch(typeName))  
                        {  
                            // Log an error  
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);  
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);  
                        }  
                    }  
                }  
  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [擴充分層圖](../modeling/extend-layer-diagrams.md)



