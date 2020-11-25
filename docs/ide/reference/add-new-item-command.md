---
title: 加入新項目命令
description: 瞭解如何使用 [加入新專案] 命令，將新的方案專案或框架加入至目前的方案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac07b374ef08a963426b9bfd44f101a8863f04c8
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871284"
---
# <a name="add-new-item-command"></a>加入新項目命令
將新的方案項目，例如 .htm、.css、.txt 或框架組新增至目前的方案，並開啟它。

## <a name="syntax"></a>語法

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>引數
`filename`\
選擇性。 要新增至方案之項目的路徑和檔名。

## <a name="switches"></a>交換器
/t: `templatename`\
選擇性。 指定要建立之檔案的類型。 如果未指定任何範本名稱，則預設會建立文字檔。

/t:`templatename` 引數語法會鏡像 [Add New Solution Item] (新增方案項目) 對話方塊中所找到的資訊。 您必須輸入後接檔案類型的完整分類，且使用反斜線 (`\`) 隔開分類名稱與檔案類型，並使用引號括住整個字串。

例如，若要建立新的文字檔，您將針對 /t:`templatename` 引數輸入下列項目。

```cmd
/t:"General\Style Sheet"
```

/e: `editorname`\
選擇性。 將用來開啟檔案之編輯器的名稱。 如果指定此引數，但未提供編輯器名稱，則會出現 [開啟方式] 對話方塊。

/e:`editorname` 引數語法會使用出現在 [開啟方式] 對話方塊並使用引號括住的編輯器名稱。

例如，若要使用原始程式碼編輯器開啟樣式表，您將針對 /e:`editorname` 引數輸入下列項目。

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>範例
此範例會將新的方案項目 MyHTMLpg 新增至目前方案。

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
