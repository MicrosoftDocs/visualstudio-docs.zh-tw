---
title: 如何：指定建置事件 (Visual Basic)
description: 瞭解如何使用 Visual Basic 中的組建事件，在編譯器中執行腳本、宏或其他動作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 426b387603fbe7bca29f2ad4f507f2e517cac9bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869254"
---
# <a name="how-to-specify-build-events-visual-basic"></a>如何：指定建置事件 (Visual Basic)

在 Visual Basic 中的建置事件可以用來執行指令碼、巨集或編譯處理程序當中的其他動作。 編譯之前發生的是建置前事件；編譯之後發生的則是建置後事件。

您可在 [建置事件] 對話方塊 (位於 [專案設計工具} 的 [編譯] 頁面) 中，指定建置事件。

> [!NOTE]
> Visual Basic Express 不支援建置事件的項目。 只有完整版 Visual Studio 產品才支援此項目。

## <a name="how-to-specify-pre-build-and-post-build-events"></a>如何指定建置前和建置後事件

### <a name="to-specify-a-build-event"></a>若要指定建置事件

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [編譯] 索引標籤。

3. 按一下 [建置事件] 按鈕，開啟 [建置事件] 對話方塊。

4. 輸入建置前或建置後動作的命令列引數，然後按一下 [確定]。

    > [!NOTE]
    > `call`在所有執行 *.bat* 檔案的建立後命令之前加入語句。 例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。

    > [!NOTE]
    > 如果您的建置前或建置後事件未順利完成，您可以將代碼不為零 (0) 的事件動作結束 (若為 0 表示動作成功)，以終止建置。

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>範例：如何使用建置後事件變更資訊清單

下列程式顯示如何在應用程式資訊清單中設定最低作業系統版本，方法是在專案目錄) 中，使用從建立後事件呼叫的 *.exe* 命令 *(。* 最低作業系統版本是由四組號碼來表示，例如 4.10.0.0。 若要進行上述作業，請使用命令來變更資訊清單的 `<dependentOS>` 區段：

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>建立 .exe 命令以變更應用程式資訊清單

1. 建立命令的主控台應用程式。 **在 [檔案**] 功能表中，按一下 [**新增**]，然後按一下 [**專案**]。

2. 在 [新增專案] 對話方塊的 [Visual Basic] 節點中，依序選取 [Windows] 和 [主控台應用程式] 範本。 將專案命名為 `ChangeOSVersionVB`。

3. 在 [在] *中，將* 下列這一行新增至檔案頂端的其他 `Imports` 語句：

   ```vb
   Imports System.Xml
   ```

4. 將下列程式碼加入 `Sub Main`：

   ```vb
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

   此命令會採用兩個引數。 第一個引數是應用程式資訊清單的路徑 (也就是組建程式建立資訊清單的資料夾，通常是 *\<ProjectName> 發佈*) 。 第二個引數是新的作業系統版本。

5. 在 [建置] 功能表上，按一下 [建置方案]。

6. 複製 *.exe* 檔案到例如 *C:\TEMP\ChangeOSVersionVB.exe* 的目錄。

   接下來，在建置後事件中叫用此命令，以變更應用程式資訊清單。

### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>叫用建置後事件，以變更應用程式資訊清單

1. 針對要發行的專案，建立 Windows 應用程式。 **在 [檔案**] 功能表中，按一下 [**新增**]，然後按一下 [**專案**]。

2. 在 [新增專案] 對話方塊的 [Visual Basic] 節點中，依序選取 [Windows 桌面] 和 [Windows Forms 應用程式] 範本。 將專案命名為 `VBWinApp`。
3. 選取方案總管中的專案，然後按一下 [專案] 功能表中的 [屬性]。

4. 在 **專案設計工具** 中，移至 [發行] 頁面，然後將 [發行位置] 設為 *C:\TEMP*。

5. 按一下 [Publish Now]\(立即發行)，即可發行專案。

     會建置資訊清單檔並將它放入 *C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest*。 若要檢視資訊清單，請以滑鼠右鍵按一下檔案，然後依序按一下 [開啟方式]、[從清單中選取程式] 以及 [記事本]。

     在檔案中搜尋 `<osVersionInfo>` 項目。 例如，版本可能是：

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. 在 **專案設計工具** 中，移至 [編譯] 索引標籤，並按一下 [建置事件] 按鈕以開啟 [建置事件] 對話方塊。

7. 在 [建置後事件命令列] 文字方塊中，輸入下列命令：

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     當您建置專案時，此命令會將應用程式資訊清單中的最低作業系統版本變更為 5.1.2600.0。

     `$(TargetPath)` 巨集表示要建立之可執行檔的完整路徑。 因此，*$(TargetPath).manifest* 會指定在 *bin* 目錄中建立應用程式資訊清單。 發行時，系統會將這份資訊清單複製到您先前設定的發行位置中。

8. 再次發行專案。 移至 [發行] 頁面，然後按一下 [Publish Now]\(立即發行)。

     再次檢視資訊清單。 若要檢視資訊清單，請移至發行目錄，以滑鼠右鍵按一下檔案，然後依序按一下 [開啟方式]、[從清單中選取程式] 以及 [記事本]。

     現在，版本應讀為：

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>另請參閱

- [編譯頁面、專案設計工具 (Visual Basic) ](../ide/reference/compile-page-project-designer-visual-basic.md)
- [專案設計工具、發行頁](../ide/reference/publish-page-project-designer.md)
- [預先建立事件/後置事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [如何：指定建置事件 (C#)](../ide/how-to-specify-build-events-csharp.md)
