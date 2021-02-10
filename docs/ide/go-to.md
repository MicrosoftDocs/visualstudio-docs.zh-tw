---
title: 移至檔案、移至符號、移至行
description: 瞭解如何在 Visual Studio 中移至命令，以及如何使用它們來執行程式碼的焦點搜尋。
ms.custom: SEO-VS-2020
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 257db632c095027d9fa4be667a30e809ecb2fff4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946614"
---
# <a name="find-code-using-go-to-commands"></a>使用移至命令來尋找程式碼

Visual Studio 的 [移至] 命令會對程式碼執行焦點式搜尋，協助您快速找出指定的項目。 您可以透過簡潔的整合介面，移至特定行、類型、符號、檔案和成員。

## <a name="how-to-use-it"></a>用法

輸入 | 函式
------------ | ---
**鍵盤** | 按下 **ctrl** + **T** 或 **ctrl** + **，**
**滑鼠** | 選取 [**編輯**  >  **移** 至  >  **全部**]

在您程式碼編輯器的右上方會顯示一個小視窗。

![[移至全部] 視窗](media/go-to-all.png)

當您在文字方塊中鍵入時，結果會出現在文字方塊下方的下拉式清單中。 若要移至項目，請在清單中選擇它。

![[巡覽至] 視窗](../ide/media/vside_navigatetowindow.png)

您也可以輸入問號 (**?**) 以取得其他說明。

![移至全部說明](media/go-to-all-help.png)

## <a name="filtered-searches"></a>篩選的搜尋

根據預設，會在所有方案項目中搜尋指定的項目。 不過，您可以在搜尋詞彙前面引用特定字元，以將程式碼搜尋限制為特定項目類型。 您也可以選擇 [ **移至** ] 對話方塊工具列上的按鈕，快速變更搜尋篩選。 變更類型篩選的按鈕是在左邊，變更搜尋範圍的按鈕則是在右邊。

![移至成員](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>篩選至特定類型的程式碼項目

若要縮小搜尋範圍至特定類型的程式碼項目，您可以在 [搜尋] 方塊中指定前置詞，或選取五個篩選條件圖示的其中一個：

前置詞 | 圖示 | 快速鍵 | Description
:-: | - | - | -
:| ![行圖示](media/gotoall-line-icon.png) | **Ctrl** +**G** | 移至指定的行號
f| ![檔案圖示](media/gotoall-files-icon.png) | **Ctrl** +**1**、 **Ctrl** + **F** | 移至指定的檔案
r| ![最近使用的檔案圖示](media/gotoall-recent-files-icon.png) | **Ctrl** +**1**、 **Ctrl** + **R** | 移至指定的最近瀏覽檔案
t| ![類型圖示](media/gotoall-types-icon.png) | **Ctrl** +**1**、 **Ctrl** + **T** | 移至指定的類型
m| ![成員圖示](media/gotoall-members-icon.png) | **Ctrl** +**1**、 **Ctrl** + **M** | 移至指定的成員
\#| ![符號圖示](media/gotoall-symbols-icon.png) | **Ctrl** +**1**、 **Ctrl** + **S** | 移至指定的符號

### <a name="filter-to-a-specific-location"></a>篩選至特定位置

若要將搜尋範圍縮小為特定位置，請選取兩個文件圖示的其中一個：

圖示 | Description
---- | ---
![目前的文件](media/gotoall_currentdocument.png) | 僅搜尋目前文件
![外部文件](media/gotoall_external.png) | 除了專案/方案中的文件之外，還會搜尋外部文件

## <a name="camel-casing"></a>駝峰式命名法的大小寫

如果您在程式碼中使用 [camel casing](https://en.wikipedia.org/wiki/Camel_case) (駝峰式命名法)，則只要輸入程式碼項目名稱的大寫字母，就可以更快速地找到程式碼項目。 例如，如果您的程式碼有一個稱為的型 `CredentialViewModel` **別**，您可以選擇 **類型** 篩選 (t) ，然後只在 `CVM` [移至] 對話方塊中輸入名稱 () 的大寫字母，以縮小搜尋範圍。 如果您的程式碼名稱很長，則這個功能十分有用。

![[巡覽至] 視窗 - 使用大寫搜尋](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>設定

選取齒輪圖示 ![齒輪圖示](media/gotoall_gear.png) 可讓您變更這項功能的運作方式：

設定 | Description
------- | ---
使用預覽索引標籤 | 在 IDE 的預覽索引標籤中立即顯示選取的項目
顯示詳細資料 | 在視窗中顯示文件註解中的專案、檔案、行和摘要資訊
置中視窗 | 將此視窗移至程式碼編輯器的正上方，而不是右上方

## <a name="see-also"></a>另請參閱

- [巡覽程式碼](../ide/navigating-code.md)
- [移至行對話方塊](../ide/reference/go-to-line.md)
- [移至定義和查看定義](../ide/go-to-and-peek-definition.md)
