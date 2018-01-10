---
title: "在 Visual Studio 中不使用專案或方案來開發程式碼 | Microsoft Docs"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code, editing
- code editor, syntax coloring
- code editor [Visual Studio]
- brace matching
- code editor, line numbers
- code editor, brace matching
- line numbers
- syntax coloring
- code editor
- code files
- code
ms.assetid: cb53bb9b-5b76-4759-b9b8-7bf32298bcbb
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 78b59ff3d8d6c54465ce29334c1dbe041b7a71be
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>在 Visual Studio 中不使用專案或方案來開發程式碼  
在 Visual Studio 2017 中，您可以在 Visual Studio 中從幾乎任何類型的目錄型專案開啟程式碼，而不需使用方案或專案檔。 例如，這意謂著您可以在 Git 上尋找程式碼專案、複製它，然後直接在 Visual Studio 中開啟它並開始開發，而不需建立方案或專案。  

您不僅可以在 Visual Studio 中編輯程式碼並建置它，還可以瀏覽程式碼 (例如透過使用 [巡覽至] 命令)。 程式碼的語法會以色彩標示，並且在許多情況下，會包含基本陳述式完成和偵錯，其中會包含中斷點。 有些語言甚至還會包含更多功能。 如需詳細資訊，請參閱[建立可移植的自訂編輯器設定](create-portable-custom-editor-options.md)。  

## <a name="open-code-anywhere"></a>在開啟任何位置的程式碼  
您可以透過下列方式在 Visual Studio 中開啟程式碼：  

- 在 Visual Studio 功能表列上，選擇 [檔案] > [開啟] > [資料夾]，然後瀏覽至程式碼位置。  

- 在包含程式碼之資料夾 (按一下滑鼠右鍵) 的操作功能表上，選擇 [在 Visual Studio 中開啟] 命令。  

- 在 Visual Studio 的 [開始] 頁面上，選擇 [開啟資料夾] 連結。  

- 開啟從 GitHub 儲存機制複製的程式碼。  

### <a name="to-open-code-from-a-cloned-github-repo"></a>從複製的 GitHub 儲存機制開啟程式碼  
下列範例說明如何複製 GitHub 儲存機制，然後在 Visual Studio 中開啟其程式碼。 若要依照此程序，您必須擁有 GitHub 帳戶並在您的系統上安裝 Git for Windows。 如需詳細資訊，請參閱[註冊新的 GitHub 帳戶 (英文)](https://help.github.com/articles/signing-up-for-a-new-github-account/) 和 [Git for Windows (英文)](https://git-for-windows.github.io/)。  

1. 移至您想要複製到 GitHub 的存放庫。  

1. 選擇 [Clone or Download] (複製或下載) 按鈕，然後選擇下拉式清單中的 [複製到剪貼簿] 按鈕，以複製 GitHub 存放庫的安全 URL。  

  ![GitHub 複製按鈕](./media/VSIDE_Code_Clone.png)

    > [!NOTE]
    >  雖然您也可以選擇在您的桌上型電腦上開啟該專案，或下載該專案的 .zip 檔案，但此範例會示範如何使用安全 URL 方法來複製儲存機制。

1. 在 Visual Studio 中，選擇 [Team Explorer] 索引標籤以開啟 [Team Explorer]。  

1. 在 [Team Explorer] 中的 [本機 Git 儲存機制] 區段底下，選擇 [複製] 命令，然後將 GitHub 頁面的 URL 貼到文字方塊中。  

  ![複製專案](./media/VSIDE_Code_Clone2.png)

1. 選擇 [複製] 按鈕，以將專案的檔案複製到本機 Git 儲存機制。 視儲存機制的大小而定，此程序可能會花費數分鐘的時間。  

1. 將存放庫複製到您的系統之後，在 [Team Explorer] 中，從新複製的存放庫 (按一下滑鼠右鍵) 的操作功能表上，選擇 [開啟] 命令。  

  ![複製的存放庫](./media/VSIDE_Code_Clone3.png)

1. 選擇 [顯示資料夾檢視] 命令，以在 [方案總管] 中檢視檔案  

  ![顯示資料夾檢視](./media/VSIDE_Code_Clone3_show.png)

  您現在可以瀏覽所複製存放庫中的資料夾和檔案，並在 Visual Studio 程式碼編輯器中檢視及搜尋程式碼，其中會包含語法色彩標示及其他功能。

    ![搜尋已複製的專案程式碼](./media/VSIDE_Code_Clone4.png)  

|         |         |
|---------|---------|
|  ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片")  |    [觀看影片](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171) 了解如何使用 Visual Studio 複製及開啟 GitHub 存放庫的程式碼。 |

## <a name="debug-your-code"></a>偵錯程式碼  
您可以在 Visual Studio 中偵錯程式碼，不使用專案或解決方案。 若要針對某些語言進行偵錯，您可能需要指定程式碼專案中的有效「啟動檔案」，例如指令碼、可執行檔或專案。 當您針對程式碼進行偵錯時，Visual Studio 會先執行這個指定的程式碼。  

工具列上 [開始] 按鈕旁邊的下拉式清單除了會列出您在資料夾中特別選擇的項目之外，也會列出 Visual Studio 偵測到的所有啟動項目。  

![執行按鈕](./media/VSIDE_Code_Run_Button.png)  

Visual Studio 會自動辨識專案，但指令碼 (例如 Python 和 JavaScript) 則必須在您明確選取來作為啟動項目之後，它們才會顯示在清單中。 此外，有些啟動項目 (例如 MSBuild 和 CMake) 可以有多個組建組態，這些組態會顯示在「執行按鈕」的下拉式清單中。  

Visual Studio 目前支援下列語言的偵錯：  

- Node.js  

- Python  

- MSBuild 型專案 (C#、VB、C++)  

- 任何含有 PDB (Python 偵錯工具) 檔案的可執行檔。  

### <a name="to-debug-nodejs-and-python"></a>針對 Node.js 和 Python 進行偵錯：  
1. 安裝 Node.js 或 Python 工具或是 Visual Studio 2017 及 Node.js 執行階段。  

1. 在 [方案總管] 中 JavaScript 檔案的操作功能表上，選擇 [設定為啟動項目] 命令。  

1. 選擇 **F5** 鍵開始偵錯。  

### <a name="to-debug-msbuild-projects"></a>針對 MSBuild 專案進行偵錯  
1. 在 Visual Studio 功能表上，選擇 [偵錯]。 在下拉式功能表上，選擇專案，或選取您想要在方案總管中顯示為啟動項目的專案或檔案。  

1. 選擇 **F5** 鍵開始偵錯。  

### <a name="to-debug-executable-files"></a>針對可執行檔進行偵錯  
1. 在 Visual Studio 功能表上，選擇 [偵錯]。 在下拉式功能表上，選擇專案，或選取您想要在方案總管中顯示為啟動項目的專案或檔案。  

1. 選擇 **F5** 鍵開始偵錯。  

## <a name="enable-custom-build-tools"></a>啟用自訂建置工具
Visual Studio 知道如何執行許多不同的語言，但不是所有語言它都知道怎麼執行。 如果 Visual Studio 知道如何執行您的語言，您可以立即執行程式碼。 如果您嘗試執行程式碼但 Visual Studio 不知道如何執行它，資訊列將會提示您指定程式碼基底中的檔案來作為啟動項目。  

如果程式碼基底使用 Visual Studio 無法辨識的自訂組建工具，在您完成一些額外步驟前，可能無法在 Visual Studio 中執行和偵錯程式碼。 您必須指定有效的可執行檔類型，例如編譯器，以及語言所需的任何自訂參數和引數。 為了啟用這項功能，Visual Studio 提供「建置工作」。 您可以建立建置工作來指定語言在建置及執行其程式碼時所需的一切項目。  

您也可以建立任意建置工作，來執行幾乎您想要執行的任何操作。 例如，您可以建立工作來列出資料夾的內容或將檔案重新命名。 或者，您也可以建立目標更明確的建置工作，以執行像是使用特定引數來進行編譯及建置專案的操作。 下列步驟說明如何建立這兩種類型的建置工作。  

#### <a name="to-create-an-arbitrary-build-task"></a>建立任意建置工作  
1. 選擇 [方案總管] 中您想要使用工作的專案檔案或資料夾，然後在該檔案或資料夾 (按一下滑鼠右鍵) 的操作功能表上，選擇 [設定工作]。  

  ![設定工作](./media/VSIDE_Code_Config_Task.png)

  選擇 [設定工作] 會開啟名為 tasks.vs.json 的檔案。 如果此檔案不存在，系統便會建立它。 此檔案會包含所選檔案或資料夾的建置工作。  

  ![Tasks.vs.json 檔案](./media/VSIDE_Code_Tasks_JSON.png)

1. 將下列建置工作新增到 tasks.vs.json。 針對這個範例，我們將新增一個名為 "List outputs" 的簡單工作，它會在 [輸出] 視窗中列出所選資料夾的檔案和子資料夾。 (您應該在現有的 "tasks" 陣列內新增新的工作)。  

  ```xml
      {
        "taskName": "List outputs",
        "appliesTo": "*",
        "type": "command",
        "command": "${env.COMSPEC}",
        "args": [
          "dir ${outDir}"
        ]
      },
  ```
  整個建置工作應該會看起來如下。  

  ![任意建置工作](./media/VSIDE_Code_Tasks_ArbTask.png)

1. 儲存專案。  

1. 開啟所選資料夾的操作功能表。 您應該會看到新的任意建置工作出現在操作功能表的底部。  

  ![任意建置工作命令](./media/VSIDE_Code_Tasks_ArbTask2.png)

1. 選擇新的 [List outputs] 命令來執行工作。  

### <a name="to-create-a-custom-build-task"></a>建立自訂建置工作
在此程序中，我們將新增兩個自訂建置工作，這些工作會使用 nMake 來建置和清除程式碼。  

1. 選擇方案總管中您想要稍後指定為啟動項目的專案檔案。 在該檔案 (按一下滑鼠右鍵) 的操作功能表上，選擇 [設定工作]。  

  ![自訂建置工作命令](./media/VSIDE_Code_Tasks_CustTask1.png)

1. 將下列建置工作新增到 tasks.vs.json。 針對這個範例，我們將新增兩個工作：一個叫做 "makefile-build"，另一個叫做 "makefile-clean"，前者會使用 nMake 命令來建置專案，後者會使用 "clean" 引數來呼叫 nMake 命令。 您應該在現有的 "tasks" 陣列內新增這些工作。 (請注意，這些只是範例建置工作。 若要讓它們實際運作，您的系統上必須安裝包含 [nMake](/cpp/build/nmake-reference) 的工作負載)。

  ```xml
  {
  "taskName": "makefile-build",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "build",
  "command": "nmake"
  },
  {
  "taskName": "makefile-clean",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "clean",
  "command": "nmake",
  "args": [
    "clean"
    ]
  },
  ```
  整個自訂建置工作應該會看起來如下。  

  ![自訂建置工作](./media/VSIDE_Code_Tasks_CustTask2.png)

1. 儲存專案。  

1. 開啟所選檔案的操作功能表。 新的自訂建置工作應該會出現在操作功能表的中間。  

  ![自訂建置工作命令](./media/VSIDE_Code_Tasks_CustTask3.png)

  > [!NOTE]
  > 由於這些命令的 `contextType` 設定緣故，因此它們會顯示在 [設定工作] 命令底下；"build" 和 "clean" 是建置命令，因此它們會顯示在操作功能表中間的建置區段中。  

  既然您已將自訂建置命令與檔案建立關聯，現在便可指派該檔案作為啟動項目。  

1. 在檔案的操作功能表上，選擇 [設定為啟動項目]。  

  ![自訂建置工作命令](./media/VSIDE_Code_Tasks_CustTask4.png)

1. 在工具列上，選擇 [開始] 按鈕旁邊的下拉式箭號。 啟動項目現在已顯示為選項。  

  ![自訂建置工作命令](./media/VSIDE_Code_Tasks_CustTask5.png)

您現在可以選擇 [開始] 按鈕或 **F5** 鍵來執行程式碼基底。 即使 Visual Studio 無法辨識程式碼基底的建置工作，您仍然可以在 Visual Studio 中進行程式碼基底編輯和偵錯。 來自建置工作的輸出會顯示在 [輸出] 視窗中，而建置錯誤則會顯示在 [錯誤清單] 中。 tasks.vs.json 建置工作檔案會將 Visual Studio 內部開發迴圈與您程式碼基底所使用的自訂建置工具結合。  

您可以將自訂建置工作新增到個別檔案中，也可以新增到特定類型的所有檔案中。 例如，您可以將 NuGet 套件檔案設定成包含「還原套件」工作，或是將所有原始程式檔設定成包含靜態分析工作 (例如適用於所有 .js 檔案的 Linter)。  

Visual Studio 除了環境變數 (例如 `$env.var`) 或機碼之外，也支援替代 tasks.vs.json 根目錄中的 VSCode `$variable`。  

## <a name="specify-build-output"></a>指定建置輸出  
如果您的專案需要進行編譯，則您可以在 tasks.vs.json 檔案中新增一個名為 `output` 的額外標記。 以下是一個範例。  

`"output": "${workspaceRoot}\\bin\\hellomake.exe"`

指定輸出位置可讓 Visual Studio 知道到哪裡尋找專案的組建輸出。  

## <a name="tasksvsjson-file-location"></a>Tasks.vs.json 檔案位置  
tasks.vs.json 檔案預設會位於名為 `.vs` 的隱藏資料夾中。 若要在 Visual Studio 中檢視隱藏的檔案，請選擇 [方案總管] 工具列上的 [顯示所有檔案] 按鈕。  

![任意建置工作命令](./media/VSIDE_Code_Tasks_FileLocation.png)

tasks.vs.json 檔案會隱藏，因為大多數使用者通常都不會想要將它簽入原始檔控制。 不過，如果您想要能夠將它簽入原始檔控制，請將檔案拖曳到您專案的根目錄中，這樣便能夠顯示它。  

其他 .json 檔案可能會在 .vs 資料夾中，但您應該移動的檔案僅限 tasks.vs.json 檔案和 launch.vs.json 檔案 (如果存在的話)。 launch.vs.json 檔案會設定 Visual Studio 偵錯工具，而 tasks.vs.json 檔案則會設定 Visual Studio 中的組建。  

## <a name="see-also"></a>另請參閱
[在程式碼和文字編輯器中撰寫程式碼](../ide/writing-code-in-the-code-and-text-editor.md)
