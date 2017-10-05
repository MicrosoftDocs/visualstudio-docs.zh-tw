---
title: "逐步解說： 連接到產生指示詞處理器的主機 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 47
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5bfeb8ea94b457114d7ba6ab74b783972e64350c
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>逐步解說：將主機連接至產生的指示詞處理器
您可以撰寫自己的主機處理文字範本。 示範基本的自訂主機[逐步解說： 建立自訂文字範本主機](../modeling/walkthrough-creating-a-custom-text-template-host.md)。 您可以擴充該主應用程式加入功能，例如產生多個輸出檔案。  
  
 在本逐步解說中，您會展開您的自訂主機，以支援呼叫指示詞處理器的文字範本。 當您定義的特定領域語言時，它會產生*指示詞處理器*網域模型。 指示詞處理器，可讓使用者更輕鬆地撰寫存取模型，也不需要撰寫組件並匯入之範本中的指示詞的範本。  
  
> [!WARNING]
>  本逐步解決建置於[逐步解說： 建立自訂文字範本主應用](../modeling/walkthrough-creating-a-custom-text-template-host.md)。 第一次執行該逐步解說。  
  
 本逐步解說包含下列工作：  
  
-   使用[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]產生網域模型為基礎的指示詞處理器。  
  
-   連線的自訂文字範本主應用程式產生指示詞處理器。  
  
-   測試自訂主應用程式以產生指示詞處理器。  
  
## <a name="prerequisites"></a>必要條件  
 若要定義 DSL，您必須已安裝下列元件：  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Visual Studio Visualization and Modeling SDK||  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
 此外，您必須擁有在建立自訂文字範本轉換[逐步解說： 建立自訂文字範本主機](../modeling/walkthrough-creating-a-custom-text-template-host.md)。  
  
## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>使用網域特定領域語言工具來產生指示詞處理器  
 在本逐步解說中，您可以使用網域特定語言設計工具精靈來建立特定領域語言方案 DSLMinimalTest。  
  
#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>要用於特定領域語言工具產生的網域模型為基礎的指示詞處理器  
  
1.  建立具有下列特性的特定領域語言方案：  
  
    -   名稱： DSLMinimalTest  
  
    -   方案範本： 最少的語言  
  
    -   副檔名： 最小值  
  
    -   公司名稱： Fabrikam  
  
     如需有關建立特定領域語言方案的詳細資訊，請參閱[How to： 建立特定領域語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。  
  
2.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
    > [!IMPORTANT]
    >  這個步驟會產生指示詞處理器，並將它的索引鍵，在登錄中。  
  
3.  按一下 [偵錯] 功能表上的 [開始偵錯]。  
  
     第二個執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]隨即開啟。  
  
4.  在實驗組建中，在**方案總管 中**，按兩下檔案**sample.min**。  
  
     在設計工具中，開啟檔案。 請注意，此模型有兩個項目、 ExampleElement1 ExampleElement2，以及它們之間的連結。  
  
5.  關閉第二個執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
6.  儲存方案，然後關閉 特定領域語言設計工具。  
  
## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>連線的自訂文字範本主應用程式的指示詞處理器  
 產生指示詞處理器之後，連線指示詞處理器和您在建立自訂文字範本主機[逐步解說： 建立自訂文字範本主機](../modeling/walkthrough-creating-a-custom-text-template-host.md)。  
  
#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>若要連線的自訂文字範本主應用程式產生指示詞處理器  
  
1.  開啟 CustomHost 方案。  
  
2.  在 [專案] 功能表上，按一下 [新增參考]。  
  
     **加入參考**對話方塊隨即開啟與**.NET**顯示索引標籤。  
  
3.  加入下列參考：  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0  
  
4.  在 Program.cs 或 Module1.vb 頂端，加入下列程式碼行：  
  
    ```csharp  
    using Microsoft.Win32;  
    ```  
  
    ```vb  
    Imports Microsoft.Win32  
    ```  
  
5.  找出屬性的程式碼`StandardAssemblyReferences`，並取代為下列程式碼：  
  
    > [!NOTE]
    >  在此步驟中，您可以將產生指示詞處理器，您的主機可以支援所需的組件的參考。  
  
    ```csharp  
    //the host can provide standard assembly references  
    //the engine will use these references when compiling and  
    //executing the generated transformation class  
    //--------------------------------------------------------------  
    public IList<string> StandardAssemblyReferences  
    {  
        get  
        {  
            return new string[]  
            {  
                //if this host searches standard paths and the GAC  
                //we can specify the assembly name like this:  
                //"System"  
                //since this host only resolves assemblies from the   
                //fully qualified path and name of the assembly  
                //this is a quick way to get the code to give us the  
                //fully qualified path and name of the System assembly  
                //---------------------------------------------------------  
                typeof(System.Uri).Assembly.Location,  
                            typeof(System.Uri).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location  
  
            };  
        }  
    }  
    ```  
  
6.  找出函式的程式碼`ResolveDirectiveProcessor`，並取代為下列程式碼：  
  
    > [!IMPORTANT]
    >  此程式碼會包含硬式編碼參考產生的指示詞處理器，您要連接的名稱。 您無法輕鬆地進行這一般，在此情況下會尋找所有指示詞處理器之登錄中列出，並嘗試尋找相符項目。 在此情況下，主機會使用任何產生的指示詞處理器。  
  
    ```csharp  
    //the engine calls this method based on the directives the user has   
            //specified it in the text template  
            //this method can be called 0, 1, or more times  
            //---------------------------------------------------------------------  
            public Type ResolveDirectiveProcessor(string processorName)  
            {  
                //check the processor name, and if it is the name of the processor the   
                //host wants to support, return the type of the processor  
                //---------------------------------------------------------------------  
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)  
                {  
                    try  
                    {  
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";  
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))  
                        {  
                            if (specificKey != null)  
                            {  
                                List<string> names = new List<String>(specificKey.GetValueNames());  
                                string classValue = specificKey.GetValue("Class") as string;  
                                if (!string.IsNullOrEmpty(classValue))  
                                {  
                                    string loadValue = string.Empty;  
                                    System.Reflection.Assembly processorAssembly = null;  
                                    if (names.Contains("Assembly"))  
                                    {  
                                        loadValue = specificKey.GetValue("Assembly") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //the assembly must be installed in the GAC  
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);  
                                        }  
                                    }  
                                    else if (names.Contains("CodeBase"))  
                                    {  
                                        loadValue = specificKey.GetValue("CodeBase") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //loading local assembly  
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);  
                                        }  
                                    }  
                                    if (processorAssembly == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    Type processorType = processorAssembly.GetType(classValue);  
                                    if (processorType == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    return processorType;  
                                }  
                            }  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        //if the directive processor can not be found, throw an error  
                        throw new Exception("Directive Processor not found");  
                    }  
                }  
  
                //if the directive processor is not one this host wants to support  
                throw new Exception("Directive Processor not supported");  
            }  
    ```  
  
7.  在**檔案**功能表上，按一下 **全部儲存**。  
  
8.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
## <a name="testing-the-custom-host-with-the-directive-processor"></a>測試自訂主應用程式與指示詞處理器  
 第一次來測試自訂文字範本主應用程式，您必須撰寫呼叫產生指示詞處理器的文字範本。 然後您執行自訂主應用程式、 傳遞給它的文字範本名稱，並確認已正確處理指示詞。  
  
#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>若要建立文字範本以測試自訂主應用程式  
  
1.  建立文字檔案，並將其命名`TestTemplateWithDP.tt`。 您可以使用任何文字編輯器，例如 [記事本] 來建立檔案。  
  
2.  將下列程式碼加入至此文字檔中：  
  
    > [!NOTE]
    >  文字範本的程式語言不需要符合自訂主應用程式。  
  
    ```csharp  
    Text Template Host Test  
  
    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
    <# //this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
    <# //uncomment this line to test that the host allows the engine to set the extension #>  
    <# //@ output extension=".htm" #>  
  
    <# //uncomment this line if you want to see the generated transformation class #>  
    <# //System.Diagnostics.Debugger.Break(); #>  
    <# //this code uses the results of the examplemodel directive #>  
    <#  
        foreach ( ExampleElement box in this.ExampleModel.Elements )   
        {   
            WriteLine("Box: {0}", box.Name);  
  
            foreach (ExampleElement linkedTo in box.Targets)  
            {  
                WriteLine("Linked to: {0}", linkedTo.Name);  
            }  
  
            foreach (ExampleElement linkedFrom in box.Sources)  
            {  
                WriteLine("Linked from: {0}", linkedFrom.Name);  
            }  
  
            WriteLine("");  
        }   
    #>  
    ```  
  
    ```vb  
    Text Template Host Test  
  
    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
  
    <# 'this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
  
    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>  
    <# '@ output extension=".htm" #>  
  
    <# 'Uncomment this line if you want to see the generated transformation class. #>  
    <# 'System.Diagnostics.Debugger.Break() #>  
  
    <# 'this code uses the results of the examplemodel directive #>  
  
    <#      
       For Each box as ExampleElement In Me.ExampleModel.Elements   
  
           WriteLine("Box: {0}", box.Name)  
  
            For Each LinkedTo as ExampleElement In box.Targets  
                WriteLine("Linked to: {0}", LinkedTo.Name)  
            Next  
  
            For Each LinkedFrom as ExampleElement In box.Sources  
                WriteLine("Linked from: {0}", LinkedFrom.Name)  
            Next  
  
            WriteLine("")  
  
       Next   
    #>  
    ```  
  
3.  在程式碼，取代\<您的路徑 > Sample.min 檔案從您在第一個程序中建立設計特定語言的路徑。  
  
4.  儲存並關閉檔案。  
  
#### <a name="to-test-the-custom-host"></a>若要測試自訂主應用程式  
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  輸入自訂主應用程式可執行檔的路徑，但是還不要按 ENTER。  
  
     例如，輸入：  
  
     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`  
  
    > [!NOTE]
    >  不要輸入位置，您可以瀏覽至 CustomHost.exe 檔中**Windows 檔案總管**，然後將檔案拖曳到 [命令提示字元] 視窗。  
  
3.  輸入空格。  
  
4.  輸入文字範本檔的路徑，然後按 ENTER。  
  
     例如，輸入：  
  
     `<YOUR PATH>TestTemplateWithDP.txt`  
  
    > [!NOTE]
    >  您可以不要輸入位置，瀏覽檔案 TestTemplateWithDP.txt 中**Windows 檔案總管**，然後將檔案拖曳到 [命令提示字元] 視窗。  
  
     自訂主應用程式會執行，並開始文字範本轉換流程。  
  
5.  在**Windows 檔案總管**，瀏覽至包含 TestTemplateWithDP.txt 檔案的資料夾。  
  
     這個資料夾也包含檔案 TestTemplateWithDP1.txt。  
  
6.  開啟這個檔案來查看文字範本轉換的結果。  
  
     產生的文字輸出的結果會出現，而且應該看起來像這樣：  
  
    ```  
    Text Template Host Test  
  
    Box: ExampleElement1  
    Linked to: ExampleElement2  
  
    Box: ExampleElement2  
    Linked from: ExampleElement1  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：建立自訂文字範本主機](../modeling/walkthrough-creating-a-custom-text-template-host.md)

