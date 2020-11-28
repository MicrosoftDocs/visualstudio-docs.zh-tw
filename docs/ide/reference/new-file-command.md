---
title: 新增檔案命令
description: 瞭解新的檔案命令，以及它如何建立新的檔案並加以開啟。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c800ce0ed130ed78f9537584c95a29a717f405fa
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304104"
---
# <a name="new-file-command"></a>新增檔案命令
建立新的檔案並開啟它。 檔案會顯示其他檔案資料夾之下。

## <a name="syntax"></a>語法

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>引數
`filename`

選擇性。 檔案名稱。 如果未提供名稱，會提供預設名稱。 如果未列出任何範本名稱，則會建立文字檔。

## <a name="switches"></a>交換器
/t:`templatename`\
選擇性。 指定要建立之檔案的類型。

/t:`templatename` 引數語法會鏡像 [新增檔案] 對話方塊中所找到的資訊。 輸入分類名稱，緊接著一個反斜線 (`\`) 和範本名稱，並且以引號括住整個字串。

例如，若要建立新的 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 原始程式檔，您將針對 /t:`templatename` 引數輸入下列項目。

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

上述範例指出 C++ 檔案範本位於 [新增檔案] 對話方塊的 Visual C++ 分類。

/e:`editorname`\
選擇性。 將用來開啟檔案之編輯器的名稱。 如果指定此引數，但未提供編輯器名稱，則會出現 [開啟方式] 對話方塊。

/e:`editorname` 引數語法會使用出現在 [開啟方式] 對話方塊並使用引號括住的編輯器名稱。

例如，若要使用原始程式碼編輯器開啟檔案，您將針對 /e:`editorname` 引數輸入下列項目。

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>範例
這個範例會建立新的網頁 "test1.htm"，並在原始碼程式碼編輯器中開啟。

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [即時運算視窗](../../ide/reference/immediate-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
