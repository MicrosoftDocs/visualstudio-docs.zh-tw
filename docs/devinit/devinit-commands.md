---
title: devinit 命令
description: 如何使用 devinit 命令來安裝元件的詳細資料。
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 1a0bd657d9612bde05a820a591c2ab2c1cfdaad3
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005528"
---
# <a name="devinit-commands"></a>devinit 命令

## <a name="init"></a>Init

```console
> devinit init
```

藉由執行目前工作目錄中檔案 [_.devinit.js_](devinit-json.md) 中指定的工具來初始化環境。  

### <a name="options-for-init"></a>Init 的選項

命令的選擇性選項 `devinit init` 。

| 引數             | 必要 | 描述                                                               |
|----------------------|----------|---------------------------------------------------------------------------|
| -f,--file           | No       | 檔案 _.devinit.js_ 的路徑。                                         |
| --錯誤-動作       | No       | 指定如何處理錯誤。 選項： [停止]、[忽略]、[繼續] (預設) 。|
| -v,--詳細資訊         | No       | 發出詳細資訊輸出。                                                      |
| -n,--試執行         | No       | 試執行。                                                                  |

## <a name="run"></a>執行

```console
> devinit run -t <toolname>
```

執行特定的工具，參數如下所示。 請參閱每個特定使用工具的 [檔](devinit-tool-list.md) 。

### <a name="options-for-run"></a>執行的選項

命令的選項 `devinit run` 。

| 引數                                  | 必要 | 描述                                                                          |
|-------------------------------------------|----------|--------------------------------------------------------------------------------------|
| -t,--工具                                 | Yes      | 必要。 工具名稱。                                                             |
| -i,--輸入                                | No       | 工具輸入值。 例如，檔案名、封裝或名稱。                           |
| --錯誤-動作                            | No       | 指定如何處理工具錯誤： [停止]、[忽略]、[繼續]。 預設值是停止。 |
| -v,--詳細資訊                              | No       | 發出詳細資訊輸出。                                                                 |
| -n,--試執行                              | No       | 試執行。                                                                             |
| --&lt;arg1 &gt; &lt; arg2 &gt; &lt; argN&gt;  | No       | 工具的其他命令列引數。                                       |

#### <a name="--file-argument"></a>--file 引數

指定檔案 _devinit.js的路徑。 如果未指定– file，我們會在下列位置中搜尋預設檔案：

* {目前的目錄} \\.devinit.js開啟
* {目前的目錄} \\ 。devinit \\.devinit.js開啟

注意：目錄或檔案名上不含前置的路徑 `.` 也會相符。

#### <a name="--error-action-argument"></a>--error-action 引數

指定工具傳回非零結束代碼時要採取的動作。 有效值為：

| 引數 | 描述                                                                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| continue | 發出錯誤給標準錯誤之後，繼續處理其他工具。 devinit.exe 結束碼為非零 (失敗) 。 此行為類似于停止錯誤動作，但仍繼續處理。 `continue` 這是 init 命令的預設錯誤（action）動作。              |
| ignore   | 發出警告給標準輸出之後，繼續處理其他工具。 DevInit 處理常式結束碼應一律為零 (成功) 。 此 `ignore` 設定會忽略所有錯誤。                                                                                                      |
| stop     | 發出錯誤給標準錯誤，並停止處理工具。 devinit.exe 結束碼為非零 (失敗) 。 這類似于 continue 錯誤動作，但處理會在第一個發生的錯誤時停止。 `stop` 這是 init 以外所有命令的預設錯誤動作。 |

#### <a name="--dry-run-switch"></a>--試執行參數

將會執行，但不會執行任何工具的 Echo 工具命令。 

#### <a name="--verbose-switch"></a>--verbose 參數

發出詳細資訊輸出給標準輸出。 如果要執行的工具支援詳細資訊選項，請將詳細資訊參數傳播至工具。

#### <a name="note-on-additional-command-line-arguments"></a>其他命令列引數的附注

使用 `<arg>` 在其值中包含空格的，必須包含一組額外的轉義引號。

```console
> devinit run -t <toolname> -<somearg> "<some value>"
```

若要將 dotnet 安裝到特定目錄 `C:\Program Files\dotnet` ：

```console
> devinit run -t require-dotnetcoresdk --"-InstallDir \"C:\Program Files\dotnet\""
```

## <a name="list"></a>清單

```console
> devinit list
```

列印所有可用工具的清單。

## <a name="show"></a>顯示

```console
> devinit show -t <toolname>
```

| 引數       | 必要 | 描述                                                                          |
|----------------|----------|--------------------------------------------------------------------------------------|
| -t,--工具      | Yes      | 必要。 工具名稱。                                                             |

列印指定工具的說明資訊。

## <a name="version"></a>版本

```console
> devinit version
```

列印 devinit 的目前版本資訊。

## <a name="help"></a>[說明]

```console
> devinit help
> devinit help list
```

列印 devinit 或特定命令的解說文字 `devinit <command>` 。
 