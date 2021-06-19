---
title: 將主機連線至產生的指示詞處理器
description: 瞭解如何擴充您的自訂主機，使其支援可呼叫指示詞處理器的文字模板。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: ed51688e5b65e34d7067963dbf7b839b1f022768
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388317"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>逐步解說：將主機連線至產生的指示詞處理器

您可以撰寫自己的主機來處理文字模板。 在 [逐步解說：建立自訂文字模板主](../modeling/walkthrough-creating-a-custom-text-template-host.md)控制項時，會示範基本的自訂主機。 您可以擴充該主機，以新增產生多個輸出檔案的功能。

在這個逐步解說中，您會展開自訂主機，讓它支援呼叫指示詞處理器的文字模板。 當您定義網域指定的語言時，它會產生網域模型的指示詞 *處理器* 。 指示詞處理器可讓使用者更輕鬆地撰寫存取模型的範本，減少在範本中撰寫元件和匯入指示詞的需求。

> [!NOTE]
> 本逐步解說是根據 [逐步解說：建立自訂文字模板主機](../modeling/walkthrough-creating-a-custom-text-template-host.md)。 先執行該逐步解說。

本逐步解說包含下列工作：

- 使用 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 產生以網域模型為基礎的指示詞處理器。

- 將自訂文字模板主機連接至產生的指示詞處理器。

- 使用產生的指示詞處理器來測試自訂主機。

## <a name="prerequisites"></a>必要條件

若要定義 DSL，您必須已安裝下列元件：

| 元件 | 連結 |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Visual Studio Visualization and Modeling SDK | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

此外，您必須在 [逐步解說：建立自訂文字模板主機](../modeling/walkthrough-creating-a-custom-text-template-host.md)中建立自訂文字模板轉換。

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>使用 Domain-Specific 語言工具來產生指示詞處理器

在這個逐步解說中，您會使用 Domain-Specific 的語言設計工具，為 [方案 DSLMinimalTest] 建立特定領域的語言。

1. 建立具有下列特性的特定領域語言方案：

   - 名稱： DSLMinimalTest

   - 解決方案範本：基礎語言

   - 副檔名：分鐘

   - 公司名稱： Fabrikam

   如需有關建立特定領域語言解決方案的詳細資訊，請參閱 [如何：建立 Domain-Specific 語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。

2. 在 [建置] 功能表上，按一下 [建置方案]。

   > [!IMPORTANT]
   > 此步驟會產生指示詞處理器，並在登錄中新增該處理器的金鑰。

3. 在 **[偵錯]** 功能表上，按一下 **[開始偵錯]** 。

    Visual Studio 的第二個實例隨即開啟。

4. 在實驗組建的 **方案總管** 中，按兩下檔案 **範例。**

    檔案隨即在設計工具中開啟。 請注意，此模型有兩個元素： ExampleElement1 和 ExampleElement2，以及兩者之間的連結。

5. 關閉 Visual Studio 的第二個實例。

6. 儲存方案，然後關閉 Domain-Specific 語言設計工具。

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>將自訂文字模板主機連接至指示詞處理器

產生指示詞處理器之後，您可以連接指示詞處理器和您在 [逐步解說：建立自訂文字模板主機](../modeling/walkthrough-creating-a-custom-text-template-host.md)中所建立的自訂文字模板主機。

1. 開啟 CustomHost 方案。

2. 在 [專案] 功能表上，按一下 [加入參考]。

     [ **加入參考** ] 對話方塊隨即開啟，並顯示 [ **.net** ] 索引標籤。

3. 加入下列參考：

    - VisualStudio （node.js）

    - VisualStudio （node.js）。

    - VisualStudio. TextTemplating 11。0

    - VisualStudio. TextTemplating. 11。0

    - VisualStudio. TextTemplating. 11。0

    - VisualStudio. TextTemplating. Vshost.exe 11。0

4. 在程式 .cs 或 Module1 的頂端，加入下列程式程式碼：

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. 找出屬性的程式碼 `StandardAssemblyReferences` ，並將它取代為下列程式碼：

    > [!NOTE]
    > 在此步驟中，您會將參考新增至您的主機將支援之產生的指示詞處理器所需的元件。

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

6. 找出函式的程式碼 `ResolveDirectiveProcessor` ，並將它取代為下列程式碼：

    > [!IMPORTANT]
    > 此程式碼包含您想要連接之所產生之指示詞處理器名稱的硬式編碼參考。 您可以輕鬆地使其更為普遍，在這種情況下，它會尋找登錄中列出的所有指示詞處理器，並嘗試尋找相符項。 在此情況下，主機會使用任何產生的指示詞處理器。

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

7. 按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。

8. 在 [建置] 功能表上，按一下 [建置方案]。

## <a name="test-the-custom-host-with-the-directive-processor"></a>使用指示詞處理器測試自訂主機

若要測試自訂文字模板主機，您必須先撰寫可呼叫所產生之指示詞處理器的文字模板。 然後您執行自訂主機，將文字模板的名稱傳遞給它，並確認指示詞已正確處理。

### <a name="create-a-text-template-to-test-the-custom-host"></a>建立文字模板以測試自訂主機

1. 建立文字檔，並將它命名為 `TestTemplateWithDP.tt` 。 您可以使用任何文字編輯器（例如 [記事本]）來建立檔案。

2. 將下列程式碼加入至此文字檔中：

    > [!NOTE]
    > 文字模板的程式設計語言不需要與自訂主控制項的程式設計語言相符。

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

3. 在程式碼中，將取代 \<YOUR PATH> 為您在第一個程式中所建立之設計特定語言的範例檔案路徑。

4. 儲存並關閉檔案。

### <a name="test-the-custom-host"></a>測試自訂主機

1. 開啟命令提示字元視窗。

2. 輸入自訂主應用程式可執行檔的路徑，但是還不要按 ENTER。

     例如，輸入：

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > 您可以流覽至 **Windows 檔案總管** 中的檔案 CustomHost.exe，然後將檔案拖曳到 [命令提示字元] 視窗中，而不是輸入位址。

3. 輸入空格。

4. 輸入文字範本檔的路徑，然後按 ENTER。

     例如，輸入：

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > 您可以流覽至 **Windows 檔案總管** 中的檔案 TestTemplateWithDP.txt，然後將檔案拖曳到 [命令提示字元] 視窗中，而不是輸入位址。

     自訂主應用程式會執行並啟動文字模板轉換流程。

5. 在 **Windows 檔案總管** 中，流覽至包含檔案 TestTemplateWithDP.txt 的資料夾。

     此資料夾也包含 TestTemplateWithDP1.txt 的檔案。

6. 開啟這個檔案來查看文字範本轉換的結果。

     產生之文字輸出的結果隨即出現，且看起來應該像這樣：

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>另請參閱

- [逐步解說：建立自訂文字範本主機](../modeling/walkthrough-creating-a-custom-text-template-host.md)
