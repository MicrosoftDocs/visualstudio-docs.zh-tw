---
title: 擴充 Visual Studio for Mac 逐步解說
description: 瞭解如何建立 Visual Studio for Mac 的簡單擴充套件，以在 [編輯] 功能表中建立新的命令。
ms.custom: SEO-VS-2020
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: 9274f86e8ade5b49b5db0c7f4773cf6fd57ea353
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876190"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>擴充 Visual Studio for Mac 逐步解說

本主題會引導您建立[簡單的延伸模組套件](https://github.com/mjh4/AddIns/tree/master/DateInserter)。 延伸模組套件將在 Visual Studio for Mac 的 [編輯] 功能表中建立新的命令，讓使用者可在開啟的文字文件中插入目前日期和時間。

此範例使用增益集製作程式。 增益集製作程式會建立新的專案範本，並填入我們自訂延伸模組套件所需的檔案。

1. 如果尚未開啟，請先啟動 Visual Studio for Mac：

   ![Visual Studio for Mac 螢幕擷取畫面](media/extending-visual-studio-mac-addin3.png)

2. 使用延伸模組管理員安裝 _增益集製作程式延伸模組套件_。 從 Visual Studio 功能表，選擇 [延伸模組]：

   ![[增益集管理員] 索引標籤](media/extending-visual-studio-mac-addin4.png)

3. 巡覽至 [資源庫] 索引標籤，然後在右上搜尋列鍵入 `Addin Maker`。 從 [增益集開發] 類別選取 [增益集製作程式]，然後按一下 [安裝]<kbd></kbd>。 如果未顯示任何內容，請點擊 [重新整理]，並再次搜尋：

   ![增益集管理員](media/extending-visual-studio-mac-addin5.png)

4. 現在已安裝增益集製作程式，您可以開始建置延伸模組套件。 開始建立新的解決方案。

5. 從 [新增解決方案] 對話方塊，選擇 [其他] > [其他] > [一般] > [Xamarin Studio 增益集] > [C#] 範本，並在接下來的螢幕為新的解決方案命令為 `DateInserter`：

   ![建立新的解決方案](media/extending-visual-studio-mac-addin7New.png)

6. Visual Studio for Mac 將會填入新的解決方案：

   ![填入的解決方案](media/extending-visual-studio-mac-addin8.png)

7. 移除 `Manifest.addin.xml` 中的範本程式碼，並取代為下列內容：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
      <ExtensionModel>
          <Extension path = "/MonoDevelop/Ide/Commands/Edit">
              <Command id = "DateInserter.DateInserterCommands.InsertDate"
                  _label = "Insert Date"
                  defaultHandler = "DateInserter.InsertDateHandler" />
          </Extension>

          <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
              <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
          </Extension>
      </ExtensionModel>
   ```

8. 現在您需要設定最終將處理在文字編輯器中插入日期和時間的檔案。 以滑鼠右鍵按一下專案節點，然後新增檔案。 選取 [一般] > [空類別] 並將新檔案命名為 *InsertDateHandler*：

   ![插入日期處理常式](media/extending-visual-studio-mac-addin9.png)

9. 讓我們移除 `InsertDateHandler.cs` 中的範本程式碼，並取代為下列程式碼：

   ```cs
   using MonoDevelop.Components.Commands;
   using MonoDevelop.Ide;
   using MonoDevelop.Ide.Gui;
   using System;

   namespace DateInserter
   {
      class InsertDateHandler : CommandHandler
      {
          protected override void Run()
          {

          }

          protected override void Update(CommandInfo info)
          {

          }
      }
   }
   ```

   我們稍後會展開這兩個預留位置方法。

10. 以滑鼠右鍵按一下 **DateInserter** 專案並選取 [新增] > [新增檔案]。 選取 [一般] > [列舉是空的]，然後將新檔案命名為 *DateInserterCommands*：

    ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. 新增 `InsertDate` 命令作為 `DateInserterCommands.cs` 檔案中的新列舉：

    ``` cs
    using System;

    namespace DateInserter
    {
      public enum DateInserterCommands
      {
          InsertDate,
      }
    }
    ```

12. 此時，您應該有能使用的延伸模組套件。 您可以儲存工作並執行應用程式來測試它。 IDE 就會啟動 Visual Studio for Mac 的新執行個體，並安裝新的延伸模組套件。 如果您巡覽至 [編輯] 功能表，您會看到 Visual Studio for Mac 有新的選項，稱為 **插入日期**，如以下螢幕擷取畫面所示：

    ![插入日期命令](media/extending-visual-studio-mac-addin11.png)

    請注意，從功能表中選取 [插入日期] 不會有任何效果，因為目前的實作只有預留位置方法。

13. 架構已針對延伸模組套件準備就緒，可以撰寫程式碼啟用插入日期。 首先，請確定 [插入日期命令] 只有在使用者開啟文字檔案時啟用，方法是將 `InsertDateHandler.cs` 中的 `Update` 方法取代為下列程式碼：

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. 以下列程式碼更新命令的 `Run` 方法，插入日期和時間：

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. 最後，讓我們執行延伸模組套件來進行測試。 在 Visual Studio for Mac 的新執行個體中，選取 [編輯] > [插入日期]。 目前的日期和時間會插入在我們的插入號，如以下螢幕擷取畫面所示：

    ![插入日期螢幕擷取畫面](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>請參閱

- [建立您的第一個延伸模組 (Windows 上的 Visual Studio)](/visualstudio/extensibility/extensibility-hello-world)