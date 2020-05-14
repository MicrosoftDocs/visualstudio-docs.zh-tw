---
title: 尋找命令方塊
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b50c0503d313d4482d8370071220dbf1403d9a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591524"
---
# <a name="findcommand-box"></a>尋找/命令方塊

您可以從 [尋找/命令]**** 方塊中搜尋文字，並執行 Visual Studio 命令。 [尋找/命令]**** 方塊仍然是工具列控制項，但不再預設為可見。 您可以選擇 [標準]**** 工具列上的 [新增或移除按鈕]****，然後選擇 [尋找]****，以顯示 [尋找/命令]**** 方塊。

要運行命令[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，請用大於 （**>**） 的符號來為命令先面。

[尋找/命令]**** 方塊會保留輸入的最後 20 個項目，並以下拉式清單予以顯示。 您可以通過選擇**方向鍵**來瀏覽清單。

![尋找&#47;命令方塊](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>搜尋文字

預設情況下，當您在 **"查找/命令**"框中指定文本，然後選擇 **"輸入**鍵"時，Visual Studio 將使用"**在檔中查找"** 對話方塊中指定的選項搜索當前文檔或工具視窗。 如需詳細資訊，請參閱[尋找和取代文字](../ide/finding-and-replacing-text.md)。

## <a name="entering-commands"></a>輸入命令

若要使用 [尋找/命令]**** 方塊來發出單一 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令或別名，而不是搜尋文字，請在命令前面加上大於 (**>**) 符號。 例如：

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

或者，您還可以使用**命令**視窗輸入和執行單個或多個命令。 某些命令或別名可以單獨輸入並執行；有些命令或別名的語法則需要有引數。 有關具有參數的命令清單，請參閱[視覺化工作室命令](../ide/reference/visual-studio-commands.md)。

## <a name="escape-characters"></a>逸出字元

命令中的加斯特**^**（ ） 字元意味著緊隨它之後的字元被從字面上解釋，而不是作為控制字元。 這可用來在參數或參數的值中嵌入一般引號 (**"**)、空格、前置斜線、插入號或任何其他常值字元，但參數名稱除外。 例如：

```
>Edit.Find ^^t /regex
```

無論插入號位於引號內部或外部，功能都相同。 如果插入號是該程式行的最後一個字元，則會將其忽略。

## <a name="see-also"></a>另請參閱

- [命令視窗](../ide/reference/command-window.md)
- [查找和替換文本](../ide/finding-and-replacing-text.md)
