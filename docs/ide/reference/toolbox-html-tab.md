---
title: HTML 索引標籤、工具箱
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c47ca792c25efe6ef77f3ee3a9baad61e801624
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="toolbox-html-tab"></a>HTML 索引標籤、工具箱

工具箱的 [HTML] 索引標籤提供適用於網頁和 Web Forms 的元件。 若要檢視這個索引標籤，請先在 HTML 設計工具中開啟文件進行編輯。 在 [檢視] 功能表上，按一下 [工具箱]，然後按一下 [工具箱] 的 [HTML] 索引標籤。

 若要在 [HTML] 索引標籤上建立工具的執行個體，請按兩下工具以將它新增至文件的目前插入點，或選取工具並將它拖曳至編輯介面上的想要位置。

## <a name="ui-elements"></a>UI 元素

[HTML] 索引標籤上預設會有下列工具。

**指標**

![ASP.NET Mobile 設計工具 HTML 網頁指標](../../ide/reference/media/vxpointer.gif "vxPointer")

任何 [工具箱] 索引標籤開啟時，根據預設都會選取這個工具。 它無法予以刪除。 指標可讓您將物件拖曳至 [設計] 檢視介面、重新調整其大小，以及將它們重新置入頁面或表單上。 如需詳細資訊，請參閱[工具箱](../../ide/reference/toolbox.md)。

**輸入 (按鈕)**

![HTML 網頁按鈕](../../ide/reference/media/vxbutton.gif "vxButton")

插入 `type="button"` 的 `input` 項目。 若要變更顯示的文字，請編輯 `name` 屬性。 根據預設，插入 `id="Button1"` 表示第一個按鈕、插入 `id="Button2"` 表示第二個按鈕，以此類推。

當您將 [輸入 (按鈕)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**輸入 (重設)**

![HTMLpageResetButton 螢幕擷取畫面](../../ide/reference/media/vxreset.gif "vxReset")

插入 `type="reset"` 的 `input` 項目。 若要變更顯示的文字，請編輯 `name` 屬性。 根據預設，插入 `id="Reset1"` 表示第一個重設按鈕、插入 `id="Reset2"` 表示第二個重設按鈕，以此類推。

當您將 [輸入 (重設)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**輸入 (送出)**

![HTMLpageToolbarSubmitButton 螢幕擷取畫面](../../ide/reference/media/vxsubmit.gif "vxSubmit")

插入 `type="submit"` 的 `input` 項目。 若要變更顯示的文字，請編輯 `name` 屬性。 根據預設，插入 `id="Submit1"` 表示第一個送出按鈕、插入 `id="Submit2"` 表示第二個送出按鈕，以此類推。

當您將 [輸入 (送出)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**輸入 (文字)**

![HTMLpageToolbarTextField 螢幕擷取畫面](../../ide/reference/media/vxtextfield.gif "vxTextfield")

在文件中，插入 `type="text"` 的 `input` 項目。 若要變更顯示的預設文字，請編輯 `value` 屬性。 根據預設，插入 `id="Text1"` 表示第一個文字欄位、插入 `id="Text2"` 表示第二個文字欄位，以此類推。

當您將 [輸入 (文字)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>建議驗證所有使用者輸入。 如需詳細資訊，請參閱[驗證 ASP.NET 網頁中的使用者輸入 (Razor) 網站](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)。

**輸入 (檔案)**

![HTML 網頁檔案欄位](../../ide/reference/media/vxfilefield.gif "vxFilefield")

在文件中，插入 `type="file"` 的 `input` 項目。 根據預設，插入 `id="File1"` 表示第一個檔案欄位、插入 `id="File2"` 表示第二個檔案欄位，以此類推。

當您將 [輸入 (檔案)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> 建議驗證所有使用者輸入。 如需詳細資訊，請參閱[驗證 ASP.NET 網頁中的使用者輸入 (Razor) 網站](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)。

**輸入 (密碼)**

![Visual Studio 密碼欄位](../../ide/reference/media/vxpassword.gif "vxPassword")

插入 `type="password"` 的 `input` 項目。 根據預設，插入 `id="Password1"` 表示第一個密碼欄位、插入 `id="Password2"` 表示第二個密碼欄位，以此類推。

當您將 [輸入 (密碼)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> 如果您的應用程式傳輸使用者名稱和密碼，您應該設定網站使用安全通訊端層 (SSL) 來加密傳輸。 如需詳細資訊，請參閱 [IIS Operations Guide](http://go.microsoft.com/fwlink/?linkid=47856) (IIS 作業手冊) 中的 "Securing Connections with SSL" (保護與 SSL 的連線)。 此外，建議驗證所有使用者輸入。 如需詳細資訊，請參閱[驗證 ASP.NET 網頁中的使用者輸入 (Razor) 網站](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)。

**輸入 (核取方塊)**

![HTML 網頁工具箱核取方塊選項](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")

插入 `type="checkbox"` 的 `input` 項目。 若要變更顯示的文字，請編輯 `name` 屬性。 根據預設，插入 `id="Checkbox1"` 表示第一個核取方塊、插入 `id="Checkbox2"` 表示第二個核取方塊，以此類推。

當您將 [輸入 (核取方塊)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**輸入 (選項按鈕)**

![VisualStudioHTMLpageRadioButton 螢幕擷取畫面](../../ide/reference/media/vxradio.gif "vxRadio")

插入 `type="radio"` 的 `input` 項目。 若要變更顯示的文字，請編輯 `name` 屬性。 根據預設，插入 `id="Radio1"` 表示第一個選項按鈕、插入 `id="Radio2"` 表示第二個選項按鈕，以此類推。

當您將 [輸入 (選項按鈕)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<input id="Radio1" type="radio" name="Radio1">
```

**輸入 (隱藏)**

![HTML 網頁隱藏項目](../../ide/reference/media/vxhidden.gif "vxhidden")

插入 `type="hidden"` 的 `input` 項目。 根據預設，插入 `id="Hidden1"` 表示第一個隱藏欄位、插入 `id="Hidden2"` 表示第二個隱藏欄位，以此類推。

當您將 [輸入 (隱藏)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**文字區域**

![HTML 網頁工具列文字區域](../../ide/reference/media/vxtextarea.gif "vxTextarea")

插入 `textarea` 項目。 您可以重新調整文字區域，或使用其捲軸來檢視超出顯示區域的文字。 若要變更顯示的預設文字，請編輯 `value` 屬性。 根據預設，插入 `id="textarea1"` 表示第一個文字區域、插入 `id=" textarea 2"` 表示第二個文字區域，以此類推。

當您將 [文字區域] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> 建議驗證所有使用者輸入。 如需詳細資訊，請參閱[驗證 ASP.NET 網頁中的使用者輸入 (Razor) 網站](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)。

**資料表**

![HTMLpageToolbarTable 螢幕擷取畫面](../../ide/reference/media/vxtable.gif "vxTable")

插入 `table` 項目。

當您將 [資料表] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**影像**

![HTML 網頁影像項目](../../ide/reference/media/vximage.gif "vxImage")

插入 `img` 項目。 編輯這個項目來指定其 `src` 和其 `alt` 文字。

當您將 [影像] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<img alt="" src="">
```

**選取**

![HTML 網頁工具箱下拉式清單](../../ide/reference/media/vxdropdown.gif "vxDropdown")

插入下拉式清單 `select` 項目 (不使用 `size` 屬性)。 根據預設，插入 `id="select1"` 表示第一個清單方塊、插入 `id="select2"` 表示第二個清單方塊，以此類推。

當您將 [選取] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<select id="select1" name="select1"><option selected></option></select>
```

您可以增加 size 屬性的值來建立多行 `select` 項目。

**水平尺規**

![HTML 網頁水平尺規項目](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")

插入 `hr` 項目。 若要增加線條的粗細，請編輯 `size` 屬性。

當您將 [水平尺規] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<hr width="100%" size=1>
```

**Div**

![HTML 網頁標籤](../../ide/reference/media/vxlabel.gif "vxLabel")

插入包含 `ms_positioning="FlowLayout"` 屬性的 `div` 項目。 除了寬度和高度之外，這個項目等同於「流程配置面板」。 若要格式化 `div` 項目內所含的文字，請將 `class="stylename"` 屬性新增至開始標記。

當您將 [Div] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>另請參閱

- [工具箱](../../ide/reference/toolbox.md)
