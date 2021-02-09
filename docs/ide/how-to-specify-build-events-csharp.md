---
title: 如何：指定建置事件 (C#)
description: 瞭解如何使用組建事件來指定在組建開始之前或組建完成之後執行的命令。
ms.custom: SEO-VS-2020
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e1ea031391b93d571b9f34ad820f1a6957dab242
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869241"
---
# <a name="how-to-specify-build-events-c"></a>如何：指定建置事件 (C#)

使用建置事件指定要在建置開始之前，或建置完成之後執行的命令。 只有在建置成功到達建置流程中的這些點時，建置事件才會執行。

建置專案時，建置前事件會新增至名為 *PreBuildEvent.bat* 的檔案，而建置後事件會新增至名為 *PostBuildEvent.bat* 的檔案。 如果您想要確保錯誤檢查，請將您自己的錯誤檢查命令新增至建置步驟。

## <a name="specify-a-build-event"></a>指定建置事件

1. 在 [方案總管] 中，選取您想要指定建置事件的專案。

2. 按一下 [專案]  功能表上的 [屬性]  。

3. 選取 [建置事件] 索引標籤。

4. 在 [建置前事件命令列] 方塊中，指定建置事件的語法。

   > [!NOTE]
   > 如果專案是最新狀態，而且未觸發任何建置，則建置前事件不會執行。

5. 在 [建置後事件命令列] 方塊中，指定建置事件的語法。

   > [!NOTE]
   > `call`在所有執行 *.bat* 檔案的建立後命令之前加入語句。 例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。

6. 在 [執行建置後事件] 方塊中，指定要執行建置後事件的情況。

   > [!NOTE]
   > 若要新增冗長的語法，或從 [建置前事件/建置後事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)選取任何建置巨集，請按一下省略符號按鈕 (**...**) 來顯示編輯方塊。

   建置事件語法可以包含在命令提示字元或 *.bat* 檔案中的任何有效命令。 批次檔的名稱之前應該加上 `call` 以確保所有後續的命令都會執行。

   > [!NOTE]
   > 如果您的建置前或建置後事件未順利完成，您可以將代碼不為零 (0) 的事件動作結束 (若為 0 表示動作成功)，以終止建置。

## <a name="example"></a>範例

下列程序示範如何使用從建置後事件呼叫的 *.exe* 命令 (專案目錄中的 *.exe.manifest* 檔案)，設定應用程式資訊清單中的最低作業系統版本。 最低作業系統版本是由四組號碼來表示，例如 4.10.0.0。 為了設定最低作業系統版本，命令將會變更資訊清單的 `<dependentOS>` 區段：

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>建立 .exe 命令以變更應用程式資訊清單

1. 針對命令建立新的 **主控台應用程式** 專案。 將專案命名為 **ChangeOSVersionCS**。

2. 在 *Program.cs* 中，將下列這一行新增至檔案頂端的其他指示詞 `using` ：

   ```csharp
   using System.Xml;
   ```

3. 在 `ChangeOSVersionCS` 命名空間中，將 `Program` 類別實作取代為下列程式碼：

   ```csharp
   class Program
   {
      /// <summary>
      /// This function sets the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest)
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

   命令接受兩個引數：應用程式資訊清單的路徑 (也就是建置程序建立資訊清單的資料夾，通常為 *Projectname.publish*)，以及新的作業系統版本。

4. 建置專案。

5. 複製 *.exe* 檔案到例如 *C:\TEMP\ChangeOSVersionVB.exe* 的目錄。

接下來，在建置後事件中叫用此命令，以修改應用程式資訊清單。

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>叫用建置後事件，以修改應用程式資訊清單

1. 建立新的 **Windows Forms 應用程式** 專案，並命名為 **CSWinApp**。

2. 選取 [方案總管] 中的專案，然後在 [專案] 功能表中選擇 [屬性]。

3. 在 **專案設計工具** 中，找到 [發行] 頁面，然後將 [發行位置] 設為 *C:\TEMP*。

4. 按一下 [Publish Now]\(立即發行)，即可發行專案。

   資訊清單檔會建置並儲存至 *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*。 若要檢視資訊清單，請以滑鼠右鍵按一下檔案、按一下 [開啟方式]、選取 [從清單中選取程式]，然後按一下 [記事本]。

   在檔案中搜尋 `<osVersionInfo>` 項目。 例如，版本可能是：

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. 回到 [專案設計工具]，依序按一下 [建置事件] 索引標籤和 [建置後進行編輯]。

6. 在 [建置後事件命令列] 文字方塊中，輸入下列命令：

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   當您建置專案時，此命令會將應用程式資訊清單中的最低作業系統版本變更為 5.1.2600.0。

   因為 `$(TargetPath)` 巨集會表達正在建立之可執行檔的完整路徑，所以 `$(TargetPath).manifest` 將會指定在 *bin* 目錄中建立的應用程式資訊清單。 發佈時，系統會將這份資訊清單複製到您先前設定的發佈位置中。

7. 再次發行專案。

   現在，應可讀取資訊清單版本：

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>另請參閱

- [專案設計工具、 (c # ) 的 [組建事件] 頁面 ](../ide/reference/build-events-page-project-designer-csharp.md)
- [預先建立事件/後置事件命令列對話方塊](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [如何：指定建置事件 (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
