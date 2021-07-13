---
title: 命令列 shell & 提示開發人員
description: 從 [工具] > 命令列功能表開始。 Visual Studio開發人員命令提示字元、開發人員 PowerShell 和終端機可讓您更輕鬆地使用 .NET 和 c + + 工具。
author: TerryGLee
ms.author: tglee
ms.date: 06/11/2021
ms.topic: reference
ms.custom: contperf-fy21q4
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: fef783475304bb1faa1788bde591a22ed610d528
ms.sourcegitcommit: e7629e132a4d2fad6bb5869e4d68d9dbeeae9631
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2021
ms.locfileid: "113649172"
---
# <a name="visual-studio-developer-command-prompt-and-developer-powershell"></a>Visual Studio開發人員命令提示字元和開發人員 PowerShell

Visual Studio 2019 包含適用于開發人員的兩個命令列 shell：

- **Visual Studio 開發人員命令提示字元**-具有特定環境變數的標準命令提示字元，設定為使用命令列開發人員工具更容易。 自 Visual Studio 2015 起提供。

- **Visual Studio Developer PowerShell** -比命令提示字元更強大。 例如，您可以將一個命令的輸出 (稱為) ）傳遞 *cmdlet* 給另一個 cmdlet 。 這個 shell 的環境變數與開發人員命令提示字元的設定相同。 自 Visual Studio 2019 起提供。

:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="顯示 clrver 工具的 Visual Studio 開發人員命令提示字元":::

從 Visual Studio 2019 16.5 版開始，Visual Studio 包含整合式 **終端** 機， (開發人員命令提示字元和開發人員 PowerShell) 都可以裝載這些 shell。 您也可以開啟每個 shell 的多個索引標籤。 Visual Studio 的終端機建置於[Windows 終端機](/windows/terminal/)之上。 若要在 Visual Studio 中開啟終端機，請選擇 [ **View**  >  **terminal**]。

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="顯示多個索引標籤的 Visual Studio 終端機":::

當您從 Visual Studio 開啟其中一個開發介面（可以是個別的應用程式或在終端機視窗中）時，它會開啟至您目前解決方案的目錄 (如果您已) 載入解決方案。 此行為可讓您輕鬆地針對方案或其專案執行命令。

這兩個 shell 都有特定的環境變數設定，可讓您更輕鬆地使用命令列開發人員工具。 開啟其中一個 shell 之後，您可以為不同的公用程式輸入命令，而不需要知道它們的所在位置。 

|常用命令|描述|
|--|--|
|[`MSBuild`](../../msbuild/msbuild-command-line-reference.md)|建立專案或方案|
|[`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool)| 適用于 CLR 的[.NET Framework 工具](/dotnet/framework/tools/index)|
|[`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)|解譯器的[.NET Framework 工具](/dotnet/framework/tools/index)|
|[`dotnet`](/dotnet/core/tools/dotnet)|[.NET CLI 命令](/dotnet/core/tools/index)|
|[`dotnet run`](/dotnet/core/tools/dotnet-run)|[.NET CLI 命令](/dotnet/core/tools/index)|
|[`CL`](/cpp/build/reference/compiler-command-line-syntax)|C/c + + 編譯工具|
|[`NMAKE`](/cpp/build/reference/running-nmake)|C/c + + 編譯工具|
|[`LIB`](/cpp/build/reference/lib-reference)| C/c + + 組建工具|
|[`DUMPBIN`](/cpp/build/reference/dumpbin-reference)| C/c + + 組建工具|


## <a name="start-in-visual-studio"></a>從 Visual Studio 開始

請遵循下列步驟，從 Visual Studio 內開啟開發人員命令提示字元或開發人員 PowerShell：

1. 開啟 Visual Studio。

1. 在功能表列上，選擇 [**工具**  >  **命令列**  >  **開發人員命令提示字元**] 或 [**開發人員 PowerShell**]。

   ![Visual Studio 中的命令提示字元功能表項目](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="start-from-windows-menu"></a>從 Windows] 功能表啟動

啟動 shell 的另一種方式是從 [開始] 功能表。 您可能會有多個命令提示字元，視 Visual Studio 版本以及您已安裝的任何其他 sdk 和工作負載而定。 

### <a name="windows-10"></a>Windows 10

1. 選取 [**開始**] ![ Windows 鍵盤上的標誌鍵。](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) 並將其滾動至字母 **V**。

1. 展開 [ **Visual Studio 2019** ] 資料夾。

1. 選擇適用于 vs 2019 的 **vs 2019** 或 **Developer PowerShell** 開發人員命令提示字元。

   或者，您可以在工作列的 [搜尋] 方塊中，開始輸入 shell 的名稱，然後選擇您想要的結果，因為結果清單會開始顯示搜尋相符專案。

   ![顯示 Windows 10 上搜尋行為的動畫 gif](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. 按下 Windows 標誌鍵 ![鍵盤上的 Windows 標誌鍵](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) 前往 [開始] 畫面。 位於您的鍵盤上，作為範例。

1. 在 [**開始**] 畫面上，按下 **Ctrl** + **Tab** 以開啟 [**應用程式**] 清單，然後按 **V**。這會顯示包含所有已安裝 Visual Studio 命令提示字元的清單。

1. 選擇適用于 vs 2019 的 **vs 2019** 或 **Developer PowerShell** 開發人員命令提示字元。

### <a name="windows-7"></a>Windows 7

1. 選擇 [ **開始** ]，然後展開 [ **所有程式**]。

1. 選擇適用于 vs 2019 的 **Visual Studio 2019**  >  **Visual Studio Tools**  >  **開發人員命令提示字元** 或 **vs 2019 的開發人員 PowerShell**。

   ![已反白顯示命令提示字元 Windows 7 [開始] 功能表](./media/developer-command-prompt-for-vs/windows-7-menu.png)

如果您已安裝其他 sdk （例如[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)或[舊版](https://developer.microsoft.com/windows/downloads/sdk-archive)），您可能會看到其他的命令提示字元。 查看個別工具的文件以判斷要使用哪個版本的命令提示字元。

## <a name="start-from-file-browser"></a>從檔案瀏覽器啟動 

您已安裝之 shell 的快捷方式通常會放在 Visual Studio 的 [**開始功能表**] 資料夾中，例如在 *%ProgramData%\Microsoft\ Windows \Start Menu\Programs\ Visual Studio 2019 \ Visual Studio Tools* 中。 但是如果搜尋命令提示字元並不會產生預期的結果，您可以嘗試手動找出電腦上的檔案。

### <a name="developer-command-prompt"></a>開發人員命令提示字元

搜尋 *VsDevCmd.bat* 的命令提示字元檔案名，或移至 Visual Studio 的 [工具] 資料夾，例如 *% ProgramFiles (x86) % \ Microsoft Visual Studio \ 2019 \ Community \Common7\Tools* (路徑變更（根據 Visual Studio 版本、版本和安裝位置) ）。

當您找到命令提示字元檔案之後，請在一般的命令提示字元視窗中輸入下列命令來開啟它：

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

或者，在 [Windows **執行**] 對話方塊中輸入下列命令：

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> 您必須編輯路徑以符合您的 Visual Studio 安裝。

### <a name="developer-powershell"></a>開發人員 PowerShell

搜尋名為 *Launch-VsDevShell.ps1* 的 PowerShell 腳本檔案，或移至 Visual Studio 的 Tools 資料夾，例如 *% ProgramFiles (x86) % \ Microsoft Visual Studio \ 2019 \ Community \Common7\Tools*。  (路徑會根據您的 Visual Studio 版本、版本和安裝位置而變更。當您找到 PowerShell 檔案之後，請 ) 在 Windows PowerShell 或 PowerShell 6 提示字元中輸入下列命令來執行此動作：

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

根據預設，啟動的開發人員 PowerShell 是針對 *Launch-VsDevShell.ps1* 檔案所在的安裝路徑設定 Visual Studio 安裝。

> [!TIP]
> 必須設定 [執行原則](/powershell/module/microsoft.powershell.core/about/about_execution_policies) ，才能執行 cmdlet 。

## <a name="see-also"></a>另請參閱

- [Windows 終端機](/windows/terminal/)
- [.NET Framework 工具](/dotnet/framework/tools/index)
- [從命令列使用 Microsoft c + + 工具組](/cpp/build/building-on-the-command-line)
- [Visual Studio Code 使用者](https://code.visualstudio.com/docs/cpp/config-msvc#:~:text=To%20open%20the%20Developer%20Command,item%20to%20open%20the%20prompt.)
