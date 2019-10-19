---
title: Shell 命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ad49aadf6be56fb330b883050e6a6ff893cf054a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663547"
---
# <a name="shell-command"></a>Shell 命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 內啟動可執行程式。

## <a name="syntax"></a>語法

```
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>引數
 `path` 必要項。 要執行之檔案或要開啟之文件的路徑和檔案名稱。 如果指定的檔案不在 PATH 環境變數的其中一個目錄中，則需要完整路徑。

 `args` 選擇項。 任何要傳遞給已叫用程式的引數。

## <a name="switches"></a>參數
 /commandwindow [或]/command [或]/c [or]/cmd Optional。 指定可執行檔的輸出會顯示在 [命令]  視窗中。

 /dir： `folder` [或]/d： `folder` 選擇性。 指定要在執行程式時設定的工作目錄。

 /outputwindow [或]/output [或]/out [或]/o 選擇性。 指定可執行檔的輸出會顯示在 [輸出]  視窗中。

## <a name="remarks"></a>備註
 必須緊接在 `Tools.Shell` 後面指定 /dir /o /c 參數。 在可執行檔名稱後面指定的任何內容都是當成命令列引數傳遞給它。

 預先定義的別名 `Shell` 可以用來取代 `Tools.Shell`。

> [!CAUTION]
> 如果 `path` 引數提供目錄路徑和檔案名稱，您應該使用常值引號 (""") 括住整個路徑名稱，如下所述：

```
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

 `Shell` 處理器會將每組三個雙引號 (""") 解譯為單一雙引號字元。 因此，上述範例實際會將下列路徑字串傳遞給 `Shell` 命令：

```
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> 如果您不要使用常值引號 (""") 括住路徑字串，則 Windows 只會使用字串部分，最多到第一個空格。 例如，如果上述路徑字串未正確地加上引號，則 Windows 會尋找名為 "Program" 且位在 C:\ 根目錄的檔案。 如果 C:\Program.exe 可執行檔實際可用 (即使是透過不正當竄改所安裝的可執行檔)，則 Windows 會嘗試執行該程式來取代所需 "c:\Program Files\SomeFile.exe" 程式。

## <a name="example"></a>範例
 下列命令會使用 xcopy.exe 將 `MyText.txt` 檔案複製至 `Text` 資料夾。 xcopy.exe 的輸出會同時顯示在 [命令視窗]  和 [輸出]  視窗中。

```
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>另請參閱
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)[命令視窗](../../ide/reference/command-window.md)[輸出視窗](../../ide/reference/output-window.md)[尋找/命令框](../../ide/find-command-box.md) [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
