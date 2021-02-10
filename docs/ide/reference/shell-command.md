---
title: Shell 命令
description: 深入瞭解 Shell 命令，以及它如何從 Visual Studio 內啟動可執行程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6b520d3bedf31bc09dc0cf48e86777872176e2e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957617"
---
# <a name="shell-command"></a>Shell 命令
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 內啟動可執行程式。

## <a name="syntax"></a>語法

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>引數
`path`

必要。 要執行之檔案或要開啟之文件的路徑和檔案名稱。 如果指定的檔案不在 PATH 環境變數的其中一個目錄中，則需要完整路徑。

`args`

選擇性。 任何要傳遞給已叫用程式的引數。

## <a name="switches"></a>交換器
/commandwindow [或] /command [或] /c [或] /cmd

選擇性。 指定可執行檔的輸出會顯示在 [命令] 視窗中。

/dir:`folder` [或] /d: `folder`

選擇性。 指定要在執行程式時設定的工作目錄。

/outputwindow [或] /output [或] /out [或] /o

選擇性。 指定可執行檔的輸出會顯示在 [輸出] 視窗中。

## <a name="remarks"></a>備註
必須緊接在 `Tools.Shell` 後面指定 /dir /o /c 參數。 在可執行檔名稱後面指定的任何內容都是當成命令列引數傳遞給它。

預先定義的別名 `Shell` 可以用來取代 `Tools.Shell`。

> [!CAUTION]
> 如果 `path` 引數提供目錄路徑和檔案名稱，您應該使用常值引號 (""") 括住整個路徑名稱，如下所述：

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

`Shell` 處理器會將每組三個雙引號 (""") 解譯為單一雙引號字元。 因此，上述範例實際會將下列路徑字串傳遞給 `Shell` 命令：

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> 如果您不要使用常值引號 (""") 括住路徑字串，則 Windows 只會使用字串部分，最多到第一個空格。 例如，如果上述路徑字串未正確地加上引號，則 Windows 會尋找名為 "Program" 且位在 C:\ 根目錄的檔案。 如果 C:\Program.exe 可執行檔實際可用 (即使是透過不正當竄改所安裝的可執行檔)，則 Windows 會嘗試執行該程式來取代所需 "c:\Program Files\SomeFile.exe" 程式。

## <a name="example"></a>範例
下列命令會使用 xcopy.exe 將 `MyText.txt` 檔案複製至 `Text` 資料夾。 xcopy.exe 的輸出會同時顯示在 [命令視窗] 和 [輸出] 視窗中。

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [輸出視窗](../../ide/reference/output-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
