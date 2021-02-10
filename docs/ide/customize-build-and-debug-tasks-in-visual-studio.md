---
title: 使用 JSON 檔案自訂群組建的調試作業
description: 瞭解如何自訂工作，以提供一些設定詳細資料來執行和偵測 Visual Studio 無法辨識的程式碼基底。
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1088cae031dc3498d2c5cdcd33db8d42f721b7d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954419"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>針對「開啟資料夾」自訂建置及對工作進行偵錯

Visual Studio 知道如何執行許多不同的語言和程式碼基底，但它並非全部都能執行。 若您在 Visual Studio 中[開啟程式碼資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)，且 Visual Studio 知道如何執行您的程式碼，您便可以在無需任何其他設定的情況下立即執行它。

若程式碼基底使用 Visual Studio 無法辨識的自訂建置工具，您便需要提供一些設定詳細資料，以在 Visual Studio 中執行該程式碼並對它進行偵錯。 您可透過定義 *建置工作* 來指示 Visual Studio 建置程式碼的方式。 您可以建立建置一或多個工作，來指定語言在建置及執行其程式碼時所需的一切項目。 您也可以建立任意工作，來執行幾乎您想要執行的任何操作。 例如，您可以建立工作來列出資料夾的內容或將檔案重新命名。

使用下列 *.json* 檔案來自定您無專案的程式碼基底：

|檔案名稱|目的|
|-|-|
|*tasks.vs.json*|指定自訂建置命令和編譯器參數，以及任意 (非建置相關) 工作。<br>透過 [方案總管] 的右鍵功能表項目 [設定工作] 來存取。|
|*launch.vs.json*|針對偵錯指定命令列引數。<br>透過 [方案總管] 的右鍵功能表項目 [偵錯並啟動設定] 來存取。|

這些 *.json* 檔案都是位於您程式碼基底之根資料夾中名為 *.vs* 的隱藏資料夾內。 當您在 [方案總管] 中的檔案或資料夾上選取 [設定工作] 或 [偵錯並啟動設定] 時，Visual Studio 會視需要建立 *tasks.vs.json* 和 *launch.vs.json* 檔案。 這些 *.json* 檔案會隱藏，因為使用者通常都不會想要將它簽入原始檔控制。 不過，如果您想要能夠將它簽入原始檔控制，請將檔案拖曳到您程式碼基底的根目錄中，這樣便能夠顯示它們。

> [!TIP]
> 若要在 Visual Studio 中檢視隱藏的檔案，請選擇 [方案總管] 工具列上的 [顯示所有檔案] 按鈕。

## <a name="define-tasks-with-tasksvsjson"></a>以 tasks.vs.json 定義工作

您可以針對您目前在工作區中所擁有的檔案自動化建置指令碼或任何其他外部作業，方法是直接在 IDE 中以工作的形式執行它們。 您能以滑鼠右鍵按一下檔案或資料夾，並選取 [設定工作] 來設定新工作。

![設定 [工作] 功能表](../ide/media/customize-configure-tasks-menu.png)

這會建立 (或開啟) *.vs* 資料夾中的 *tasks.vs.json* 檔案。 您可以在此檔案中定義組建工作或任意工作，然後使用您從 [方案總管] 右鍵功能表中給予它的名稱來叫用它。

您可以將自訂工作新增到個別檔案中，也可以新增到特定類型的所有檔案中。 比方說，您可以將 NuGet 套件檔案設定為具有「還原套件」工作，或是將所有原始程式檔設定為具有靜態分析工作，例如所有 *.js* 檔案的 linter。

### <a name="define-custom-build-tasks"></a>定義自訂建置工作

如果您的程式碼基底使用 Visual Studio 無法辨識的自訂組建工具，則在您完成一些設定步驟前，將無法在 Visual Studio 中執行程式碼並對它進行偵錯。 Visual Studio 有提供 *建置工作*，可讓您告訴 Visual Studio 建置、重新建置及清除您程式碼的方式。 組建工作檔案 *上的tasks.vs.js* 會將 Visual Studio 內部開發迴圈與您程式碼基底所使用的自訂群組建工具結合在一起。

我們以包含名為 *hello.cs* 之單一 C# 檔案的程式碼基底為例。 這類程式碼基底的 Makefile 看起來可能會像這樣：

<!-- markdownlint-disable MD010 -->
```makefile
build: directory hello.exe

hello.exe: hello.cs
    csc -debug hello.cs /out:bin\hello.exe

clean:
    del bin\hello.exe bin\hello.pdb

rebuild: clean build

directory: bin

bin:
    md bin
```
<!-- markdownlint-enable MD010 -->

針對這種包含建置、清理及重建目標的 Makefile，您可以定義下列 tasks.vs.json 檔案。 它包含針對建置、重新建置及清理程式碼基底的三個建置工作，並使用 NMAKE 作為建置工具。

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "makefile-build",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "build",
      "command": "nmake",
      "args": [ "build" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-clean",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "clean",
      "command": "nmake",
      "args": [ "clean" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-rebuild",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "rebuild",
      "command": "nmake",
      "args": [ "rebuild" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    }
  ]
}
```

在您於 *tasks.vs.json* 中定義組建工作之後，系統會將額外的右鍵功能表 (操作功能表) 項目新增至 [方案總管] 中的相對應檔案。 在此範例中，[建置]、[重建] 和 [清理] 選項會新增至任何 Makefile 檔案的操作功能表。

![具有 [建置]、[重新建置] 及 [清理] 的 Makefile 操作功能表](media/customize-build-rebuild-clean.png)

> [!NOTE]
> 基於其 `contextType` 設定，這些命令會出現在操作功能表中的 [設定工作] 命令底下。 [建置]、[重新建置] 及 [清理] 為建置命令，因此會出現在操作功能表中間的建置區段中。

當您選取其中一項選項時，系統便會執行該工作。 輸出會顯示在 [輸出] 視窗中，而建置錯誤則會顯示在 [錯誤清單] 中。

### <a name="define-arbitrary-tasks"></a>定義任意工作

您可以在 *tasks.vs.json* 檔案中定義任意工作，以執行幾乎任何您想要的動作。 例如，您可以定義工作以顯示目前在 [輸出] 視窗中已選取之檔案的名稱，或是列出指定目錄中的檔案。

下列範例顯示定義單一工作的檔案 *tasks.vs.js* 。 叫用該工作時，它會顯示目前已選取之 *.js* 檔案的檔案名稱。

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.js",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "echo ${file}" ]
    }
  ]
}
```

- `taskName` 會指定要出現在右鍵功能表中的名稱。
- `appliesTo` 能指定可執行該命令的檔案。
- `command` 屬性能指定要叫用的命令。 在此範例中，`COMSPEC` 環境變數會用來識別命令列解譯器，通常為 *cmd.exe*。
- `args` 屬性能指定要傳遞至已叫用命令的引數。
- `${file}` 巨集會在 [方案總管] 中擷取選取的檔案。

在儲存 *tasks.vs.json* 之後，您能以滑鼠右鍵按一下資料夾中的任何 *.js* 檔案，然後選擇 [Echo filename]。 該檔案名稱會顯示在 [輸出] 視窗中。

> [!NOTE]
> 如果您的程式碼基底沒有包含 *tasks.vs.json* 檔案，您可以在 [方案總管] 中，從該檔案的右鍵功能表或操作功能表選擇 [設定工作] 來建立一個。

下一個範例會定義能列出 *bin* 目錄的檔案及子資料夾的工作。

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "List Outputs",
      "appliesTo": "*",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "dir ${outDir}" ]
    }
  ]
}
```

- `${outDir}` 為在 `tasks` 區段之前最先定義的自訂巨集。 它接著會被稱為 `args` 屬性。

此工作適用於所有檔案。 當您在 [方案總管] 中開啟任何檔案的操作功能表時，該工作的名稱 [列出輸出] 會出現在功能表的底部。 當您選擇 [列出輸出] 時，*bin* 目錄的內容會列於 Visual Studio 中的 [輸出] 視窗。

![操作功能表中的任意工作](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>設定範圍

多個 *tasks.vs.json* 檔案可以存在於程式碼基底的根目錄及子目錄。 此設計能提供於程式碼基底的不同子目錄中具有不同行為的彈性。 Visual Studio 會彙總或覆寫程式碼基底中的設定，並以下列順序作為檔案的優先順序：

- 位於根資料夾之 *.vs* 目錄中的設定檔案。
- 系統正在計算其中之設定的目錄。
- 目前目錄的父系目錄，一路向上延伸至根目錄。
- 位於根目錄中的設定檔案。

這些彙總規則適用於 *tasks.vs.json*。 如需針對其他檔案中設定的彙總方式，請參閱本文中對應至該檔案的小節。

### <a name="properties-for-tasksvsjson"></a>適用於 tasks.vs.json 的屬性

本節描述可在 *tasks.vs.json* 中指定的部分屬性。

#### <a name="appliesto"></a>appliesTo

您可以在 `appliesTo` 欄位中指定任何檔案或資料夾的名稱來針對它們建立工作，例如 `"appliesTo": "hello.js"`。 下列檔案遮罩可作為值使用：

|檔案遮罩|Description|
|-|-|
|`"*"`| 工作可供工作區中的所有檔案及資料夾使用|
|`"*/"`| 工作可供工作區中的所有資料夾使用|
|`"*.js"`| 工作可供工作區中所有具有 .js 副檔名的檔案使用|
|`"/*.js"`| 工作可供工作區根目錄中所有具有 .js 副檔名的檔案使用|
|`"src/*/"`| 工作可供 src 資料夾的所有子資料夾使用|
|`"makefile"`| 工作可供工作區中的所有 Makefile 檔案使用|
|`"/makefile"`| 工作僅可供工作區根目錄中的 Makefile 使用|

#### <a name="macros-for-tasksvsjson"></a>適用於 tasks.vs.json 的巨集

|巨集|Description|
|-|-|
|`${env.<VARIABLE>}`| 指定針對開發人員命令提示字元所設定的任何環境變數 (例如 ${env.PATH}、${env.COMSPEC} 等)。 如需詳細資訊，請參閱[適用於 Visual Studio 的開發人員命令提示字元](/dotnet/framework/tools/developer-command-prompt-for-vs)。|
|`${workspaceRoot}`| 工作區資料夾的完整路徑 (例如 C:\sources\hello)|
|`${file}`| 選取來執行此工作之檔案或資料夾的完整路徑 (例如 C:\sources\hello\src\hello.js)|
|`${relativeFile}`| 檔案或資料夾的相對路徑 (例如 src\hello.js)|
|`${fileBasename}`| 沒有路徑或副檔名的檔案名稱 (例如 hello)|
|`${fileDirname}`| 檔案的完整路徑，檔案名 (（例如， *C:\sources\hello\src*) |
|`${fileExtname}`| 所選取檔案的副檔名 (例如 .js)|

## <a name="configure-debugging-with-launchvsjson"></a>搭配 launch.vs.json 設定偵錯

若要設定 CMake 專案以進行偵錯工具，請參閱 [設定 CMake 調試](/cpp/build/configure-cmake-debugging-sessions)程式。

1. 若要針對偵錯設定您的程式碼基底，請在 [方案總管] 中，從可執行檔的右鍵功能表或操作功能表選擇 [偵錯並啟動設定] 功能表項目。

   ![[偵錯並啟動設定] 操作功能表](media/customize-debug-launch-menu.png)

1. 在 [選取偵錯工具] 對話方塊中，選擇其中一個選項，然後選擇 [選取] 按鈕。

   ![[選取偵錯工具] 對話方塊](media/customize-select-a-debugger.png)

   若 *launch.vs.json* 檔案尚未存在，系統將會建立它。

   ```json
   {
     "version": "0.2.1",
     "defaults": {},
     "configurations": [
       {
         "type": "default",
         "project": "bin\\hello.exe",
         "name": "hello.exe"
       }
     ]
   }
   ```

1. 接下來，以滑鼠右鍵按一下 [方案總管] 中的可執行檔，並選擇 [設定為啟動項目]。

   系統會將該可執行檔指定為您程式碼基底的啟動項目，且偵錯 [啟動] 按鈕的標題也會變更以反映該可執行檔的名稱。

   ![自訂的 [啟動] 按鈕](media/customize-start-button.png)

   當您選擇 **F5** 時，偵錯工具會啟動，並於您可能已經設定的所有中斷點上停止。 所有您熟悉的偵錯工具視窗都會可供使用並運作。

   > [!IMPORTANT]
   > 如需 c + + 開啟資料夾專案中自訂群組建和偵錯工具工作的其他詳細資料，請參閱 [Visual Studio 中的 c + + 組建系統的開啟資料夾支援](/cpp/build/open-folder-projects-cpp)。

### <a name="specify-arguments-for-debugging"></a>指定偵錯的引數

您可以在 *launch.vs.json* 檔案中指定要針對偵錯傳入的命令列引數。 在 `args` 陣列中新增引數，如下列範例所示：

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe"
    },
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe a1",
      "args": [ "a1" ]
    }
  ]
}
```

當您儲存此檔案時，新設定的名稱會出現在偵錯目標下拉式清單中，且您可以選取它以啟動偵錯工具。 您可以視需要建立數量不限的偵錯設定。

![偵錯設定下拉式清單](media/customize-debug-configurations.png)

> [!NOTE]
> *launch.vs.json* 中的 `configurations` 陣列屬性是讀取自兩個檔案位置&mdash;程式碼基底的根目錄，以及 *.vs* 目錄。 若發生衝突，系統會優先使用 *.vs\launch.vs.json* 中的值。

## <a name="additional-settings-files"></a>其他設定檔案

除了於此主題中所描述的三個 *.json* 檔案之外，Visual Studio 也會從一些其他的檔案讀取設定 (若它們存在於程式碼基底中的話)。

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual Studio 會從名為 *settings.json* 的檔案讀取有限的設定 (若它存在於名為 *.vscode* 的目錄中的話)。 此功能是針對先前於 Visual Studio Code 中開發的程式碼基底提供。 目前，系統唯一會從 *.vscode\settings.json* 中讀取的設定是 `files.exclude`，它會以視覺方式篩選 [方案總管] 中的檔案，以及篩選來自某些搜尋工具的檔案。

您的程式碼基底中可以有任意數量的 *.vscode\settings.json* 檔案。 從此檔案所讀取的設定，將會套用至 *.vscode* 的父目錄及其所有子目錄。

### <a name="gitignore"></a>.gitignore

*.gitignore* 檔案是用來告訴 Git 有哪些檔案是應該忽略的，也就是您不想要簽入的檔案及目錄。 *.gitignore* 檔案通常會包含為程式碼基底的一部分，使該設定可與程式碼基底的所有開發人員共用。 Visual Studio 會讀取 *.gitignore* 檔案中的模式來以視覺方式篩選檔案，以及篩選來自某些搜尋工具的檔案。

讀取自 *.gitignore* 檔案的設定會套用至其父目錄及所有子目錄。

## <a name="see-also"></a>另請參閱

- [不使用專案或方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [C++ 的開啟資料夾專案](/cpp/build/open-folder-projects-cpp)
- [適用於 C++ 的 CMake 專案](/cpp/build/cmake-projects-in-visual-studio)
- [NMAKE 參考](/cpp/build/reference/nmake-reference)
- [程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md)
