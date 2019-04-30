---
title: HOW TO：指定建置事件 (C#) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f77a6b9b655cc7dfbf0639a81d7d350b904ce82a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435219"
---
# <a name="how-to-specify-build-events-c"></a>HOW TO：指定建置事件 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用建置事件指定要在建置開始之前，或建置完成之後執行的命令。 只有在建置成功到達建置流程中的這些點時，建置事件才會執行。  
  
 建置專案時，建置前事件會新增至名為 PreBuildEvent.bat 的檔案，而建置後事件會新增至名為 PostBuildEvent.bat 的檔案。 如果您想要確保錯誤檢查，請將您自己的錯誤檢查命令新增至建置步驟。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="how-to-specify-pre-build-and-post-build-events"></a>如何指定建置前和建置後事件  
  
#### <a name="to-specify-a-build-event"></a>若要指定建置事件  
  
1. 在 [方案總管] 中，選取您想要指定建置事件的專案。  
  
2. 在 [專案] 功能表上，按一下 [屬性]。  
  
3. 選取 [建置事件] 索引標籤。  
  
4. 在 [建置前事件命令列] 方塊中，指定建置事件的語法。  
  
    > [!NOTE]
    > 如果專案是最新狀態，而且未觸發任何建置，則建置前事件不會執行。  
  
5. 在 [建置後事件命令列] 方塊中，指定建置事件的語法。  
  
    > [!NOTE]
    > 在執行 .bat 檔案的所有建置命令前方，加入 `call` 陳述式。 例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。  
  
6. 在 [執行建置後事件] 方塊中，指定要執行建置後事件的情況。  
  
    > [!NOTE]
    > 若要新增冗長的語法，或從[建置前事件/建置後事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)選取任何建置巨集，請按一下省略符號按鈕 (**…**) 來顯示編輯方塊。  
  
     建置事件語法可以包含在命令提示字元或 .bat 檔案中的任何有效命令。 批次檔的名稱之前應該加上 `call` 以確保所有後續的命令都會執行。  
  
     **注意：** 如果您的建置前或建置後事件未順利完成，您可以結束代碼不為零 (0) 的事件動作 (若為 0 表示動作成功)，以終止建置。  
  
## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>範例：如何使用建置後事件變更資訊清單  
 下列程序示範如何使用從建置後事件呼叫的 .exe 命令 (專案目錄中的 .exe.manifest 檔案)，設定應用程式資訊清單中的最低作業系統版本。 最低作業系統版本是由四組號碼來表示，例如 4.10.0.0。 若要進行上述作業，請使用命令來變更資訊清單的 `<dependentOS>` 區段：  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>建立 .exe 命令以變更應用程式資訊清單  
  
1. 建立命令的主控台應用程式。 從 [檔案] 功能表，指向 [新增]，然後按一下 [專案]。  
  
2. 在 [新增專案] 對話方塊中，展開 [Visual C#]、依序按一下 [Windows] 和 [主控台應用程式] 範本。 將專案命名為 `ChangeOSVersionCS`。  
  
3. 在 Program.cs 中，將下面這行新增在檔案最上方的另一個 `using` 陳述式：  
  
   ```  
   using System.Xml;  
   ```  
  
4. 在 `ChangeOSVersionCS` 命名空間中，將 `Program` 類別實作取代為下列程式碼：  
  
   ```  
   class Program  
   {  
      /// <summary>  
      /// This function will set the minimum operating system version for a ClickOnce application.  
      /// </summary>  
      /// <param name="args">  
      /// Command Line Arguments:  
      /// 0 - Path to application manifest (.exe.manifest).  
      /// 1 - Version of OS  
      ///</param>  
      static void Main(string[] args)  
      {  
         string applicationManifestPath = args[0];  
         Console.WriteLine("Application Manifest Path: " + applicationManifestPath);  
  
         // Get version name.  
         Version osVersion = null;  
         if (args.Length >=2 ){  
            osVersion = new Version(args[1]);  
         }else{  
            throw new ArgumentException("OS Version not specified.");  
         }  
         Console.WriteLine("Desired OS Version: " + osVersion.ToString());  
  
         XmlDocument document;  
         XmlNamespaceManager namespaceManager;  
         namespaceManager = new XmlNamespaceManager(new NameTable());  
         namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");  
         namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");  
  
         document = new XmlDocument();  
         document.Load(applicationManifestPath);  
  
         string baseXPath;  
         baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";  
  
         // Change minimum required operating system version.  
         XmlNode node;  
         node = document.SelectSingleNode(baseXPath, namespaceManager);  
         node.Attributes["majorVersion"].Value = osVersion.Major.ToString();  
         node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();  
         node.Attributes["buildNumber"].Value = osVersion.Build.ToString();  
         node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();  
  
         document.Save(applicationManifestPath);  
      }  
   }  
   ```  
  
    命令接受兩個引數：應用程式資訊清單的路徑 (也就是建置程序建立資訊清單的資料夾，通常為 Projectname.publish)，以及新的作業系統版本。  
  
5. 建置專案。 在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
6. 將 .exe 檔案 (例如 `C:\TEMP\ChangeOSVersionVB.exe`) 複製到目錄。  
  
   接下來，在建置後事件中叫用此命令，以修改應用程式資訊清單。  
  
#### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>叫用建置後事件，以修改應用程式資訊清單  
  
1. 針對要發行的專案，建立 Windows 應用程式。 從 [檔案] 功能表，指向 [新增]，然後按一下 [專案]。  
  
2. 在 [新增專案] 對話方塊中，展開 [Visual C#]、依序按一下 [Windows] 和 [Windows Forms 應用程式] 範本。 將專案命名為 `CSWinApp`。  
  
3. 選取方案總管中的專案，然後按一下 [專案] 功能表中的 [屬性]。  
  
4. 在 [專案設計工具] 中，找到 [發行] 頁面，然後將 [發行位置] 設為 `C:\TEMP\`。  
  
5. 按一下 [Publish Now]\(立即發行)，即可發行專案。  
  
     隨即建立資訊清單檔並將其放入`C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest`。 若要檢視資訊清單，請以滑鼠右鍵按一下檔案、按一下 [開啟方式]、選取 [從清單中選取程式]，然後按一下 [記事本]。  
  
     在檔案中搜尋 `<osVersionInfo>` 項目。 例如，版本可能是：  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6. 在專案設計工具中，依序按一下 [建置事件] 索引標籤和 [建置後進行編輯] 按鈕。  
  
7. 在 [建置後事件命令列] 文字方塊中，輸入下列命令：  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     當您建置專案時，此命令會將應用程式資訊清單中的最低作業系統版本變更為 5.1.2600.0。  
  
     因為 `$(TargetPath)` 巨集會表達正在建立之可執行檔的完整路徑，所以 `$(TargetPath)`.manifest 將會指定在 bin 目錄中建立的應用程式資訊清單。 發行時，系統會將這份資訊清單複製到您先前設定的發行位置中。  
  
8. 再次發行專案。 移至 [發行] 頁面，然後按一下 [Publish Now]\(立即發行)。  
  
     再次檢視資訊清單。 若要檢視資訊清單，請開啟發行目錄，以滑鼠右鍵按一下檔案、按一下 [開啟方式]、選取 [從清單中選取程式]，然後按一下 [記事本]。  
  
     現在，版本應讀為：  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [專案設計工具、建置事件 (C#)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [建置前事件/建置後事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [如何：指定建置事件 (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)   
 [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
