---
title: 定義 Python 專案的自訂功能表命令
description: 您可以藉由編輯專案和目標檔案，將自訂命令新增至 Visual Studio 中的 Python 專案操作功能表，以叫用可執行程式、指令碼、模組、內嵌程式碼片段，以及 pip。
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 43270ee1ec956f45b76d23a6b649ad2d870638c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887922"
---
# <a name="define-custom-commands-for-python-projects"></a>定義 Python 專案的自訂命令

在使用 Python 專案的過程中，您可能發現常常需要切換到命令視窗來執行特定指令碼或模組、PIP 命令或其他任意工具。 若要改善工作流程，您可以在 Python 專案操作功能表的 [Python] 子功能表新增自訂命令。 這些命令可以在主控台視窗或 Visual Studio 的 [輸出] 視窗中執行。 您也可以使用規則運算式來指示 Visual Studio 如何從命令的輸出剖析錯誤與警告。

依預設，該功能表只會包含單一 **Run PyLint** 命令：

![專案操作功能表上的 Python 子功能表預設外觀](media/custom-commands-default-menu.png)

自訂命令會顯示在此相同的操作功能表中。 自訂命令會直接新增至專案檔，並在其中套用到該個別專案。 您也可以在 *.targets* 檔案中定義自訂命令，該檔案可輕鬆匯入多個專案檔中。

Visual Studio 中有部分 Python 專案範本已經使用其 *.targets* 檔案自行新增自訂命令。 例如，Bottle Web 專案與 Flask Web 專案範本兩者皆會新增兩個命令：[啟動伺服器] 與 [啟動偵錯伺服器]。 Django Web 專案範本除了新增上述命令外，還會新增一些其他命令：

![Django 專案操作功能表上的 Python 子功能表外觀](media/custom-commands-django-menu.png)

每個自訂命令皆可參考 Python 檔案、Python 模組、內嵌 Python 程式碼、任何可執行檔或 PIP 命令。 您也可以指定命令執行的方式與位置。

> [!Tip]
> 每當您在文字編輯器中對專案檔進行變更，都必須在 Visual Studio 中重新載入該專案以套用這些變更。 例如，新增自訂命令定義後，您必須重新載入專案，這些專案才會顯示在專案的操作功能表上。
>
> 您或許已經知道 Visual Studio 有提供能夠直接編輯專案檔的方法。 先以滑鼠右鍵按一下專案檔並選取 **[卸載專案**]，然後再按一下滑鼠右鍵並選取 [**編輯 \<project-name>** ]，即可在 Visual Studio 編輯器中開啟專案。 在進行編輯並加以儲存後，再一次以滑鼠右鍵按一下專案，並選取 [重新載入專案]，此時系統也會提示您確認是否要關閉編輯器中的專案檔。
>
> 在開發自訂命令時，這些點選作業可能會變得相當繁瑣。 若要提高工作流程的效率，請同時在 Visual Studio 與其他編輯器中開啟 *.pyproj* 檔案 (例如另一個 Visual Studio 執行個體、Visual Studio Code 或 [筆記本] 等)。 當您在編輯器中儲存變更並切換至 Visual Studio 時，Visual Studio 會偵測變更，並詢問是否要重載專案 (**專案 \<name> 是否已在環境外部修改。**) 。 選取 [重新載入] 即可一舉立即套用您的所有變更。

## <a name="walkthrough-add-a-command-to-a-project-file"></a>逐步解說：將命令新增至專案檔

為了讓您更熟悉自訂命令，本節將透過使用 *python.exe* 直接執行專案啟動檔案的簡單範例為您進行逐步解說  (這類命令的效果，與在不進行偵錯工具的  >  **情況下** 使用 Debug Start 相同。 ) 

1. 使用 [Python 應用程式] 範本建立名為 "Python-CustomCommands" 的新專案。 (若仍對程序不熟悉，請參閱[快速入門：從範本建立 Python 專案](quickstart-02-python-in-visual-studio-project-from-template.md)的說明。)

1. 在 *Python_CustomCommands.py* 中新增程式碼 `print("Hello custom commands")`。

1. 在 **方案總管** 中以滑鼠右鍵按一下專案，選取 [Python] 並注意子功能表上顯示的唯一命令為 [執行 PyLint]。 您的自訂命令會顯示在此相同的子功能表上。

1. 根據簡介中的建議，在另一個文字編輯器中開啟 *Python-CustomCommands.pyproj*。 然後在檔案的末端，於結尾的 `</Project>` 前新增以下程式行，然後儲存檔案。

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. 切換回 Visual Studio 並在收到檔案變更提示時選取 [重新載入]。 然後再次查看 [Python] 功能表，確認 [執行 PyLint] 是否仍為該處唯一顯示的項目。這樣做的原因是您新增的程式行僅複寫了包含 PyLint 命令的預設 `<PythonCommands>` 屬性群組。

1. 切換至編輯器並開啟專案檔，然後在 `<PropertyGroup>` 後面新增下列 `<Target>` 定義。 如本文後續內容所述，此 `Target` 元素會在主控台視窗中使用 *python.exe* 來定義執行啟動檔案 (由 "StartupFile" 屬性識別) 的自訂命令。 屬性 `ExecuteIn="consolepause"` 使用的主控台會在等候您按下任意鍵之後關閉。

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. 將目標的 `Name` 屬性值新增至稍早新增的 `<PythonCommands>` 屬性群組，使元素看起來類似下方程式碼。 在此清單中新增的目標名稱，即為新增至 [Python] 功能表的項目。

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    若您希望自己的命令顯示在 `$(PythonCommands)` 中定義的項目之前，請將其放在該語彙基元前。

1. 儲存專案檔並切換至 Visual Studio，然後在收到提示時重新載入專案。 隨後以滑鼠右鍵按一下 **Python-CustomCommands** 專案並選取 [Python]。 您隨後應會在功能表上看到 [執行啟動檔案] 項目。 若未看到該功能表項目，請確認您已將名稱新增至 `<PythonCommands>` 元素。 另請參閱本文稍後的[疑難排解](#troubleshooting)。

    ![自訂命令顯示在 Python 操作子功能表上](media/custom-commands-walkthrough-menu-item.png)

1. 選取 [執行啟動檔案] 命令應該會出現命令視窗，其中內容顯示文字 **Hello custom commands**，後面接著 **Press any key to continue**。  按下任意鍵即可關閉視窗。

    ![主控台視窗中的自訂命令輸出](media/custom-commands-walkthrough-console.png)

1. 回到編輯器並開啟專案檔，然後將 `ExecuteIn` 屬性的值變更為 `output`。 儲存檔案，切換至 Visual Studio，重新載入專案並再次叫用命令。 您這次會在 Visual Studio 的 [輸出] 視窗看到程式的輸出：

    ![輸出視窗中的自訂命令輸出](media/custom-commands-walkthrough-output-window.png)

1. 若要新增更多命令，請為各個命令定義適當的 `<Target>` 元素，並將目標名稱新增至 `<PythonCommands>` 屬性群組中，然後在 Visual Studio 中重新載入專案。

>[!Tip]
> 若您叫用了使用專案屬性的命令 (例如 `($StartupFile)`)，而該命令因為未定義語彙基元而失敗，Visual Studio 就會停用該命令，直到您重新載入專案為止。 對定義屬性的專案進行變更並不會重新整理這些命令的狀態，因此在此情況下您仍須重新載入專案。

## <a name="command-target-structure"></a>命令目標結構

下列虛擬代碼呈現了 `<Target>` 元素的一般形式：

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

若要參考專案屬性或屬性值中的環境變數，請在 `$()` 語彙基元中使用名稱，例如 `$(StartupFile)` 與 `$(MSBuildProjectDirectory)`。 如需詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。

### <a name="target-attributes"></a>目標屬性

| 屬性 | 必要 | 描述 |
| --- | --- | --- |
| 名稱 | 是 | Visual Studio 專案中的命令識別項。 您必須將此名稱新增至 `<PythonCommands>` 屬性群組，命令才會顯示在 [Python] 子功能表上。 |
| 標籤 | 是 | [Python] 子功能表上顯示的 UI 顯示名稱。 |
| 傳回 | 是 | 必須包含可將目標識別為命令的 `@(Commands)`。 |

### <a name="createpythoncommanditem-attributes"></a>CreatePythonCommandItem 屬性

所有屬性值均區分大小寫。

| 屬性 | 必要 | 描述 |
| --- | --- | --- |
| TargetType | 是 | 指定目標屬性的內容，以及其搭配 Arguments 屬性使用的方式：<ul><li>：執行在 Target 中命名的可執行檔，附加 Arguments 中的值，使其看似直接在命令列上輸入。 此值只能包含程式名稱，而不能包含引數。</li><li>**script**：以 Target 中的檔案名稱執行 *python.exe*，後面接著 Arguments 中的值。</li><li>**module**：執行 `python -m`，後面依序接著 Target 中的模組名稱及 Arguments 中的值。</li><li>**code**：執行 Target 中包含的內嵌程式碼。 這會忽略 Arguments 值。</li><li>**pip**：以 Target 中的命令執行 `pip`，後面接著 Arguments，is ExecuteIn 設定為 "output"，但 PIP 會假設 `install` 命令並將 Target 用作套件名稱。</li></ul> |
| 目標 | 是 | 要使用的檔案名稱、模組名稱、程式碼或 PIP 命令，端視 TargetType 而定。 |
| 引數 | 選擇性 | 指定要指派至目標的引數字串 (如果有的話)。 請注意，當 TargetType 為 `script` 時，引數會指派至 Python 程序，而非 *python.exe*。 若為 `code` TargetType 請予以略過。 |
| ExecuteIn | 是 | 指定要在其中執行命令的環境：<ul><li>**console**：(預設) 將 Target 與 Arguments 視作直接在命令列上輸入加以執行。 命令視窗會在 Target 執行時顯示，然後自動關閉。</li><li>**consolepause**：與 console 相同，但會在關閉視窗前等待按鍵動作。</li><li>**output**：執行 Target，並在 Visual Studio 的 [輸出] 視窗中顯示其結果。 若 TargetType 為 "pip"，Visual Studio 會將 Target 用作套件名稱並在後面加上 Arguments。</li><li>**repl**：在 [Python 互動式](python-interactive-repl-in-visual-studio.md)視窗中執行 Target；選擇性顯示名稱會用於視窗標題。</li><li>**none**：行為與 console 相同。</li></ul>|
| WorkingDirectory | 選擇性 | 要在其中執行命令的資料夾。 |
| ErrorRegex<br>WarningRegEx | 選擇性 | 僅在 ExecuteIn 為 `output` 時使用。 這兩個值均會指定規則運算式，Visual Studio 將用以剖析命令輸出，並在其 [錯誤清單] 視窗中顯示錯誤與警告。 若未指定，則命令並不會影響 [錯誤清單] 視窗。 如需有關 Visual Studio 要求的詳細資訊，請參閱[具名擷取群組](#named-capture-groups-for-regular-expressions)。 |
| RequiredPackages | 選擇性 | 命令的套件需求清單，格式與 [*requirements.txt*](https://pip.pypa.io/en/stable/user_guide/#requirements-files) (pip.readthedocs.io) 相同。 例如 [執行 PyLint] 命令會指定 `pylint>=1.0.0`。 執行命令前，Visual Studio 會檢查清單中的所有套件皆已安裝。 Visual Studio 會使用 PIP 來安裝所有缺少的套件。 |
| 環境 | 選用 | 可在執行命令前定義的環境變數字串。 每個變數都會使用 \<NAME> = \<VALUE> 具有以分號分隔之多個變數的表單。 具有多個值的變數須以單引號或雙引號括住，例如 'NAME=VALUE1;VALUE2'。 |

#### <a name="named-capture-groups-for-regular-expressions"></a>規則運算式的擷取群組

剖析命令輸出的錯誤與警示時，Visual Studio 要求 `ErrorRegex` 與 `WarningRegex` 值中的規則運算式使用以下具名群組：

- `(?<message>...)`：錯誤的文字
- `(?<code>...)`：錯誤碼
- `(?<filename>...)`：回報有錯誤的檔案名稱
- `(?<line>...)`：檔案中回報錯誤的位置行號。
- `(?<column>...)`：檔案中回報錯誤的資料行編號。

例如，PyLint 會產生下列形式的警告：

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

若要允許 Visual Studio 從這類警告擷取正確資訊，並在 [錯誤清單] 視窗中加以顯示，請依照下列內容指定 [執行 Pylint] 的 `WarningRegex` 值：

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(請注意，值中的 `msg_id` 實際上應為 `code`，請參閱[問題 3680](https://github.com/Microsoft/PTVS/issues/3680)。)

## <a name="create-a-targets-file-with-custom-commands"></a>建立具自訂命令的 .targets 檔案

在專案檔中定義自訂命令，會使命令僅能由該專案檔使用。 若要在多個專案檔中使用命令，請改在 *.targets* 檔案中定義 `<PythonCommands>` 屬性群組與所有 `<Target>` 元素。 隨後將該檔案匯入個別專案檔。

*.targets* 檔案將使用以下格式：

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

若要將 *.targets* 檔案載入專案，請在 `<Project>` 元素中的任一處放置 `<Import Project="(path)">` 元素。 例如，若您在專案的 *targets* 子資料夾中具有名為 *CustomCommands.targets* 的檔案，請使用下列程式碼：

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> 每當您變更 *.targets* 檔案，除了專案本身以外也必須重新載入包含專案的「方案」。

## <a name="example-commands"></a>範例命令

### <a name="run-pylint-module-target"></a>執行 PyLint (模組目標)

下列程式碼會顯示在 *Microsoft.PythonTools.targets* 檔案中：

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>使用特定套件執行 PIP 安裝 (PIP 目標)

下列命令會在 [輸出] 視窗中執行 `pip install my-package`。 您可在開發套件並測試其安裝等情況下使用此類命令。 請注意，使用 `ExecuteIn="output"`時，會假定目標包含套件名稱而非 `install` 命令。

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>顯示到期的 PIP 套件 (PIP 目標)

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>以 consolepause 執行可執行檔

下列命令僅執行 `where` 來顯示位在專案資料夾中的 Python 檔案：

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>執行伺服器與執行偵錯伺服器命令

若要探索 Web 專案的 **啟動伺服器** 與 **啟動偵錯伺服器** 命令定義方式，請查看 [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub)。

### <a name="install-package-for-development"></a>安裝開發用的套件

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*從 [>fxthomas example.pyproj.xml/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) ，與許可權一起使用。*

### <a name="generate-windows-installer"></a>產生 Windows Installer

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*從 [>fxthomas example.pyproj.xml/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) ，與許可權一起使用。*

### <a name="generate-wheel-package"></a>產生 wheel 套件

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*從 [>fxthomas example.pyproj.xml/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) ，與許可權一起使用。*

## <a name="troubleshooting"></a>疑難排解

### <a name="message-the-project-file-could-not-be-loaded"></a>訊息：「無法載入專案檔」

指出專案檔中有語法錯誤。 此訊息包含特定錯誤的行號與字元位置。

### <a name="console-window-closes-immediately-after-command-is-run"></a>主控台視窗會在執行命令後立即關閉

使用 `ExecuteIn="consolepause"`，而不是 `ExecuteIn="console"`。

### <a name="command-does-not-appear-on-the-menu"></a>命令未顯示在功能表上

確認該命令包含在 `<PythonCommands>` 屬性群組內，且命令清單中的名稱與在 `<Target>` 元素中指定的名稱相符。

例如，在下列元素中，屬性群組中的 "Example" 名稱即與目標中的名稱 "ExampleCommand" 不符。 因為 Visual Studio 找不到名為 "Example" 的命令，所以不會出現任何命令。 請使用命令清單中的 "ExampleCommand"，或只將目標的名稱變更為 "Example"。

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>訊息：「執行時發生錯誤 \<command name> 。 無法 \<target-name> 從專案取得命令。」

表示 `<Target>` 或 `<CreatePythonCommandItem>` 元素中的內容不正確。 可能的原因包括：

- 要求的 `Target` 屬性為空白。
- 要求的 `TargetType` 屬性為空白或包含無法辨識的值。
- 要求的 `ExecuteIn` 屬性為空白或包含無法辨識的值。
- 已指定 `ErrorRegex` 或 `WarningRegex`，但未設定 `ExecuteIn="output"`。
- 元素中包含無法辨識的屬性。 例如，您可能使用了 `Argumnets` (拼字有誤) 而非 `Arguments`。

若您參考未定義的屬性，則屬性值可能為空白。 例如，若您使用語彙基元 `$(StartupFile)`，但專案中並未定義任何啟動檔案，則語彙基元會解析至空白的字串。 在此情況下，建議您定義預設值。 例如，若您未另外在專案屬性中指定伺服器啟動檔案，則在 Bottle、Flask 及 Django 專案範本中定義的 [執行伺服器] 與 [執行偵錯伺服器] 命令將預設為 *manage.py*。

### <a name="visual-studio-stops-responding-and-crashes-when-running-the-command"></a>執行命令時，Visual Studio 停止回應並損毀

您可能嘗試以 `ExecuteIn="output"` 執行主控台命令，Visual Studio 在嘗試剖析輸出時可能會損毀。 請改用 `ExecuteIn="console"`。 (請參閱[問題 3682](https://github.com/Microsoft/PTVS/issues/3681)。)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>可執行命令「不是內部或外部命令、可執行程式或批次檔」

當使用 `TargetType="executable"` 時，`Target` 中的值「只能」為不具任何引數的程式名稱，例如單獨使用 *python* 或 *python.exe*。 請將所有引數移至 `Arguments` 屬性。
