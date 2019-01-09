---
title: 適用於安裝的命令列參數範例
description: 自訂這些範例來建立您自己的 Visual Studio 命令列安裝。
ms.date: 11/14/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6584d1b1864712a1c97b8d2405e7b366c5dd69d6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989983"
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Visual Studio 2017 安裝的命令列參數範例

為了說明如何[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)，以下是幾個範例，您可以自訂以符合您的需求。

在每個範例中，`vs_enterprise.exe`、`vs_professional.exe` 和 `vs_community.exe` 表示 Visual Studio 啟動載入器的個別版本，這是起始下載程序的小型檔案 (約 1 MB)。 如果您使用不同的版本，請取代為適當的啟動載入器名稱。

> [!NOTE]
> 所有命令都需要提升系統管理權限，如果未從已提升權限的提示字元啟動程序，則會顯示 [使用者帳戶控制] 提示。
>
> [!NOTE]
>  您可以在命令列結尾處使用 `^` 字元，將多行串連成單一命令。 或者，您也可以直接將這幾行放到一列。 在 PowerShell 中，對等項目為倒引號 (`` ` ``) 字元。

## <a name="using---installpath"></a>使用 --installPath

* 安裝 Visual Studio 的最小執行個體，不會顯示互動式提示，但會顯示進度：

  ```cmd
  vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* 使用命令列更新 Visual Studio 執行個體，不顯示互動式提示，但顯示進度：

  ```cmd
  vs_enterprise.exe --update --quiet --wait
  vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
  ```

  > [!NOTE]
  > 兩個命令都是必要的。 第一個命令更新 Visual Studio 安裝程式。 第二個命令更新 Visual Studio 執行個體。 若要避免 [使用者帳戶控制] 對話方塊，請以系統管理員身分執行命令提示字元。

* 使用法文語言套件以無訊息方式安裝 Visual Studio 的桌面執行個體，並只在安裝產品時傳回。

  ```cmd
  vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

  > [!NOTE]
  > `--wait` 參數是專為在批次檔中使用所設計。 在批次檔中，直到安裝完成之後，才會繼續執行下一個命令。 `%ERRORLEVEL%` 環境變數會包含命令的傳回值，如[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md) 頁面中所述。

## <a name="using---layout"></a>使用 --layout

* 下載 Visual Studio 核心編輯器 (最基本的 Visual Studio 設定)。 只包含英文語言套件：

  ```cmd
  vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* 下載 .NET 桌面和 .NET Web 工作負載，以及所有建議的元件和 GitHub 延伸模組。 只包含英文語言套件：

  ```cmd
  vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---includerecommended"></a>使用 --includeRecommended

* 啟動 Visual Studio 2017 Enterprise 版中可用之所有工作負載和元件的互動式安裝：

  ```cmd
  vs_enterprise.exe --all --includeRecommended --includeOptional
  ```

* 在已安裝 Visual Studio 2017 Community 版的電腦上安裝第二個名為 Visual Studio 2017 Professional 的執行個體，並提供 Node.js 開發的支援：

  ```cmd
  vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>使用 --remove

* 從預設安裝的 Visual Studio 執行個體移除程式碼剖析工具元件：

  ```cmd
  vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

## <a name="using---path"></a>使用 --path

這些命令列參數是**在 15.7 中新增的**。 如需詳細資訊，請參閱 [Use command-line parameters to install Visual Studio](use-command-line-parameters-to-install-visual-studio.md) (使用命令列參數安裝 Visual Studio) 頁面。

* 使用安裝、快取和共用路徑：

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* 只使用安裝和快取路徑：

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* 只使用安裝和共用路徑：

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* 只使用安裝路徑：

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>使用 export

此命令列命令是 **15.9 中的新功能**。 如需其詳細資訊，請參閱[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md) 頁面。

* 使用 export 可儲存來自安裝的選取項目：

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
```

* 使用 export 可從頭開始儲存自訂選取項目：

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
```

## <a name="using---config"></a>使用 --config

此命令列參數是 **15.9 中的新功能**。 如需其詳細資訊，請參閱[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md) 頁面。

* 使用 --config 可從先前儲存的安裝組態檔安裝工作負載和元件：

```cmd
vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
```

* 使用 --config 可將工作負載和元件新增至現有的安裝：

```cmd
vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
```


[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [建立 Visual Studio 2017 的離線安裝](create-an-offline-installation-of-visual-studio.md)
