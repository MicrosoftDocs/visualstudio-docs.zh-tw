---
title: "逐步解說：建立自訂文字範本主機 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文字範本, 自訂主機逐步解說"
  - "逐步解說 [文字範本], 自訂主機"
ms.assetid: d00bc366-65ed-4229-885a-196ef9625f05
caps.latest.revision: 51
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 51
---
# 逐步解說：建立自訂文字範本主機
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

「*文字範本**主應用程式*」\(Text Template Host\) 會提供可供執行「*文字範本轉換引擎*」\(Text Template Transformation Engine\) 的環境。  這個主應用程式負責管理引擎與檔案系統之間的互動。  需要檔案或組件的引擎或「*指示詞處理器*」\(Directive Processor\) 可以向主應用程式要求資源。  主機便會搜尋目錄和全域組件快取來找出要求的資源。  如需詳細資訊，請參閱[文字範本轉換流程](../modeling/the-text-template-transformation-process.md)。  
  
 如果您要從外部 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 使用「*文字範本轉換*」，或是想要將這個功能整合到自訂工具，您可以撰寫自訂主機。  若要建立自訂主機，您必須建立一個繼承自 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> 的類別。  如需個別方法的說明文件，請參閱 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>。  
  
> [!WARNING]
>  如果您要撰寫 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 擴充功能或封裝，請考慮使用文字範本化服務，而不是建立自己的主應用程式。  如需詳細資訊，請參閱[叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。  
  
 本逐步解說所述的工作包括下列各項：  
  
-   建立自訂文字範本主應用程式。  
  
-   測試自訂主應用程式。  
  
## 必要條件  
 若要完成這個逐步解說，您必須具有下列各項：  
  
-   Visual Studio 2010 \(含\) 以後版本  
  
-   Visual Studio SDK  
  
## 建立自訂文字範本主應用程式  
 在本逐步解說中，您將會在可從命令列呼叫執行的應用程式 \(Application\) 中建立自訂主應用程式 \(Custom Host\)。  此應用程式會接受文字範本檔做為引數、讀取範本、呼叫引擎以轉換範本，然後在命令提示字元視窗中顯示發生的任何錯誤。  
  
#### 若要建立自訂主應用程式  
  
1.  在 Visual Studio 中建立新的 Visual Basic 或 C\# 主控台應用程式，並命名為 CustomHost。  
  
2.  加入下列組件的參考：  
  
    -   **Microsoft.VisualStudio.TextTemplating.\*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.Interfaces.10.0 \(含\) 以後版本**  
  
3.  以下列程式碼取代 Program.cs 或 Module1.vb 檔案中的程式碼：  
  
    ```c#  
    using System;  
    using System.IO;  
    using System.CodeDom.Compiler;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.TextTemplating;  
  
    namespace CustomHost  
    {  
        //The text template transformation engine is responsible for running   
        //the transformation process.  
        //The host is responsible for all input and output, locating files,   
        //and anything else related to the external environment.  
        //-------------------------------------------------------------------------  
        class CustomCmdLineHost : ITextTemplatingEngineHost  
        {  
            //the path and file name of the text template that is being processed  
            //---------------------------------------------------------------------  
            internal string TemplateFileValue;  
            public string TemplateFile  
            {  
                get { return TemplateFileValue; }  
            }  
            //This will be the extension of the generated text output file.  
            //The host can provide a default by setting the value of the field here.  
            //The engine can change this value based on the optional output directive  
            //if the user specifies it in the text template.  
            //---------------------------------------------------------------------  
            private string fileExtensionValue = ".txt";  
            public string FileExtension  
            {  
                get { return fileExtensionValue; }  
            }  
            //This will be the encoding of the generated text output file.  
            //The host can provide a default by setting the value of the field here.  
            //The engine can change this value based on the optional output directive  
            //if the user specifies it in the text template.  
            //---------------------------------------------------------------------  
            private Encoding fileEncodingValue = Encoding.UTF8;  
            public Encoding FileEncoding  
            {  
                get { return fileEncodingValue; }  
            }  
            //These are the errors that occur when the engine processes a template.  
            //The engine passes the errors to the host when it is done processing,  
            //and the host can decide how to display them. For example, the host   
            //can display the errors in the UI or write them to a file.  
            //---------------------------------------------------------------------  
            private CompilerErrorCollection errorsValue;  
            public CompilerErrorCollection Errors  
            {  
                get { return errorsValue; }  
            }  
            //The host can provide standard assembly references.  
            //The engine will use these references when compiling and  
            //executing the generated transformation class.  
            //--------------------------------------------------------------  
            public IList<string> StandardAssemblyReferences  
            {  
                get  
                {  
                    return new string[]  
                    {  
                        //If this host searches standard paths and the GAC,  
                        //we can specify the assembly name like this.  
                        //---------------------------------------------------------  
                        //"System"  
  
                        //Because this host only resolves assemblies from the   
                        //fully qualified path and name of the assembly,  
                        //this is a quick way to get the code to give us the  
                        //fully qualified path and name of the System assembly.  
                        //---------------------------------------------------------  
                        typeof(System.Uri).Assembly.Location  
                    };  
                }  
            }  
            //The host can provide standard imports or using statements.  
            //The engine will add these statements to the generated   
            //transformation class.  
            //--------------------------------------------------------------  
            public IList<string> StandardImports  
            {  
                get  
                {  
                    return new string[]  
                    {  
                        "System"  
                    };  
                }  
            }  
            //The engine calls this method based on the optional include directive  
            //if the user has specified it in the text template.  
            //This method can be called 0, 1, or more times.  
            //---------------------------------------------------------------------  
            //The included text is returned in the context parameter.  
            //If the host searches the registry for the location of include files,  
            //or if the host searches multiple locations by default, the host can  
            //return the final path of the include file in the location parameter.  
            //---------------------------------------------------------------------  
            public bool LoadIncludeText(string requestFileName, out string content, out string location)  
            {  
                content = System.String.Empty;  
                location = System.String.Empty;  
  
                //If the argument is the fully qualified path of an existing file,  
                //then we are done.  
                //----------------------------------------------------------------  
                if (File.Exists(requestFileName))  
                {  
                    content = File.ReadAllText(requestFileName);  
                    return true;  
                }  
                //This can be customized to search specific paths for the file.  
                //This can be customized to accept paths to search as command line  
                //arguments.  
                //----------------------------------------------------------------  
                else  
                {  
                    return false;  
                }  
            }  
            //Called by the Engine to enquire about   
            //the processing options you require.   
            //If you recognize that option, return an   
            //appropriate value.   
            //Otherwise, pass back NULL.  
            //--------------------------------------------------------------------  
            public object GetHostOption(string optionName)  
            {  
            object returnObject;  
            switch (optionName)  
            {  
            case "CacheAssemblies":  
                        returnObject = true;  
         break;  
            default:  
            returnObject = null;  
            break;  
            }  
            return returnObject;  
            }  
            //The engine calls this method to resolve assembly references used in  
            //the generated transformation class project and for the optional   
            //assembly directive if the user has specified it in the text template.  
            //This method can be called 0, 1, or more times.  
            //---------------------------------------------------------------------  
            public string ResolveAssemblyReference(string assemblyReference)  
            {  
                //If the argument is the fully qualified path of an existing file,  
                //then we are done. (This does not do any work.)  
                //----------------------------------------------------------------  
                if (File.Exists(assemblyReference))  
                {  
                    return assemblyReference;  
                }  
                //Maybe the assembly is in the same folder as the text template that   
                //called the directive.  
                //----------------------------------------------------------------  
                string candidate = Path.Combine(Path.GetDirectoryName(this.TemplateFile), assemblyReference);  
                if (File.Exists(candidate))  
                {  
                    return candidate;  
                }  
                //This can be customized to search specific paths for the file  
                //or to search the GAC.  
                //----------------------------------------------------------------  
                //This can be customized to accept paths to search as command line  
                //arguments.  
                //----------------------------------------------------------------  
                //If we cannot do better, return the original file name.  
                return "";  
            }  
            //The engine calls this method based on the directives the user has   
            //specified in the text template.  
            //This method can be called 0, 1, or more times.  
            //---------------------------------------------------------------------  
            public Type ResolveDirectiveProcessor(string processorName)  
            {  
                //This host will not resolve any specific processors.  
                //Check the processor name, and if it is the name of a processor the   
                //host wants to support, return the type of the processor.  
                //---------------------------------------------------------------------  
                if (string.Compare(processorName, "XYZ", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    //return typeof();  
                }  
                //This can be customized to search specific paths for the file  
                //or to search the GAC  
                //If the directive processor cannot be found, throw an error.  
                throw new Exception("Directive Processor not found");  
            }  
            //A directive processor can call this method if a file name does not   
            //have a path.  
            //The host can attempt to provide path information by searching   
            //specific paths for the file and returning the file and path if found.  
            //This method can be called 0, 1, or more times.  
            //---------------------------------------------------------------------  
            public string ResolvePath(string fileName)  
            {  
                if (fileName == null)  
                {  
                    throw new ArgumentNullException("the file name cannot be null");  
                }  
                //If the argument is the fully qualified path of an existing file,  
                //then we are done  
                //----------------------------------------------------------------  
                if (File.Exists(fileName))  
                {  
                    return fileName;  
                }  
                //Maybe the file is in the same folder as the text template that   
                //called the directive.  
                //----------------------------------------------------------------  
                string candidate = Path.Combine(Path.GetDirectoryName(this.TemplateFile), fileName);  
                if (File.Exists(candidate))  
                {  
                    return candidate;  
                }  
                //Look more places.  
                //----------------------------------------------------------------  
                //More code can go here...  
                //If we cannot do better, return the original file name.  
                return fileName;  
            }  
            //If a call to a directive in a text template does not provide a value  
            //for a required parameter, the directive processor can try to get it  
            //from the host by calling this method.  
            //This method can be called 0, 1, or more times.  
            //---------------------------------------------------------------------  
            public string ResolveParameterValue(string directiveId, string processorName, string parameterName)  
            {  
                if (directiveId == null)  
                {  
                    throw new ArgumentNullException("the directiveId cannot be null");  
                }  
                if (processorName == null)  
                {  
                    throw new ArgumentNullException("the processorName cannot be null");  
                }  
                if (parameterName == null)  
                {  
                    throw new ArgumentNullException("the parameterName cannot be null");  
                }  
                //Code to provide "hard-coded" parameter values goes here.  
                //This code depends on the directive processors this host will interact with.  
                //If we cannot do better, return the empty string.  
                return String.Empty;  
            }  
            //The engine calls this method to change the extension of the   
            //generated text output file based on the optional output directive   
            //if the user specifies it in the text template.  
            //---------------------------------------------------------------------  
            public void SetFileExtension(string extension)  
            {  
                //The parameter extension has a '.' in front of it already.  
                //--------------------------------------------------------  
                fileExtensionValue = extension;  
            }  
            //The engine calls this method to change the encoding of the   
            //generated text output file based on the optional output directive   
            //if the user specifies it in the text template.  
            //----------------------------------------------------------------------  
            public void SetOutputEncoding(System.Text.Encoding encoding, bool fromOutputDirective)  
            {  
                fileEncodingValue = encoding;  
            }  
            //The engine calls this method when it is done processing a text  
            //template to pass any errors that occurred to the host.  
            //The host can decide how to display them.  
            //---------------------------------------------------------------------  
            public void LogErrors(CompilerErrorCollection errors)  
            {  
                errorsValue = errors;  
            }  
            //This is the application domain that is used to compile and run  
            //the generated transformation class to create the generated text output.  
            //----------------------------------------------------------------------  
            public AppDomain ProvideTemplatingAppDomain(string content)  
            {  
                //This host will provide a new application domain each time the   
                //engine processes a text template.  
                //-------------------------------------------------------------  
                return AppDomain.CreateDomain("Generation App Domain");  
                //This could be changed to return the current appdomain, but new   
                //assemblies are loaded into this AppDomain on a regular basis.  
                //If the AppDomain lasts too long, it will grow indefintely,   
                //which might be regarded as a leak.  
                //This could be customized to cache the application domain for   
                //a certain number of text template generations (for example, 10).  
                //This could be customized based on the contents of the text   
                //template, which are provided as a parameter for that purpose.  
            }  
        }  
        //This will accept the path of a text template as an argument.  
        //It will create an instance of the custom host and an instance of the  
        //text templating transformation engine, and will transform the  
        //template to create the generated text output file.  
        //-------------------------------------------------------------------------  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                try  
                {  
                    ProcessTemplate(args);  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex.Message);  
                }  
            }  
            static void ProcessTemplate(string[] args)  
            {  
                string templateFileName = null;  
                if (args.Length == 0)  
                {  
                    throw new System.Exception("you must provide a text template file path");  
                }  
                templateFileName = args[0];  
                if (templateFileName == null)  
                {  
                    throw new ArgumentNullException("the file name cannot be null");  
                }  
                if (!File.Exists(templateFileName))  
                {  
                    throw new FileNotFoundException("the file cannot be found");  
                }  
                CustomCmdLineHost host = new CustomCmdLineHost();  
                Engine engine = new Engine();  
                host.TemplateFileValue = templateFileName;  
                //Read the text template.  
                string input = File.ReadAllText(templateFileName);  
                //Transform the text template.  
                string output = engine.ProcessTemplate(input, host);  
                string outputFileName = Path.GetFileNameWithoutExtension(templateFileName);  
                outputFileName = Path.Combine(Path.GetDirectoryName(templateFileName), outputFileName);  
                outputFileName = outputFileName + "1" + host.FileExtension;  
                File.WriteAllText(outputFileName, output, host.FileEncoding);  
  
                foreach (CompilerError error in host.Errors)  
                {  
                    Console.WriteLine(error.ToString());  
                }  
            }  
        }  
    }  
    ```  
  
    ```vb#  
    Imports System  
    Imports System.IO  
    Imports System.CodeDom.Compiler  
    Imports System.Collections.Generic  
    Imports System.Text  
    Imports Microsoft.VisualStudio.TextTemplating  
  
    Namespace CustomHost  
        'The text template transformation engine is responsible for running   
        'the transformation process.  
        'The host is responsible for all input and output, locating files,   
        'and anything else related to the external environment.  
        '-------------------------------------------------------------------------  
        Public Class CustomCmdLineHost  
            Implements ITextTemplatingEngineHost  
  
            'the path and file name of the text template that is being processed  
            '---------------------------------------------------------------------  
            Friend TemplateFileValue As String  
            Public ReadOnly Property TemplateFile() As String Implements ITextTemplatingEngineHost.TemplateFile  
                Get  
                    Return TemplateFileValue  
                End Get  
            End Property  
            'This will be the extension of the generated text output file.  
            'The host can provide a default by setting the value of the field here.  
            'The engine can change this based on the optional output directive  
            'if the user specifies it in the text template.  
            '---------------------------------------------------------------------  
            Private fileExtensionValue As String = ".txt"  
            Public ReadOnly Property FileExtension() As String  
                Get  
                    Return fileExtensionValue  
                End Get  
            End Property  
            'This will be the encoding of the generated text output file.  
            'The host can provide a default by setting the value of the field here.  
            'The engine can change this value based on the optional output directive  
            'if the user specifies it in the text template.  
            '---------------------------------------------------------------------  
            Private fileEncodingValue As Encoding = Encoding.UTF8  
            Public ReadOnly Property fileEncoding() As Encoding  
                Get  
                    Return fileEncodingValue  
                End Get  
            End Property  
            'These are the errors that occur when the engine processes a template.  
            'The engine passes the errors to the host when it is done processing,  
            'and the host can decide how to display them. For example, the host   
            'can display the errors in the UI or write them to a file.  
            '---------------------------------------------------------------------  
            Private errorsValue As CompilerErrorCollection  
            Public ReadOnly Property Errors() As CompilerErrorCollection  
                Get  
                    Return errorsValue  
                End Get  
            End Property  
            'The host can provide standard assembly references.  
            'The engine will use these references when compiling and  
            'executing the generated transformation class.  
            '--------------------------------------------------------------  
            Public ReadOnly Property StandardAssemblyReferences() As IList(Of String) Implements ITextTemplatingEngineHost.StandardAssemblyReferences  
                Get  
                    'If this host searches standard paths and the GAC,  
                    'we can specify the assembly name like this.  
                    '---------------------------------------------------------  
                    'Return New String() {"System"}  
                    'Because this host only resolves assemblies from the   
                    'fully qualified path and name of the assembly,  
                    'this is a quick way to get the code to give us the  
                    'fully qualified path and name of the System assembly.  
                    '---------------------------------------------------------  
                    Return New String() {(New System.UriBuilder()).GetType().Assembly.Location}  
                End Get  
            End Property  
            'The host can provide standard imports or imports statements.  
            'The engine will add these statements to the generated   
            'transformation class.  
            '--------------------------------------------------------------  
            Public ReadOnly Property StandardImports() As IList(Of String) Implements ITextTemplatingEngineHost.StandardImports  
                Get  
                    Return New String() {"System"}  
                End Get  
            End Property  
            ' Called by the Engine to enquire about   
            ' the processing options you require.   
            ' If you recognize that option, return an   
            ' appropriate value.   
            ' Otherwise, pass back NULL.  
            '--------------------------------------------------------------------  
            Public Function GetHostOption(ByVal optionName As String) As Object Implements ITextTemplatingEngineHost.GetHostOption  
                Dim returnObject As Object  
                Select Case optionName  
                    Case "CacheAssemblies"  
                        returnObject = True  
                    Case Else  
                        returnObject = False  
                End Select  
                Return returnObject  
            End Function  
            'The engine calls this method based on the optional include directive  
            'if the user has specified it in the text template.  
            'This method can be called 0, 1, or more times.  
            '---------------------------------------------------------------------  
            'The included text is returned in the context parameter.  
            'If the host searches the registry for the location of include files  
            'or if the host searches multiple locations by default, the host can  
            'return the final path of the include file in the location parameter.  
            '---------------------------------------------------------------------  
            Public Function LoadIncludeText(ByVal requestFileName As String, ByRef content As String, ByRef location As String) As Boolean Implements ITextTemplatingEngineHost.LoadIncludeText  
                content = System.String.Empty  
                location = System.String.Empty  
                'If the argument is the fully qualified path of an existing file,  
                'then we are done.  
                '----------------------------------------------------------------  
                If File.Exists(requestFileName) Then  
                    content = File.ReadAllText(requestFileName)  
                    Return True  
                'This can be customized to search specific paths for the file.  
                'This can be customized to accept paths to search as command line  
                'arguments.  
                '----------------------------------------------------------------  
                Else  
                    Return False  
                End If  
            End Function  
            'The engine calls this method to resolve assembly references used in  
            'the generated transformation class project and for the optional   
            'assembly directive if the user has specified it in the text template.  
            'This method can be called 0, 1, or more times.  
            '---------------------------------------------------------------------  
            Public Function ResolveAssemblyReference(ByVal assemblyReference As String) As String Implements ITextTemplatingEngineHost.ResolveAssemblyReference  
                'If the argument is the fully qualified path of an existing file,  
                'then we are done. (This does not do any work.)  
                '----------------------------------------------------------------  
                If File.Exists(assemblyReference) Then  
                    Return assemblyReference  
                End If  
                'Maybe the assembly is in the same folder as the text template that   
                'called the directive.  
                '----------------------------------------------------------------  
                Dim candidate As String = Path.Combine(Path.GetDirectoryName(Me.TemplateFile), assemblyReference)  
                If File.Exists(candidate) Then  
                    Return candidate  
                End If  
                'This can be customized to search specific paths for the file,  
                'or to search the GAC.  
                '----------------------------------------------------------------  
                'This can be customized to accept paths to search as command line  
                'arguments.  
                '----------------------------------------------------------------  
                'If we cannot do better, return the original file name.  
                Return ""  
            End Function  
            'The engine calls this method based on the directives the user has   
            'specified in the text template.  
            'This method can be called 0, 1, or more times.  
            '---------------------------------------------------------------------  
            Public Function ResolveDirectiveProcessor(ByVal processorName As String) As System.Type Implements ITextTemplatingEngineHost.ResolveDirectiveProcessor  
                'This host will not resolve any specific processors.  
                'Check the processor name, and if it is the name of a processor the   
                'host wants to support, return the type of the processor.  
                '---------------------------------------------------------------------  
                If String.Compare(processorName, "XYZ", StringComparison.InvariantCultureIgnoreCase) = 0 Then  
                    'return typeof()  
                End If  
                'This can be customized to search specific paths for the file,  
                'or to search the GAC.  
                'If the directive processor cannot be found, throw an error.  
                Throw New Exception("Directive Processor not found")  
            End Function  
            'A directive processor can call this method if a file name does not   
            'have a path.  
            'The host can attempt to provide path information by searching   
            'specific paths for the file and returning the file and path if found.  
            'This method can be called 0, 1, or more times.  
            '---------------------------------------------------------------------  
            Public Function ResolvePath(ByVal fileName As String) As String Implements ITextTemplatingEngineHost.ResolvePath  
                If fileName Is Nothing Then  
                    Throw New ArgumentNullException("the file name cannot be null")  
                End If  
                'If the argument is the fully qualified path of an existing file,  
                'then we are done.  
                '----------------------------------------------------------------  
                If File.Exists(fileName) Then  
                    Return fileName  
                End If  
                'Maybe the file is in the same folder as the text template that   
                'called the directive.  
                '----------------------------------------------------------------  
                Dim candidate As String = Path.Combine(Path.GetDirectoryName(Me.TemplateFile), fileName)  
                If File.Exists(candidate) Then  
                    Return candidate  
                End If  
                'Look more places.  
                '----------------------------------------------------------------  
                'More code can go here...  
                'If we cannot do better, return the original file name  
                Return fileName  
            End Function  
            'If a call to a directive in a text template does not provide a value  
            'for a required parameter, the directive processor can try to get it  
            'from the host by calling this method.  
            'This method can be called 0, 1, or more times.  
            '---------------------------------------------------------------------  
            Public Function ResolveParameterValue(ByVal directiveId As String, ByVal processorName As String, ByVal parameterName As String) As String Implements ITextTemplatingEngineHost.ResolveParameterValue  
                If directiveId Is Nothing Then  
                    Throw New ArgumentNullException("the directiveId cannot be null")  
                End If  
                If processorName Is Nothing Then  
                    Throw New ArgumentNullException("the processorName cannot be null")  
                End If  
                If parameterName Is Nothing Then  
                    Throw New ArgumentNullException("the parameterName cannot be null")  
                End If  
                'Code to provide "hard-coded" parameter values goes here.  
                'This code depends on the directive processors this host will interact with.  
                'If we cannot do better, return the empty string.  
                Return String.Empty  
            End Function  
            'The engine calls this method to change the extension of the   
            'generated text output file based on the optional output directive   
            'if the user specifies it in the text template.  
            '---------------------------------------------------------------------  
            Public Sub SetFileExtension(ByVal extension As String) Implements ITextTemplatingEngineHost.SetFileExtension  
                'The parameter extension has a '.' in front of it already.  
                '--------------------------------------------------------  
                fileExtensionValue = extension  
            End Sub  
            'The engine calls this method to change the encoding of the   
            'generated text output file based on the optional output directive   
            'if the user specifies it in the text template.  
            '---------------------------------------------------------------------  
            Public Sub SetOutputEncoding(ByVal encoding As System.Text.Encoding, ByVal fromOutputDirective As Boolean) Implements ITextTemplatingEngineHost.SetOutputEncoding  
                fileEncodingValue = encoding  
            End Sub  
            'The engine calls this method when it is done processing a text  
            'template to pass any errors that occurred to the host.  
            'The host can decide how to display them.  
            '---------------------------------------------------------------------  
            Public Sub LogErrors(ByVal errors As System.CodeDom.Compiler.CompilerErrorCollection) Implements ITextTemplatingEngineHost.LogErrors  
                errorsValue = errors  
            End Sub  
            'This is the application domain that is used to compile and run  
            'the generated transformation class to create the generated text output.  
            '----------------------------------------------------------------------  
            Public Function ProvideTemplatingAppDomain(ByVal content As String) As System.AppDomain Implements ITextTemplatingEngineHost.ProvideTemplatingAppDomain  
                'This host will provide a new application domain each time the   
                'engine processes a text template.  
                '-------------------------------------------------------------  
                Return AppDomain.CreateDomain("Generation App Domain")  
                'This could be changed to return the current appdomain, but new   
                'assemblies are loaded into this AppDomain on a regular basis.  
                'If the AppDomain lasts too long, it will grow indefintely,   
                'which might be regarded as a leak.  
                'This could be customized to cache the application domain for   
                'a certain number of text template generations (for example, 10).  
                'This could be customized based on the contents of the text   
                'template, which are provided as a parameter for that purpose.  
            End Function  
        End Class 'CustomCmdLineHost  
        'This will accept the path of a text template as an argument.  
        'It will create an instance of the custom host and an instance of the  
        'text templating transformation engine. It will also transform the  
        'template to create the generated text output file.  
        '-------------------------------------------------------------------------  
        Class Program  
            Shared Sub Main(ByVal args As String())  
                Try  
                    ProcessTemplate(args)  
                Catch ex As Exception  
                    Console.WriteLine(ex.Message)  
                End Try  
            End Sub  
            Shared Sub ProcessTemplate(ByVal args As String())  
                Dim templateFileName As String = ""  
                If args.Length = 0 Then  
                    Throw New System.Exception("you must provide a text template file path")  
                End If  
                templateFileName = args(0)  
                If templateFileName Is Nothing Then  
                    Throw New ArgumentNullException("the file name cannot be null")  
                End If  
                If Not File.Exists(templateFileName) Then  
                    Throw New FileNotFoundException("the file cannot be found")  
                End If  
                Dim host As CustomCmdLineHost = New CustomCmdLineHost()  
                Dim engine As Engine = New Engine()  
                host.TemplateFileValue = templateFileName  
                'Read the text template.  
                Dim input As String = File.ReadAllText(templateFileName)  
                'Transform the text template.  
                Dim output As String = engine.ProcessTemplate(input, host)  
                Dim outputFileName As String = Path.GetFileNameWithoutExtension(templateFileName)  
                outputFileName = Path.Combine(Path.GetDirectoryName(templateFileName), outputFileName)  
                outputFileName = outputFileName & "1" & host.FileExtension  
                File.WriteAllText(outputFileName, output, host.fileEncoding)  
                Dim e As CompilerError  
                For Each e In host.Errors  
                    Console.WriteLine(e.ToString())  
                Next  
            End Sub 'ProcessTemplate  
        End Class 'Program  
    End Namespace  
    ```  
  
4.  \(僅限 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) 開啟 \[**專案**\] 功能表，然後按一下 \[**CustomHost 屬性**\]。  在 \[**啟始物件**\] 清單中，按一下 \[**CustomHost.Program**\]。  
  
5.  在 \[**檔案**\] 功能表上，按一下 \[**全部儲存**\]。  
  
6.  在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
## 測試自訂主應用程式  
 若要測試自訂主應用程式，請先撰寫文字範本，接著執行自訂主應用程式、將文字範本的名稱傳遞給這個主應用程式，然後確認已轉換該範本。  
  
#### 若要建立文字範本以測試自訂主應用程式  
  
1.  建立文字檔並命名為 `TestTemplate.tt`。  
  
     您可以使用任何文字編輯器 \(例如 \[記事本\]\) 來建立檔案。  
  
2.  將下列內容加入至檔案中：  
  
    > [!NOTE]
    >  文字範本的程式語言與自訂主應用程式的語言不一定要相符。  
  
    ```c#  
    Text Template Host Test  
  
    <#@ template debug="true" #>  
  
    <# //Uncomment this line to test that the host allows the engine to set the extension. #>  
    <# //@ output extension=".htm" #>  
  
    <# //Uncomment this line if you want to debug the generated transformation class. #>  
    <# //System.Diagnostics.Debugger.Break(); #>  
  
    <# for (int i=0; i<3; i++)  
       {  
           WriteLine("This is a test");  
       }   
    #>  
    ```  
  
    ```vb#  
    Text Template Host Test  
  
    <#@ template debug="true" language="VB"#>  
  
    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>  
    <# '@ output extension=".htm" #>  
  
    <# 'Uncomment this line if you want to debug the generated transformation class. #>  
    <# 'System.Diagnostics.Debugger.Break() #>  
  
    <# Dim i As Integer  
       For i = 0 To 2  
  
           WriteLine("This is a test")  
       Next  
    #>  
  
    ```  
  
3.  儲存並關閉檔案。  
  
#### 若要測試自訂主應用程式  
  
1.  開啟 \[命令提示字元\] 視窗。  
  
2.  輸入自訂主應用程式可執行檔的路徑，但是還不要按 ENTER。  
  
     例如，輸入：  
  
     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`  
  
    > [!NOTE]
    >  如果不要輸入位置路徑，您可以在 \[**Windows 檔案總管**\] 中瀏覽至 CustomHost.exe 檔，然後將該檔案拖曳到 \[命令提示字元\] 視窗中。  
  
3.  輸入空格。  
  
4.  輸入文字範本檔的路徑，然後按 ENTER。  
  
     例如，輸入：  
  
     `C:\<YOUR PATH>TestTemplate.tt`  
  
    > [!NOTE]
    >  如果不要輸入位置路徑，您可以在 \[**Windows 檔案總管**\] 中瀏覽至 TestTemplate.tt 檔，然後將該檔案拖曳到 \[命令提示字元\] 視窗中。  
  
     自訂主應用程式隨即執行並完成文字範本轉換流程。  
  
5.  在 \[**Windows 檔案總管**\] 中，瀏覽至包含檔案 TestTemplate.tt 的資料夾。  
  
     該資料夾也會包含 TestTemplate1.txt 檔。  
  
6.  開啟這個檔案來查看文字範本轉換的結果。  
  
     產生的文字輸出隨即出現，看起來如下所示：  
  
    ```  
    Text Template Host Test  
  
    This is a test  
    This is a test  
    This is a test  
    ```  
  
## 後續步驟  
 在本逐步解說中，您已經建立支援基本轉換功能的文字範本轉換主應用程式。  您可以擴充這個主應用程式，支援呼叫自訂或產生之指示詞處理器的文字範本。  如需詳細資訊，請參閱[逐步解說：將主機連接至產生的指示詞處理器](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>