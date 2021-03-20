---
title: devinit 命令
description: 如何使用 devinit 命令來安裝元件的詳細資料。
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: d6c8f487fcb35fc210db57f0c8a49a2a86f909e9
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672211"
---
# <a name="devinit-commands"></a>devinit 命令

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

## <a name="init"></a>Init

```console
devinit init
```

執行 [.devinit.json](devinit-json.md) 檔案中指定的工具，以初始化環境。

### <a name="options-for-init"></a>Init 的選項

命令的選擇性選項 `devinit init` 。

| 引數             | 必要 | 描述                                                               |
|----------------------|----------|---------------------------------------------------------------------------|
| -f,--file            | No       | 檔案的路徑 `.devinit.json` 。                                         |
| --錯誤-動作       | No       | 指定如何處理錯誤。 選項： [停止]、[忽略]、[繼續] (預設) 。|
| -v,--詳細資訊         | No       | 發出詳細資訊輸出。                                                      |
| -n,--試執行         | No       | 試執行。                                                                  |

#### <a name="--file-argument"></a>--file 引數

指定檔案 _devinit.js_ 的路徑。 如果未指定--file，我們會在下列位置中搜尋預設檔案：

* {目前的目錄} \\.devinit.js開啟
* {目前的目錄} \\devinit.js開啟
* {目前的目錄} \\ 。devinit \\.devinit.js開啟
* {目前的目錄} \\ 。devinit \\devinit.js開啟
* {目前的目錄} \\devinit \\.devinit.js開啟
* {目前的目錄} \\devinit \\devinit.js開啟
* {目前的目錄} \\ 。devcontainer \\.devinit.js開啟
* {目前的目錄} \\ 。devcontainer \\devinit.js開啟

> [!NOTE]
> 如果找到多個預設檔案，則 devinit 會使用上述清單中第一個出現的檔案。

#### <a name="--error-action-argument"></a>--error-action 引數

請參閱 [下文](#options-for-run)。

#### <a name="--verbose-switch"></a>--verbose 參數

請參閱 [下文](#options-for-run)。

#### <a name="--dry-run-switch"></a>--試執行參數

請參閱 [下文](#options-for-run)。

## <a name="run"></a>執行

```console
devinit run -t <toolname>
```

執行特定的工具，參數如下所示。 請參閱每個特定使用工具的 [檔](devinit-tool-list.md) 。

### <a name="options-for-run"></a>執行的選項

命令的選項 `devinit run` 。

| 引數                                      | 必要 | 描述                                                                          |
|-----------------------------------------------|----------|--------------------------------------------------------------------------------------|
| -t,--工具                                     | Yes      | 必要。 工具名稱。                                                             |
| -i,--輸入                                    | No       | 工具輸入值。 例如，檔案名、封裝或名稱。                     |
| --錯誤-動作                                | No       | 指定如何處理工具錯誤： [停止]、[忽略]、[繼續]。 預設值是停止。 |
| -v,--詳細資訊                                  | No       | 發出詳細資訊輸出。                                                                 |
| -n,--試執行                                  | No       | 試執行。                                                                             |
| --&lt;arg1 &gt; &lt; arg2 &gt; ... &lt;argN&gt;  | No       | 工具的其他命令列引數。                                       |

#### <a name="--error-action-argument"></a>--error-action 引數

指定工具傳回非零結束代碼時要採取的動作。 有效值為：

| 引數 | 描述                                                                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| continue | 發出錯誤給標準錯誤之後，繼續處理其他工具。 devinit.exe 結束碼為非零 (失敗) 。 此行為類似于停止錯誤動作，但仍繼續處理。 `continue` 這是 init 命令的預設錯誤（action）動作。              |
| ignore   | 發出警告給標準輸出之後，繼續處理其他工具。 DevInit 處理常式結束碼應一律為零 (成功) 。 此 `ignore` 設定會忽略所有錯誤。                                                                                                      |
| stop     | 發出錯誤給標準錯誤，並停止處理工具。 devinit.exe 結束碼為非零 (失敗) 。 這類似于 continue 錯誤動作，但處理會在第一個發生的錯誤時停止。 `stop` 這是 init 以外所有命令的預設錯誤動作。 |

#### <a name="--dry-run-switch"></a>--試執行參數

要執行的 Echo 工具命令。 某些工具可能會對該工具採取進一步的動作。 

#### <a name="--verbose-switch"></a>--verbose 參數

發出詳細資訊輸出給標準輸出。 如果要執行的工具支援詳細資訊選項，請將詳細資訊參數傳播至工具。

#### <a name="--dry-run-switch"></a>--試執行參數

將會執行，但不會執行任何工具的 Echo 工具命令。

#### <a name="additional-command-line-arguments"></a>其他命令列引數

使用 `<arg>` 在其值中包含空格的，必須包含一組額外的轉義引號。

```console
devinit run -t <toolname> -<somearg> "<some value>"
```

若要將 dotnet 安裝到特定目錄 `C:\Program Files\dotnet` ：

```console
devinit run -t require-dotnetcoresdk --"-InstallDir \"C:\Program Files\dotnet\""
```

## <a name="list"></a>List

```console
devinit list
```

列印所有可用工具的清單。

## <a name="show"></a>顯示

```console
devinit show -t <toolname>
```

| 引數       | 必要 | 描述                                                                          |
|----------------|----------|--------------------------------------------------------------------------------------|
| -t,--工具      | Yes      | 必要。 工具名稱。                                                             |

列印指定工具的說明資訊。

## <a name="version"></a>版本

```console
devinit version
```

列印 devinit 的目前版本資訊。

## <a name="help"></a>Help

```console
devinit help
devinit help list
```

列印 devinit 或特定命令的解說文字 `devinit <command>` 。
 
