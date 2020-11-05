---
title: msi-安裝
description: 適用于 msiexec 的 devinit 工具。
ms.date: 10/13/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 98667c602272f22e7803647a688ee75d6c6cbd70
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402247"
---
# <a name="msi-install"></a>msi-安裝

此 `msi-install` 工具是用來 `.msi` 使用 [msiexec](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)安裝封裝檔案格式。

## <a name="usage"></a>使用方式

如果 `input` 省略或空白，則工具會輸出錯誤。

| 名稱                                         | 類型   | 必要 | 值                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **評論**                                 | 字串 | No       | 選擇性批註屬性。 未使用。                                             |
| [**輸入**](#input)                          | 字串 | 是      | 要安裝的 `msi`。 如需詳細資料，請參閱下列 [輸入](#input) 。                      |
| [**additionalOptions**](#additional-options) | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。                  |

### <a name="input"></a>輸入

輸入屬性是用來指定將安裝之檔案的路徑或 URL `.msi` 。 如果的路徑不 `.msi` 正確，或 URL 未直接指向 a，則 `.msi` `msi-install` 會注意到無法開啟安裝套件。

### <a name="additional-options"></a>其他選項

您可以將其他設定選項傳入作為 additionalOptions 的值。 這些引數直接傳遞至所使用的引數 `msiexec` ，並在 `msiexec` [檔](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)中定義。

### <a name="built-in-options"></a>內建選項

Msi 安裝工具會設定一些 `msiexec` 命令列引數，以確保 msi 可以執行無周邊。 以下列出這些引數，您可以在檔中找到這些引數的相關檔 `msiexec` [ ](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)。

| 名稱          | 描述                                                                                                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /i            | 執行正常安裝                                                                                                                                                                    | 
| /quiet        | 指定無需使用者互動的無訊息模式                                                                                                                                        | 
| /qn           | 指定在安裝過程中沒有 UI                                                                                                                                           | 
| /passive      | 指定安裝只顯示進度列的自動模式                                                                                                                    | 
| /l * V          | 開啟記錄，並將所有資訊（包括詳細資訊）記錄到 `devinit.log` 電腦本機暫存資料夾中的檔案。 如果工具失敗，則會顯示記錄檔路徑。      | 
| /norestart    | 在安裝完成後停止機器重新開機，但如果需要重新開機，則會傳回3010結束代碼                                                                  | 

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-4.0",
    "run": [
        {
            "comments": "Installs the 7-Zip MSI",
            "tool": "msi-install",
            "input": "https://www.7-zip.org/a/7z1900.msi"
        }
    ]
}
```
