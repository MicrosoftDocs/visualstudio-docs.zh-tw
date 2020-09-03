---
title: 程式碼片段
description: 如何使用程式碼片段在 Visual Studio for Mac 中有效率進行程式設計
author: cobey
ms.author: cobey
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 1dacc935549d738ff1b5e84c3ac4420c343155fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68787691"
---
# <a name="code-snippets"></a>程式碼片段

程式碼片段通常稱為「程式碼範本」__，適用於具效率的程式設計，因為它們允許插入和編輯預先撰寫的程式碼區塊。 使用程式碼片段可便於迅速新增常見模式，或甚至在您是開發人員但不確定語法時學習新的模式。 有針對 C#、F#、HTML、XML、Python 和 Razor 提供的範本。

本節說明如何在程式碼中建立、插入和使用程式碼片段。

## <a name="inserting-a-snippet"></a>插入程式碼片段

有一些不同的方式可以新增程式碼片段，而下面說明其中一部分：

- **定位點擴充** &ndash; 開始輸入範本名稱，從清單中選取它，然後按 **Tab**、**Tab** 來予以新增：

  ![程式碼中的定位點擴充](media/source-editor-image13.png)

- **工具箱** &ndash; 使用工具箱板來顯示所有程式碼片段的清單。 將任何範本從工具箱拖曳至原始程式碼中的正確位置：

  [![工具箱中的程式碼片段](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **插入範本命令** &ndash; 目前未設定任何用於插入範本的預設按鍵繫結關係。 若要建立一個，請流覽至 **Visual Studio > 喜好設定 > 按鍵** 系結，並搜尋 `template` 。 這允許將想要的按鍵繫結關係新增至 [編輯繫結] 欄位，然後按一下 [套用]****：

  ![插入範本命令](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>建立新範本

雖然您可以使用和編輯多個各種語言的現有範本，但也可以新增範本，方法是巡覽至 [Visual Studio] > [喜好設定] > [文字編輯器] > [程式碼片段]****：

![插入新範本](media/source-editor-image12.png)

按 [新增]**** 或 [編輯]**** 按鈕以建立或編輯程式碼片段。

## <a name="keywords-in-code-snippets"></a>程式碼片段中的關鍵字

將程式碼片段插入編輯器中之後，所有已定義的關鍵字都會以醒目提示方式顯示，您可以藉由使用 Tab 鍵在它們之間移動來編輯它們。 關鍵字的作用就像程式碼片段中的「變數」，若要定義關鍵字，請在關鍵字名稱的前後加上一個貨幣符號 `$`。 

以下顯示 [編輯範本]**** 視窗，其中正在編輯內建的 `prop` 程式碼片段。 此程式碼片段包含兩個關鍵字 &ndash; `$type$` ，且 `$name$` &ndash; 可以設定進一步的屬性 (例如視窗右邊的預設值和工具提示) ：

![[編輯範本] 視窗](media/source-editor-image12z.png)

下列欄位可用來定義程式碼片段：

- **捷徑** &ndash; 使用者所輸入來插入程式碼片段的文字。
- **群組** &ndash; 程式碼片段會使用此值在程式碼片段內容功能表中一起組成群組。
- **描述** &ndash; 程式碼片段用途的說明。
- **MIME** &ndash; 控制可用程式碼片段的檔案類型。
- **Is expandable template \(是可擴充的範本\) ** &ndash; 請務必選取此選項，如此才可藉由輸入捷徑，在游標位置插入程式碼片段。
- **Is surround with template \(是範圍陳述式範本\) ** &ndash; 若要在編輯器的 [範圍陳述式]**** 內容功能表中列出此捷徑，請選取此選項。
- **範本文字** &ndash; 將插入到編輯器中的實際程式碼片段。 定義關鍵字預留位置時，可藉由以貨幣符號括住語彙基元來定義，例如： `$type$`.
- **關鍵字屬性面板** &ndash; 在視窗右側，使用頂端的下拉式清單來選擇關鍵字 (例如 `type`)，然後編輯預設值和工具提示等屬性。

## <a name="using-keywords-in-the-editor"></a>在編輯器中使用關鍵字

若要使用程式碼片段搭配關鍵字 (例如上方所定義的關鍵字)，請輸入捷徑並按兩次 **Tab** 鍵，就會在游標位置插入程式碼片段內容：

![顯示關鍵字的已插入程式碼片段](media/source-editor-image12a.png)

按 **Tab** 鍵以在 `object` 與 `MyProperty` 之間移動，以自訂您類別的程式碼片段。

關鍵字可以在程式碼片段中重複出現，例如這個 `for` 範例，請注意 `$i$` 關鍵字出現 3 次：

![含有重複關鍵字的程式碼片段](media/source-editor-image12b.png)

在編輯器中使用時，**Tab** 鍵會在第一個 `i` 與 `max` 之間切換。 如果您將 `i` 取代成不同的變數名稱，三個執行個體都會更新：

![顯示多個關鍵字的已插入程式碼片段](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>保留關鍵字

您可以在程式碼片段中使用兩個保留關鍵字：

- `$selected$` &ndash; 如果已為程式碼片段選取 [Is surround with template] \(是範圍陳述式範本\)****，就會以選擇程式碼片段時在編輯器中以醒目提示方式顯示的文字取代此關鍵字。
- `$end$`&ndash;當使用者完成編輯程式碼片段中的關鍵字時，游標將放置於關鍵字的位置 `$end$` 。

上一節中的 `for` 程式碼片段即是這兩個保留關鍵字的範例。

## <a name="see-also"></a>另請參閱

- [程式碼片段 (Windows 上的 Visual Studio)](/visualstudio/ide/code-snippets)
