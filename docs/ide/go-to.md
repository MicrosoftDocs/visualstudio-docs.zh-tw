---
title: 移至檔案、移至符號、移至行
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 00ec7361304d76d33264b98b45cf373bc5fc9f51
ms.sourcegitcommit: 4c60bcfa2281bcc1a28def6a8e02433d2c905be6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42627181"
---
# <a name="find-code-using-go-to-commands"></a>使用移至命令來尋找程式碼

Visual Studio 的 [移至] 命令會對程式碼執行焦點式搜尋，協助您快速找出指定的項目。 您可以透過簡潔的整合介面，移至特定行、類型、符號、檔案和成員。 Visual Studio 2017 及更新版本有提供這項功能，

## <a name="how-to-use-it"></a>如何使用

輸入        | 功能
------------ | ---
**鍵盤** | 按 **Ctrl**+**T** 或 **Ctrl**+**,**
**滑鼠**    | 選取 [編輯] > [移至] > [Go To All (移至全部)]

在您程式碼編輯器的右上方會顯示一個小視窗。

![[移至全部] 視窗](media/go-to-all.png)

當您在文字方塊中鍵入時，結果會出現在文字方塊下方的下拉式清單中。 若要移至項目，請在清單中選擇它。

![[巡覽至] 視窗](../ide/media/vside_navigatetowindow.png)

您也可以輸入問號 (**?**) 以取得其他說明。

![移至全部說明](media/go-to-all-help.png)

## <a name="filtered-searches"></a>篩選的搜尋

根據預設，會在所有方案項目中搜尋指定的項目。 不過，您可以在搜尋詞彙前面引用特定字元，以將程式碼搜尋限制為特定項目類型。 您也可以選擇 [移至] 對話方塊工具列上的按鈕，快速變更搜尋篩選。 變更類型篩選的按鈕是在左邊，變更搜尋範圍的按鈕則是在右邊。

![移至成員](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>篩選至特定類型的程式碼項目

若要縮小搜尋範圍至特定類型的程式碼項目，您可以在 [搜尋] 方塊中指定前置詞，或選取五個篩選條件圖示的其中一個：

前置詞 | 圖示 | 快速鍵 | 描述
:-: | - | - | -
:| ![行圖示](media/gotoall-line-icon.png) | **Ctrl**+**G**         | 移至指定的行號
f| ![檔案圖示](media/gotoall-files-icon.png) | **Ctrl**+**1**、**Ctrl**+**F** | 移至指定的檔案
r| ![最近使用的檔案圖示](media/gotoall-recent-files-icon.png) | **Ctrl**+**1**、**Ctrl**+**R** | 移至指定的最近瀏覽檔案
t| ![類型圖示](media/gotoall-types-icon.png) | **Ctrl**+**1**、**Ctrl**+**T** | 移至指定的類型
m| ![成員圖示](media/gotoall-members-icon.png) | **Ctrl**+**1**、**Ctrl**+**M** | 移至指定的成員
\#| ![符號圖示](media/gotoall-symbols-icon.png) | **Ctrl**+**1**、**Ctrl**+**S** | 移至指定的符號

### <a name="filter-to-a-specific-location"></a>篩選至特定位置

若要將搜尋範圍縮小為特定位置，請選取兩個文件圖示的其中一個：

圖示 | 描述
---- | ---
![目前文件](media/gotoall_currentdocument.png) | 僅搜尋目前文件
![外部文件](media/gotoall_external.png) | 除了專案/方案中的文件之外，還會搜尋外部文件

## <a name="camel-casing"></a>駝峰式命名法的大小寫

如果您在程式碼中使用 [camel casing](https://en.wikipedia.org/wiki/Camel_case) (駝峰式命名法)，則只要輸入程式碼項目名稱的大寫字母，就可以更快速地找到程式碼項目。 例如，如果您的程式碼有一個稱為 `CredentialViewModel` 的型別，則選擇 [型別] 篩選 (**t**)，並且只要在 [移至] 對話方塊中輸入名稱的大寫字母 (`CVM`)，就可以縮小搜尋範圍。 如果您的程式碼名稱很長，則這個功能十分有用。

![[巡覽至] 視窗 - 使用大寫搜尋](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>設定

選取齒輪圖示 ![齒輪圖示](media/gotoall_gear.png) 可讓您變更這項功能的運作方式：

設定 | 描述
------- | ---
使用預覽索引標籤 | 在 IDE 的預覽索引標籤中立即顯示選取的項目
顯示詳細資料    | 在視窗中顯示文件註解中的專案、檔案、行和摘要資訊
置中視窗   | 將此視窗移至程式碼編輯器的正上方，而不是右上方

## <a name="see-also"></a>另請參閱

- [巡覽程式碼](../ide/navigating-code.md)
- [移至指定行對話方塊](../ide/reference/go-to-line.md)
- [移至定義和查看定義](../ide/go-to-and-peek-definition.md)