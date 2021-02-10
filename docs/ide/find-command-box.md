---
title: 尋找命令方塊
description: 瞭解 [尋找/命令] 方塊，以及如何使用它來搜尋文字並執行 Visual Studio 命令。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e650acd4dabec3dd3c657a91e4258b1678918e61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945665"
---
# <a name="findcommand-box"></a>尋找/命令方塊

您可以從 [尋找/命令] 方塊中搜尋文字，並執行 Visual Studio 命令。 [尋找/命令] 方塊仍然是工具列控制項，但不再預設為可見。 您可以選擇 [標準] 工具列上的 [新增或移除按鈕]，然後選擇 [尋找]，以顯示 [尋找/命令] 方塊。

若要執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令，請在其前面加上大於 (**>**) 號。

[尋找/命令] 方塊會保留輸入的最後 20 個項目，並以下拉式清單予以顯示。 您可以選擇 **方向鍵** 來瀏覽清單。

![尋找&#47;命令方塊](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>搜尋文字

依預設，當您在 [ **尋找/命令** ] 方塊中指定文字，然後選擇 **Enter** 鍵時，Visual Studio 會使用 [檔案 **中尋找** ] 對話方塊中所指定的選項來搜尋目前的檔或工具視窗。 如需詳細資訊，請參閱[尋找和取代文字](../ide/finding-and-replacing-text.md)。

## <a name="entering-commands"></a>輸入命令

若要使用 [尋找/命令] 方塊來發出單一 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令或別名，而不是搜尋文字，請在命令前面加上大於 (**>**) 符號。 例如：

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

或者，您也可以使用 **命令** 視窗來輸入並執行單一或多個命令。 某些命令或別名可以單獨輸入並執行；有些命令或別名的語法則需要有引數。 如需包含引數的命令清單，請參閱 [Visual Studio 命令](../ide/reference/visual-studio-commands.md)。

## <a name="escape-characters"></a>逸出字元

命令中的插入號 (**^**) 字元，表示緊接在它後面的字元會以字面方式解讀，而不是控制字元。 這可用來在參數或參數的值中嵌入一般引號 (**"**)、空格、前置斜線、插入號或任何其他常值字元，但參數名稱除外。 例如：

```
>Edit.Find ^^t /regex
```

無論插入號位於引號內部或外部，功能都相同。 如果插入號是該程式行的最後一個字元，則會將其忽略。

## <a name="see-also"></a>另請參閱

- [命令視窗](../ide/reference/command-window.md)
- [尋找和取代文字](../ide/finding-and-replacing-text.md)
