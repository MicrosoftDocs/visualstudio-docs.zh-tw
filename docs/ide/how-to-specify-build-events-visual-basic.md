---
title: "如何：指定建置事件 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
caps.latest.revision: 26
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 595995a0369ff74c4223e7a585c913bc90aca411
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-specify-build-events-visual-basic"></a>如何：指定建置事件 (Visual Basic)
在 Visual Basic 中的建置事件可以用來執行指令碼、巨集或編譯處理程序當中的其他動作。 編譯之前發生的是建置前事件；編譯之後發生的則是建置後事件。  
  
 您可在 建置事件 對話方塊 (位於 專案設計工具} 的 編譯 頁面) 中，指定建置事件。  
  
> [!NOTE]
>  Visual Basic Express 不支援建置事件的項目。 只有完整版 Visual Studio 產品才支援此項目。  
  
## <a name="how-to-specify-pre-build-and-post-build-events"></a>如何指定建置前和建置後事件  
  
#### <a name="to-specify-a-build-event"></a>若要指定建置事件  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [編譯] 索引標籤。  
  
3.  按一下 [建置事件] 按鈕，開啟 [建置事件] 對話方塊。  
  
4.  輸入建置前或建置後動作的命令列引數，然後按一下 [確定]。  
  
    > [!NOTE]
    >  在執行 .bat 檔案的所有建置命令前方，加入 `call` 陳述式。 例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。  
  
    > [!NOTE]
    >  如果您的建置前或建置後事件未順利完成，您可以將代碼不為零 (0) 的事件動作結束 (若為 0 表示動作成功)，以終止建置。  
  
## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>範例：如何使用建置後事件變更資訊清單  
 下列程序示範如何使用從建置後事件呼叫的 .exe 命令 (專案目錄中的 .exe.manifest 檔案)，設定應用程式資訊清單中的最低作業系統版本。 最低作業系統版本是由四組號碼來表示，例如 4.10.0.0。 若要進行上述作業，請使用命令來變更資訊清單的 `<dependentOS>` 區段：  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>建立 .exe 命令以變更應用程式資訊清單  
  
1.  建立命令的主控台應用程式。 從 [檔案] 功能表中，依序按一下 [新增] 和 [專案]。  
  
2.  在 [新增專案] 對話方塊的 [Visual Basic] 節點中，依序選取 [Windows] 和 [主控台應用程式] 範本。 將專案命名為 `ChangeOSVersionVB`。  
  
3.  在 Module1.vb 中，將下面這行加入檔案最上方的另一個 `Imports` 陳述式：  
  
    ```  
    Imports System.Xml  
    ```  
  
4.  將下列程式碼加入 `Sub Main`：  
  
    ```  
    Sub Main()  
       Dim applicationManifestPath As String  
       applicationManifestPath = My.Application.CommandLineArgs(0)  
       Console.WriteLine("Application Manifest Path: " & applicationManifestPath.ToString)  
  
       'Get version name  
       Dim osVersion As Version  
       If My.Application.CommandLineArgs.Count >= 2 Then  
          osVersion = New Version(My.Application.CommandLineArgs(1).ToString)  
       Else  
          Throw New ArgumentException("OS Version not specified.")  
       End If  
       Console.WriteLine("Desired OS Version: " & osVersion.ToString())  
  
       Dim document As XmlDocument  
       Dim namespaceManager As XmlNamespaceManager  
       namespaceManager = New XmlNamespaceManager(New NameTable())  
       With namespaceManager  
          .AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1")  
          .AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2")  
       End With  
  
       document = New XmlDocument()  
       document.Load(applicationManifestPath)  
  
       Dim baseXPath As String  
       baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os"  
  
       'Change minimum required OS Version.  
       Dim node As XmlNode  
       node = document.SelectSingleNode(baseXPath, namespaceManager)  
       node.Attributes("majorVersion").Value = osVersion.Major.ToString()  
       node.Attributes("minorVersion").Value = osVersion.Minor.ToString()  
       node.Attributes("buildNumber").Value = osVersion.Build.ToString()  
       node.Attributes("servicePackMajor").Value = osVersion.Revision.ToString()  
  
       document.Save(applicationManifestPath)  
    End Sub  
    ```  
  
     此命令會採用兩個引數。 第一個引數是應用程式資訊清單的路徑 (也就是建置程序建立資訊清單的資料夾，通常為 Projectname.publish)。 第二個引數是新的作業系統版本。  
  
5.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
6.  將 .exe 檔案 (例如 `C:\TEMP\ChangeOSVersionVB.exe`) 複製到目錄。  
  
 接下來，在建置後事件中叫用此命令，以變更應用程式資訊清單。  
  
#### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>叫用建置後事件，以變更應用程式資訊清單  
  
1.  針對要發行的專案，建立 Windows 應用程式。 從 [檔案] 功能表中，依序按一下 [新增] 和 [專案]。  
  
2.  在 [新增專案] 對話方塊的 [Visual Basic] 節點中，依序選取 [Windows] 和 [Windows 應用程式] 範本。 將專案命名為 `VBWinApp`。  
  
3.  選取方案總管中的專案，然後按一下 [專案] 功能表中的 [屬性]。  
  
4.  在 [專案設計工具] 中，移至 [發行] 頁面，然後將 [發行位置] 設為 `C:\TEMP\`。  
  
5.  按一下 [Publish Now]\(立即發行)，即可發行專案。  
  
     隨即建立資訊清單檔並將其放入`C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest`。 若要檢視資訊清單，請以滑鼠右鍵按一下檔案，然後依序按一下 [開啟方式]、[從清單中選取程式] 以及 [記事本]。  
  
     在檔案中搜尋 `<osVersionInfo>` 項目。 例如，版本可能是：  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  在 [專案設計工具] 中，移至 [編譯] 索引標籤，並按一下 [建置事件] 按鈕以開啟 [建置事件] 對話方塊。  
  
7.  在 [建置後事件命令列] 文字方塊中，輸入下列命令：  
  
     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     當您建置專案時，此命令會將應用程式資訊清單中的最低作業系統版本變更為 5.1.2600.0。  
  
     `$(TargetPath)` 巨集表示要建立之可執行檔的完整路徑。 因此， $(TargetPath).manifest 會指定在 bin 目錄中建立應用程式資訊清單。 發行時，系統會將這份資訊清單複製到您先前設定的發行位置中。  
  
8.  再次發行專案。 移至 [發行] 頁面，然後按一下 [Publish Now]\(立即發行)。  
  
     再次檢視資訊清單。 若要檢視資訊清單，請移至發行目錄，以滑鼠右鍵按一下檔案，然後依序按一下 [開啟方式]、[從清單中選取程式] 以及 [記事本]。  
  
     現在，版本應讀為：  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [管理編譯屬性](http://msdn.microsoft.com/en-us/94308881-f10f-4caf-a729-f1028e596a2c)   
 [專案設計工具、編譯頁 (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)   
 [專案設計工具、發行頁](../ide/reference/publish-page-project-designer.md)   
 [建置前事件/建置後事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [如何：指定建置事件 (C#)](../ide/how-to-specify-build-events-csharp.md)
