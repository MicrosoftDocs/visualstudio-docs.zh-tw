---
title: "逐步解說： 建立自訂指示詞處理器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, custom directive processors
- walkthroughs [text templates], directive processor
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e50e433ea3f954efd085a02a3e29a0eff958da0c
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="walkthrough-creating-a-custom-directive-processor"></a>逐步解說：建立自訂指示詞處理器
*指示詞處理器*碼加入至工作*產生轉換類別*。 如果您呼叫*指示詞*從*文字範本*，文字範本中所撰寫的程式碼的其餘部分可以依賴指示詞提供的功能。  
  
 您可以撰寫專屬自訂指示詞處理器。 這可讓您自訂文字範本。 若要建立自訂指示詞處理器，您可以建立繼承 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 的類別。  
  
 本逐步解說將會說明的工作包括下列各項：  
  
-   建立自訂指示詞處理器  
  
-   註冊指示詞處理器  
  
-   測試指示詞處理器  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   Visual Studio 2010  
  
-   Visual Studio 2010 SDK  
  
## <a name="creating-a-custom-directive-processor"></a>建立自訂指示詞處理器  
 在本逐步解說中，您將會建立自訂指示詞處理器。 您要加入讀取 XML 檔的自訂指示詞，並將其儲存在 <xref:System.Xml.XmlDocument> 變數中，然後透過屬性予以公開。 在＜測試指示詞處理器＞一節中，您會在文字範本中使用這個屬性來存取 XML 檔。  
  
 對自訂指示詞的呼叫如下所示：  
  
 `<#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<Your Path>DocFile.xml" #>`  
  
 自訂指示詞處理器會將變數和屬性加入至產生的轉換類別中。 您撰寫的指示詞會使用 <xref:System.CodeDom> 類別來建立引擎要加入至產生之轉換類別中的程式碼。 <xref:System.CodeDom> 類別會根據 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 指示詞之 `language` 參數中所指定的語言，使用 Visual C# 或 `template` 來建立程式碼。 指示詞處理器的語言與存取指示詞處理器之文字範本的語言不一定要相符。  
  
 指示詞建立的程式碼如下所示：  
  
```csharp  
private System.Xml.XmlDocument document0Value;  
  
public virtual System.Xml.XmlDocument Document0  
{  
  get  
  {  
    if ((this.document0Value == null))  
    {  
      this.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>);  
    }  
    return this.document0Value;  
  }  
}  
```  
  
```vb  
Private document0Value As System.Xml.XmlDocument  
  
Public Overridable ReadOnly Property Document0() As System.Xml.XmlDocument  
    Get  
        If (Me.document0Value Is Nothing) Then  
            Me.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>)  
        End If  
        Return Me.document0Value  
    End Get  
End Property  
```  
  
#### <a name="to-create-a-custom-directive-processor"></a>若要建立自訂指示詞處理器  
  
1.  在 Visual Studio 中建立 C# 或 Visual Basic 類別庫專案，並命名為 CustomDP。  
  
    > [!NOTE]
    >  如果您想要在多台電腦上安裝指示詞處理器，最好是使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 擴充功能 (VSIX) 專案，並在擴充功能中包含 .pkgdef 檔。 如需詳細資訊，請參閱[部署自訂指示詞處理器](../modeling/deploying-a-custom-directive-processor.md)。  
  
2.  加入下列組件的參考：  
  
    -   **Microsoft.VisualStudio.TextTemplating。\*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.Interfaces。\*.0**  
  
3.  中的程式碼取代**Class1**為下列程式碼。 下列程式碼會定義繼承 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 類別的 CustomDirectiveProcessor 類別，並實作必要的方法。  
  
    ```csharp  
    using System;  
    using System.CodeDom;  
    using System.CodeDom.Compiler;  
    using System.Collections.Generic;  
    using System.Globalization;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using Microsoft.VisualStudio.TextTemplating;  
  
    namespace CustomDP  
    {  
        public class CustomDirectiveProcessor : DirectiveProcessor  
        {  
            //this buffer stores the code that is added to the   
            //generated transformation class after all the processing is done   
            //---------------------------------------------------------------------  
            private StringBuilder codeBuffer;  
  
            //Using a Code Dom Provider creates code for the   
            //generated transformation class in either Visual Basic or C#.  
            //If you want your directive processor to support only one language, you  
            //can hard code the code you add to the generated transformation class.  
            //In that case, you do not need this field.  
            //--------------------------------------------------------------------------  
            private CodeDomProvider codeDomProvider;  
  
            //this stores the full contents of the text template that is being processed  
            //--------------------------------------------------------------------------  
            private String templateContents;  
  
            //These are the errors that occur during processing. The engine passes   
            //the errors to the host, and the host can decide how to display them,  
            //for example the the host can display the errors in the UI  
            //or write them to a file.  
            //---------------------------------------------------------------------  
            private CompilerErrorCollection errorsValue;  
            public new CompilerErrorCollection Errors  
            {  
                get { return errorsValue; }  
            }  
  
            //Each time this directive processor is called, it creates a new property.  
            //We count how many times we are called, and append "n" to each new  
            //property name. The property names are therefore unique.  
            //-----------------------------------------------------------------------------  
            private int directiveCount = 0;  
  
            public override void Initialize(ITextTemplatingEngineHost host)  
            {  
                //we do not need to do any initialization work  
            }  
  
            public override void StartProcessingRun(CodeDomProvider languageProvider, String templateContents, CompilerErrorCollection errors)  
            {  
                //the engine has passed us the language of the text template  
                //we will use that language to generate code later  
                //----------------------------------------------------------  
                this.codeDomProvider = languageProvider;  
                this.templateContents = templateContents;  
                this.errorsValue = errors;  
  
                this.codeBuffer = new StringBuilder();  
            }  
  
            //Before calling the ProcessDirective method for a directive, the   
            //engine calls this function to see whether the directive is supported.  
            //Notice that one directive processor might support many directives.  
            //---------------------------------------------------------------------  
            public override bool IsDirectiveSupported(string directiveName)  
            {  
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    return true;  
                }  
                if (string.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    return true;  
                }  
                return false;  
            }  
  
            public override void ProcessDirective(string directiveName, IDictionary<string, string> arguments)  
            {  
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    string fileName;  
  
                    if (!arguments.TryGetValue("FileName", out fileName))  
                    {  
                        throw new DirectiveProcessorException("Required argument 'FileName' not specified.");  
                    }  
  
                    if (string.IsNullOrEmpty(fileName))  
                    {  
                        throw new DirectiveProcessorException("Argument 'FileName' is null or empty.");  
                    }  
  
                    //Now we add code to the generated transformation class.  
                    //This directive supports either Visual Basic or C#, so we must use the  
                    //System.CodeDom to create the code.  
                    //If a directive supports only one language, you can hard code the code.  
                    //--------------------------------------------------------------------------  
  
                    CodeMemberField documentField = new CodeMemberField();  
  
                    documentField.Name = "document" + directiveCount + "Value";  
                    documentField.Type = new CodeTypeReference(typeof(XmlDocument));  
                    documentField.Attributes = MemberAttributes.Private;  
  
                    CodeMemberProperty documentProperty = new CodeMemberProperty();  
  
                    documentProperty.Name = "Document" + directiveCount;  
                    documentProperty.Type = new CodeTypeReference(typeof(XmlDocument));  
                    documentProperty.Attributes = MemberAttributes.Public;  
                    documentProperty.HasSet = false;  
                    documentProperty.HasGet = true;  
  
                    CodeExpression fieldName = new CodeFieldReferenceExpression(new CodeThisReferenceExpression(), documentField.Name);  
                    CodeExpression booleanTest = new CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, new CodePrimitiveExpression(null));  
                    CodeExpression rightSide = new CodeMethodInvokeExpression(new CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", new CodePrimitiveExpression(fileName));  
                    CodeStatement[] thenSteps = new CodeStatement[] { new CodeAssignStatement(fieldName, rightSide) };  
  
                    CodeConditionStatement ifThen = new CodeConditionStatement(booleanTest, thenSteps);  
                    documentProperty.GetStatements.Add(ifThen);  
  
                    CodeStatement s = new CodeMethodReturnStatement(fieldName);  
                    documentProperty.GetStatements.Add(s);  
  
                    CodeGeneratorOptions options = new CodeGeneratorOptions();  
                    options.BlankLinesBetweenMembers = true;  
                    options.IndentString = "    ";  
                    options.VerbatimOrder = true;  
                    options.BracingStyle = "C";  
  
                    using (StringWriter writer = new StringWriter(codeBuffer, CultureInfo.InvariantCulture))  
                    {  
                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options);  
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options);  
                    }  
  
                }//end CoolDirective  
  
                //One directive processor can contain many directives.  
                //If you want to support more directives, the code goes here...  
                //-----------------------------------------------------------------  
                if (string.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    //code for SuperCoolDirective goes here...  
                }//end SuperCoolDirective  
  
                //Track how many times the processor has been called.  
                //-----------------------------------------------------------------  
                directiveCount++;  
  
            }//end ProcessDirective  
  
            public override void FinishProcessingRun()  
            {  
                this.codeDomProvider = null;  
  
                //important: do not do this:  
                //the get methods below are called after this method   
                //and the get methods can access this field  
                //-----------------------------------------------------------------  
                //this.codeBuffer = null;  
            }  
  
            public override string GetPreInitializationCodeForProcessingRun()  
            {  
                //Use this method to add code to the start of the   
                //Initialize() method of the generated transformation class.  
                //We do not need any pre-initialization, so we will just return "".  
                //-----------------------------------------------------------------  
                //GetPreInitializationCodeForProcessingRun runs before the   
                //Initialize() method of the base class.  
                //-----------------------------------------------------------------  
                return String.Empty;  
            }  
  
            public override string GetPostInitializationCodeForProcessingRun()  
            {  
                //Use this method to add code to the end of the   
                //Initialize() method of the generated transformation class.  
                //We do not need any post-initialization, so we will just return "".  
                //------------------------------------------------------------------  
                //GetPostInitializationCodeForProcessingRun runs after the  
                //Initialize() method of the base class.  
                //-----------------------------------------------------------------  
                return String.Empty;  
            }  
  
            public override string GetClassCodeForProcessingRun()  
            {  
                //Return the code to add to the generated transformation class.  
                //-----------------------------------------------------------------  
                return codeBuffer.ToString();  
            }  
  
            public override string[] GetReferencesForProcessingRun()  
            {  
                //This returns the references that we want to use when   
                //compiling the generated transformation class.  
                //-----------------------------------------------------------------  
                //We need a reference to this assembly to be able to call   
                //XmlReaderHelper.ReadXml from the generated transformation class.  
                //-----------------------------------------------------------------  
                return new string[]  
                {  
                    "System.Xml",  
                    this.GetType().Assembly.Location  
                };  
            }  
  
            public override string[] GetImportsForProcessingRun()  
            {  
                //This returns the imports or using statements that we want to   
                //add to the generated transformation class.  
                //-----------------------------------------------------------------  
                //We need CustomDP to be able to call XmlReaderHelper.ReadXml  
                //from the generated transformation class.  
                //-----------------------------------------------------------------  
                return new string[]  
                {  
                    "System.Xml",  
                    "CustomDP"  
                };  
            }  
        }//end class CustomDirectiveProcessor  
  
        //-------------------------------------------------------------------------  
        // the code that we are adding to the generated transformation class   
        // will call this method  
        //-------------------------------------------------------------------------  
        public static class XmlReaderHelper  
        {  
            public static XmlDocument ReadXml(string fileName)  
            {  
                XmlDocument d = new XmlDocument();  
  
                using (XmlTextReader reader = new XmlTextReader(fileName))  
                {  
                    try  
                    {  
                        d.Load(reader);  
                    }  
                    catch (System.Xml.XmlException e)  
                    {  
                        throw new DirectiveProcessorException("Unable to read the XML file.", e);  
                    }  
                }  
                return d;  
            }  
        }//end class XmlReaderHelper  
    }//end namespace CustomDP  
    ```  
  
    ```vb  
    Imports System  
    Imports System.CodeDom  
    Imports System.CodeDom.Compiler  
    Imports System.Collections.Generic  
    Imports System.Globalization  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports Microsoft.VisualStudio.TextTemplating  
  
    Namespace CustomDP  
  
        Public Class CustomDirectiveProcessor  
        Inherits DirectiveProcessor  
  
            'this buffer stores the code that is added to the   
            'generated transformation class after all the processing is done   
            '---------------------------------------------------------------  
            Private codeBuffer As StringBuilder  
  
            'Using a Code Dom Provider creates code for the  
            'generated transformation class in either Visual Basic or C#.  
            'If you want your directive processor to support only one language, you  
            'can hard code the code you add to the generated transformation class.  
            'In that case, you do not need this field.  
            '--------------------------------------------------------------------------  
            Private codeDomProvider As CodeDomProvider  
  
            'this stores the full contents of the text template that is being processed  
            '--------------------------------------------------------------------------  
            Private templateContents As String  
  
            'These are the errors that occur during processing. The engine passes   
            'the errors to the host, and the host can decide how to display them,  
            'for example the the host can display the errors in the UI  
            'or write them to a file.  
            '---------------------------------------------------------------------  
            Private errorsValue As CompilerErrorCollection  
            Public Shadows ReadOnly Property Errors() As CompilerErrorCollection  
                Get  
                    Return errorsValue  
                End Get  
            End Property  
  
            'Each time this directive processor is called, it creates a new property.  
            'We count how many times we are called, and append "n" to each new  
            'property name. The property names are therefore unique.  
            '--------------------------------------------------------------------------  
            Private directiveCount As Integer = 0  
  
            Public Overrides Sub Initialize(ByVal host As ITextTemplatingEngineHost)  
  
                'we do not need to do any initialization work  
            End Sub  
  
            Public Overrides Sub StartProcessingRun(ByVal languageProvider As CodeDomProvider, ByVal templateContents As String, ByVal errors As CompilerErrorCollection)  
  
                'the engine has passed us the language of the text template  
                'we will use that language to generate code later  
                '----------------------------------------------------------  
                Me.codeDomProvider = languageProvider  
                Me.templateContents = templateContents  
                Me.errorsValue = errors  
  
                Me.codeBuffer = New StringBuilder()  
            End Sub  
  
            'Before calling the ProcessDirective method for a directive, the   
            'engine calls this function to see whether the directive is supported.  
            'Notice that one directive processor might support many directives.  
            '---------------------------------------------------------------------  
            Public Overrides Function IsDirectiveSupported(ByVal directiveName As String) As Boolean  
  
                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
                    Return True  
                End If  
  
                If String.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
                    Return True  
                End If  
  
                Return False  
            End Function  
  
            Public Overrides Sub ProcessDirective(ByVal directiveName As String, ByVal arguments As IDictionary(Of String, String))  
  
                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
  
                    Dim fileName As String  
  
                    If Not (arguments.TryGetValue("FileName", fileName)) Then  
                        Throw New DirectiveProcessorException("Required argument 'FileName' not specified.")  
                    End If  
  
                    If String.IsNullOrEmpty(fileName) Then  
                        Throw New DirectiveProcessorException("Argument 'FileName' is null or empty.")  
                    End If  
  
                    'Now we add code to the generated transformation class.  
                    'This directive supports either Visual Basic or C#, so we must use the  
                    'System.CodeDom to create the code.  
                    'If a directive supports only one language, you can hard code the code.  
                    '--------------------------------------------------------------------------  
  
                    Dim documentField As CodeMemberField = New CodeMemberField()  
  
                    documentField.Name = "document" & directiveCount & "Value"  
                    documentField.Type = New CodeTypeReference(GetType(XmlDocument))  
                    documentField.Attributes = MemberAttributes.Private  
  
                    Dim documentProperty As CodeMemberProperty = New CodeMemberProperty()  
  
                    documentProperty.Name = "Document" & directiveCount  
                    documentProperty.Type = New CodeTypeReference(GetType(XmlDocument))  
                    documentProperty.Attributes = MemberAttributes.Public  
                    documentProperty.HasSet = False  
                    documentProperty.HasGet = True  
  
                    Dim fieldName As CodeExpression = New CodeFieldReferenceExpression(New CodeThisReferenceExpression(), documentField.Name)  
                    Dim booleanTest As CodeExpression = New CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, New CodePrimitiveExpression(Nothing))  
                    Dim rightSide As CodeExpression = New CodeMethodInvokeExpression(New CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", New CodePrimitiveExpression(fileName))  
                    Dim thenSteps As CodeStatement() = New CodeStatement() {New CodeAssignStatement(fieldName, rightSide)}  
  
                    Dim ifThen As CodeConditionStatement = New CodeConditionStatement(booleanTest, thenSteps)  
                    documentProperty.GetStatements.Add(ifThen)  
  
                    Dim s As CodeStatement = New CodeMethodReturnStatement(fieldName)  
                    documentProperty.GetStatements.Add(s)  
  
                    Dim options As CodeGeneratorOptions = New CodeGeneratorOptions()  
                    options.BlankLinesBetweenMembers = True  
                    options.IndentString = "    "  
                    options.VerbatimOrder = True  
                    options.BracingStyle = "VB"  
  
                    Using writer As StringWriter = New StringWriter(codeBuffer, CultureInfo.InvariantCulture)  
  
                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options)  
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options)  
                    End Using  
  
                End If  'CoolDirective  
  
                'One directive processor can contain many directives.  
                'If you want to support more directives, the code goes here...  
                '-----------------------------------------------------------------  
                If String.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
  
                    'code for SuperCoolDirective goes here  
                End If 'SuperCoolDirective  
  
                'Track how many times the processor has been called.  
                '-----------------------------------------------------------------  
                directiveCount += 1  
            End Sub 'ProcessDirective  
  
            Public Overrides Sub FinishProcessingRun()  
  
                Me.codeDomProvider = Nothing  
  
                'important: do not do this:  
                'the get methods below are called after this method   
                'and the get methods can access this field  
                '-----------------------------------------------------------------  
                'Me.codeBuffer = Nothing  
            End Sub  
  
            Public Overrides Function GetPreInitializationCodeForProcessingRun() As String  
  
                'Use this method to add code to the start of the   
                'Initialize() method of the generated transformation class.  
                'We do not need any pre-initialization, so we will just return "".  
                '-----------------------------------------------------------------  
                'GetPreInitializationCodeForProcessingRun runs before the   
                'Initialize() method of the base class.  
                '-----------------------------------------------------------------  
                Return String.Empty  
            End Function  
  
            Public Overrides Function GetPostInitializationCodeForProcessingRun() As String  
  
                'Use this method to add code to the end of the   
                'Initialize() method of the generated transformation class.  
                'We do not need any post-initialization, so we will just return "".  
                '------------------------------------------------------------------  
                'GetPostInitializationCodeForProcessingRun runs after the  
                'Initialize() method of the base class.  
                '-----------------------------------------------------------------  
                Return String.Empty  
            End Function  
  
            Public Overrides Function GetClassCodeForProcessingRun() As String  
  
                'Return the code to add to the generated transformation class.  
                '-----------------------------------------------------------------  
                Return codeBuffer.ToString()  
            End Function  
  
            Public Overrides Function GetReferencesForProcessingRun() As String()  
  
                'This returns the references that we want to use when   
                'compiling the generated transformation class.  
                '-----------------------------------------------------------------  
                'We need a reference to this assembly to be able to call   
                'XmlReaderHelper.ReadXml from the generated transformation class.  
                '-----------------------------------------------------------------  
                Return New String() {"System.Xml", Me.GetType().Assembly.Location}  
            End Function  
  
            Public Overrides Function GetImportsForProcessingRun() As String()  
  
                'This returns the imports or using statements that we want to   
                'add to the generated transformation class.  
                '-----------------------------------------------------------------  
                'We need CustomDP to be able to call XmlReaderHelper.ReadXml  
                'from the generated transformation class.  
                '-----------------------------------------------------------------  
                Return New String() {"System.Xml", "CustomDP"}  
            End Function  
        End Class 'CustomDirectiveProcessor  
  
        '--------------------------------------------------------------------------  
        ' the code that we are adding to the generated transformation class   
        ' will call this method  
        '--------------------------------------------------------------------------  
        Public Class XmlReaderHelper  
  
            Public Shared Function ReadXml(ByVal fileName As String) As XmlDocument  
  
                Dim d As XmlDocument = New XmlDocument()  
  
                Using reader As XmlTextReader = New XmlTextReader(fileName)  
  
                    Try  
                        d.Load(reader)  
  
                    Catch e As System.Xml.XmlException  
  
                        Throw New DirectiveProcessorException("Unable to read the XML file.", e)  
                    End Try  
                End Using  
  
                Return d  
            End Function  
        End Class 'XmlReaderHelper  
  
    End Namespace  
    ```  
  
4.  如[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，開啟**專案**功能表，然後按一下**CustomDP 屬性**。 在**應用程式**索引標籤的**根命名空間**，刪除預設值， `CustomDP`。  
  
5.  在**檔案**功能表上，按一下 **全部儲存**。  
  
6.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
### <a name="build-the-project"></a>建置專案  
 建置專案。 在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
## <a name="registering-the-directive-processor"></a>註冊指示詞處理器  
 您可以從文字範本中呼叫指示詞之前[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，您必須新增登錄機碼指示詞處理器。  
  
> [!NOTE]
>  如果您想要在多台電腦上安裝指示詞處理器，最好是定義 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 擴充功能 (VSIX)，在其中包含 .pkgdef 檔和組件。 如需詳細資訊，請參閱[部署自訂指示詞處理器](../modeling/deploying-a-custom-directive-processor.md)。  
  
 指示詞處理器的機碼存在於下列登錄位置：  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors  
```  
  
 64 位元系統的登錄位置為：  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors  
```  
  
 在本節中，您會將自訂指示詞處理器的機碼加入至位於上述位置的登錄。  
  
> [!CAUTION]
>  不當編輯登錄可能會對系統造成嚴重損害。 變更登錄之前，務必先備份電腦上任何重要的資料。  
  
#### <a name="to-add-a-registry-key-for-the-directive-processor"></a>若要加入指示詞處理器的登錄機碼  
  
1.  執行`regedit`使用 [開始] 功能表或命令列命令。  
  
2.  瀏覽至位置**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**，然後按一下節點。  
  
     在 64 位元系統上使用**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**  
  
3.  加入名為 CustomDirectiveProcessor 的新機碼。  
  
    > [!NOTE]
    >  這是將會在自訂指示詞的 [處理器] 欄位中使用的名稱。 這個名稱不需要與指示詞名稱、指示詞處理器類別名稱或指示詞處理器命名空間相符。  
  
4.  加入名為 Class 的新字串值，其值 CustomDP.CustomDirectiveProcessor 為新字串名稱的值。  
  
5.  加入名為 CodeBase 的新字串值，其值等於您稍早在本逐步解說中建立之 CustomDP.dll 的路徑。  
  
     例如，路徑可能會看起來像`C:\UserFiles\CustomDP\bin\Debug\CustomDP.dll`。  
  
     您的登錄機碼應該含有下列值：  
  
    |名稱|類型|資料|  
    |----------|----------|----------|  
    |(預設值)|REG_SZ|(值未設定)|  
    |類別|REG_SZ|CustomDP.CustomDirectiveProcessor|  
    |程式碼基底|REG_SZ|**\<您的方案路徑 >**CustomDP\bin\Debug\CustomDP.dll|  
  
     如果組件已置於 GAC 中，則值看起來應該如下表所示：  
  
    |名稱|類型|資料|  
    |----------|----------|----------|  
    |(預設值)|REG_SZ|(值未設定)|  
    |類別|REG_SZ|CustomDP.CustomDirectiveProcessor|  
    |Assembly|REG_SZ|CustomDP.dll|  
  
6.  重新啟動 Visual Studio。  
  
## <a name="testing-the-directive-processor"></a>測試指示詞處理器  
 若要測試指示詞處理器，您必須撰寫呼叫該處理器的文字範本。  
  
 在本範例中，文字範本會呼叫指示詞，並傳入 XML 檔 (包含類別檔案的文件) 的名稱。
  
 文字範本接著使用指示詞建立的 <xref:System.Xml.XmlDocument> 屬性，巡覽 XML 並印出文件註解。  
  
#### <a name="to-create-an-xml-file-for-use-in-testing-the-directive-processor"></a>若要建立可用於測試指示詞處理器的 XML 檔  
  
1.  建立名為文字檔`DocFile.xml`使用任何文字編輯器 （例如 「 記事本 」）。  
  
    > [!NOTE]
    >  您可以在任何位置建立這個檔案 (例如 C:\Test\DocFile.xml)。  
  
2.  將下列程式碼加入至此文字檔中：  
  
    ```  
    <?xml version="1.0"?>  
    <doc>  
        <assembly>  
            <name>xmlsample</name>  
        </assembly>  
        <members>  
            <member name="T:SomeClass">  
                <summary>Class level summary documentation goes here.</summary>  
                <remarks>Longer comments can be associated with a type or member through the remarks tag</remarks>  
            </member>  
            <member name="F:SomeClass.m_Name">  
                <summary>Store for the name property</summary>  
            </member>   
            <member name="M:SomeClass.#ctor">  
                <summary>The class constructor.</summary>   
            </member>  
            <member name="M:SomeClass.SomeMethod(System.String)">  
                <summary>Description for SomeMethod.</summary>  
                <param name="s">Parameter description for s goes here</param>  
                <seealso cref="T:System.String">You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.</seealso>  
            </member>  
            <member name="M:SomeClass.SomeOtherMethod">  
                <summary>Some other method.</summary>  
                <returns>Return results are described through the returns tag.</returns>  
                <seealso cref="M:SomeClass.SomeMethod(System.String)">Notice the use of the cref attribute to reference a specific method</seealso>  
            </member>  
            <member name="M:SomeClass.Main(System.String[])">  
                <summary>The entry point for the application.</summary>  
                <param name="args">A list of command line arguments</param>  
            </member>  
            <member name="P:SomeClass.Name">  
                <summary>Name property</summary>  
                <value>A value tag is used to describe the property value</value>  
            </member>  
        </members>  
    </doc>  
    ```  
  
3.  儲存並關閉檔案。  
  
#### <a name="to-create-a-text-template-to-test-the-directive-processor"></a>若要建立文字範本以測試指示詞處理器  
  
1.  在 Visual Studio 中建立 C# 或 Visual Basic 類別庫專案，並命名為 TemplateTest。  
  
2.  新增名為 TestDP.tt 的文字範本檔。  
  
3.  請確定**自訂工具**TestDP.tt 的屬性設定為`TextTemplatingFileGenerator`。  
  
4.  將 TestDP.tt 的內容變更為下列文字。  
  
    > [!NOTE]
    >  請務必取代字串 <`YOUR PATH>` DocFile.xml 檔案的路徑。  
  
     文字範本的語言與指示詞處理器的語言不一定要相符。  
  
    ```csharp  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" #>  
    <#@ output extension=".txt" #>  
  
    <#  //This will call the custom directive processor. #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  //Uncomment this line if you want to see the generated transformation class. #>  
    <#  //System.Diagnostics.Debugger.Break(); #>  
  
    <#  //This will use the results of the directive processor. #>  
    <#  //The directive processor has read the XML and stored it in Document0. #>  
    <#  
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");  
  
        foreach (XmlNode member in node.ChildNodes)  
        {  
            XmlNode name = member.Attributes.GetNamedItem("name");  
            WriteLine("{0,7}:  {1}", "Name", name.Value);  
  
            foreach (XmlNode comment in member.ChildNodes)  
            {  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);  
            }  
            WriteLine("");  
        }  
    #>  
  
    <#  //You can call the directive processor again and pass it a different file. #>  
    <# //@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\<Your Second File>" #>  
  
    <#  //To use the results of the second directive call, use Document1. #>  
    <#  
        //XmlNode node2 = Document1.DocumentElement.SelectSingleNode("members");  
  
        //...  
    #>  
    ```  
  
    ```vb  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" language="vb" #>  
    <#@ output extension=".txt" #>  
  
    <#  'This will call the custom directive processor. #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  'Uncomment this line if you want to see the generated transformation class. #>  
    <#  'System.Diagnostics.Debugger.Break() #>  
  
    <#  'This will use the results of the directive processor. #>  
    <#  'The directive processor has read the XML and stored it in Document0. #>  
    <#  
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")  
  
        Dim member As XmlNode  
        For Each member In node.ChildNodes  
  
            Dim name As XmlNode = member.Attributes.GetNamedItem("name")  
            WriteLine("{0,7}:  {1}", "Name", name.Value)  
  
            Dim comment As XmlNode  
            For Each comment In member.ChildNodes  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)  
            Next  
  
            WriteLine("")  
        Next  
    #>  
  
    <#  'You can call the directive processor again and pass it a different file. #>  
    <# '@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFileTwo.xml" #>  
  
    <#  'To use the results of the second directive call, use Document1. #>  
    <#  
        'node = Document1.DocumentElement.SelectSingleNode("members")  
  
        '...  
    #>  
    ```  
  
    > [!NOTE]
    >  在這個範本中，`Processor` 參數的值為 `CustomDirectiveProcessor`。 `Processor` 參數的值必須與處理器之登錄機碼的名稱相符。  
  
5.  在**檔案**功能表上，按一下 **全部儲存**。  
  
#### <a name="to-test-the-directive-processor"></a>若要測試指示詞處理器  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下 TestDP.tt，然後按一下**執行自訂工具**。  
  
     如[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]使用者 TestDP.txt 可能不會出現在**方案總管 中**預設。 若要顯示指派給專案的所有檔案，請開啟**專案**功能表，然後按一下**顯示所有檔案**。  
  
2.  在**方案總管 中**，展開 TestDP.txt 節點，然後按兩下 TestDP.txt，在編輯器中開啟它。  
  
     產生的文字輸出隨即出現。 輸出看起來應該如下所示：  
  
    ```  
       Name:  T:SomeClass  
    summary:  Class level summary documentation goes here.  
    remarks:  Longer comments can be associated with a type or member through the remarks tag  
  
       Name:  F:SomeClass.m_Name  
    summary:  Store for the name property  
  
       Name:  M:SomeClass.#ctor  
    summary:  The class constructor.  
  
       Name:  M:SomeClass.SomeMethod(System.String)  
    summary:  Description for SomeMethod.  
      param:  Parameter description for s goes here  
    seealso:  You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.  
  
       Name:  M:SomeClass.SomeOtherMethod  
    summary:  Some other method.  
    returns:  Return results are described through the returns tag.  
    seealso:  Notice the use of the cref attribute to reference a specific method  
  
       Name:  M:SomeClass.Main(System.String[])  
    summary:  The entry point for the application.  
      param:  A list of command line arguments  
  
       Name:  P:SomeClass.Name  
    summary:  Name property  
      value:  A value tag is used to describe the property value  
    ```  
  
## <a name="adding-html-to-generated-text"></a>將 HTML 加入至產生的文字  
 在測試自訂指示詞處理器之後，您可能會想要將一些 HTML 加入至產生的文字。  
  
#### <a name="to-add-html-to-the-generated-text"></a>若要 HTML 將加入至產生的文字  
  
1.  以下列內容取代 TestDP.tt 中的程式碼。 HTML 會反白顯示。 請務必取代字串`YOUR PATH`DocFile.xml 檔案的路徑。  
  
    > [!NOTE]
    >  其他的開頭\<# 和結尾 #> 標記陳述式程式碼與 HTML 標記隔開。  
  
    ```csharp  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" #>  
    <#@ output extension=".htm" #>  
  
    <#  //this will call the custom directive processor #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  //uncomment this line if you want to see the generated transformation class #>  
    <#  //System.Diagnostics.Debugger.Break(); #>  
  
    <html><body>  
  
    <#  //this will use the results of the directive processor #>  
    <#  //the directive processor has read the XML and stored it in Document0#>  
    <#  
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");  
  
        foreach (XmlNode member in node.ChildNodes)  
        {  
    #>  
    <h3>  
    <#      
            XmlNode name = member.Attributes.GetNamedItem("name");  
            WriteLine("{0,7}:  {1}", "Name", name.Value);  
    #>  
    </h3>  
    <#  
            foreach (XmlNode comment in member.ChildNodes)  
            {  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);  
    #>  
    <br/>  
    <#  
            }  
        }  
    #>  
    </body></html>  
    ```  
  
    ```vb  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" language="vb" #>  
    <#@ output extension=".htm" #>  
  
    <#  'this will call the custom directive processor #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  'uncomment this line if you want to see the generated transformation class #>  
    <#  'System.Diagnostics.Debugger.Break() #>  
  
    <html><body>  
  
    <#  'this will use the results of the directive processor #>  
    <#  'the directive processor has read the XML and stored it in Document0#>  
    <#  
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")  
  
        Dim member As XmlNode  
        For Each member In node.ChildNodes  
    #>  
    <h3>  
    <#      
            Dim name As XmlNode = member.Attributes.GetNamedItem("name")  
            WriteLine("{0,7}:  {1}", "Name", name.Value)  
    #>  
    </h3>  
    <#  
            Dim comment As XmlNode  
            For Each comment In member.ChildNodes  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)  
    #>  
    <br/>  
    <#  
            Next  
        Next  
    #>  
    </body></html>  
    ```  
  
2.  在**檔案**功能表上，按一下 **儲存 TestDP.txt**。  
  
3.  若要檢視的瀏覽器中，輸出中**方案總管 中**，以滑鼠右鍵按一下 TestDP.htm，然後按一下**瀏覽器中檢視**。  
  
     您的輸出除了已套用 HTML 格式之外，應該與原本的文字相同。 每個項目名稱應該顯示為粗體。
