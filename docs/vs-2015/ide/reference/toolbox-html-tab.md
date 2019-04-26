---
title: HTML 索引標籤、工具箱 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6c0603bd820990789af0d9bbca147acd7004e1a1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097527"
---
# <a name="toolbox-html-tab"></a>HTML 索引標籤、工具箱
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

工具箱的 [HTML] 索引標籤提供適用於網頁和 Web Forms 的元件。 若要檢視這個索引標籤，請先在 HTML 設計工具中開啟文件進行編輯。 在 [檢視] 功能表上，按一下 [工具箱]，然後按一下 [工具箱] 的 [HTML] 索引標籤。  
  
 若要在 [HTML] 索引標籤上建立工具的執行個體，請按兩下工具以將它新增至文件的目前插入點，或選取工具並將它拖曳至編輯介面上的想要位置。  
  
## <a name="tasks"></a>工作  
  
- [如何：Manage the Toolbox Window](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) (如何：管理工具箱視窗)  
  
- [如何：Manipulate Toolbox Tabs](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db) (如何：操作工具箱索引標籤)  
  
## <a name="ui-elements"></a>UI 項目  
 [HTML] 索引標籤上預設會有下列工具。  
  
 **指標**  
 ![ASP.NET Mobile 設計工具 HTML 網頁指標](../../ide/reference/media/vxpointer.gif "vxPointer")  
  
 任何 [工具箱] 索引標籤開啟時，根據預設都會選取這個工具。 它無法予以刪除。 指標可讓您將物件拖曳至 [設計] 檢視介面、重新調整其大小，以及將它們重新置入頁面或表單上。 如需詳細資訊，請參閱[如何：Manage the Toolbox Window](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) (如何：管理工具箱視窗) 及 [How to:Manipulate Toolbox Tabs](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db) (如何：操作工具箱索引標籤)。  
  
 **輸入 (按鈕)**  
 ![HTML 網頁按鈕](../../ide/reference/media/vxbutton.gif "vxButton")  
  
 插入 `type="button"` 的 `input` 項目。 若要變更顯示的文字，請編輯 `name` 屬性。 根據預設，插入 `id="Button1"` 表示第一個按鈕、插入 `id="Button2"` 表示第二個按鈕，以此類推。  
  
 當您將 [輸入 (按鈕)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  
  
 如需詳細資訊，請參閱 [HTML Input Controls](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) (HTML Input 控制項)、[HtmlInputButton Server Control Declarative Syntax](http://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa) (HtmlInputHidden 伺服器控制項宣告式語法) 與 [NIB:HOW TO：Create Scripts and Edit Event Handlers](http://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d) (NIB：如何：建立指命碼與編輯事件處理常式)、[Button Web Server Controls Content Map](http://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf) (按鈕網頁瀏覽器控制項內容地圖)、<xref:System.Web.UI.HtmlControls.HtmlInputButton>、<xref:System.Web.UI.HtmlControls.HtmlButton> 及 <xref:System.Web.UI.WebControls.Button>。  
  
 **輸入 (重設)**  
 ![HTMLpageResetButton 螢幕擷取畫面](../../ide/reference/media/vxreset.gif "vxReset")  
  
 插入 `type="reset"` 的 `input` 項目。 若要變更顯示的文字，請編輯 `name` 屬性。 根據預設，插入 `id="Reset1"` 表示第一個重設按鈕、插入 `id="Reset2"` 表示第二個重設按鈕，以此類推。  
  
 當您將 [輸入 (重設)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  
  
 如需詳細資訊，請參閱 [HTML Input 控制項](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) \(英文\)、[HtmlInputReset 伺服器控制項宣告式語法](http://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979) \(機器翻譯\)、<xref:System.Web.UI.HtmlControls.HtmlInputButton> 與 <xref:System.Web.UI.WebControls.Button>。  
  
 **輸入 (送出)**  
 ![HTMLpageToolbarSubmitButton 螢幕擷取畫面](../../ide/reference/media/vxsubmit.gif "vxSubmit")  
  
 插入 `type="submit"` 的 `input` 項目。 若要變更顯示的文字，請編輯 `name` 屬性。 根據預設，插入 `id="Submit1"` 表示第一個送出按鈕、插入 `id="Submit2"` 表示第二個送出按鈕，以此類推。  
  
 當您將 [輸入 (送出)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  
  
 如需詳細資訊，請參閱 [HTML Input 控制項](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) \(英文\)、[HtmlInputSubmit 伺服器控制項宣告式語法](http://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2) \(機器翻譯\)、<xref:System.Web.UI.HtmlControls.HtmlInputButton> 與 <xref:System.Web.UI.WebControls.Button>。  
  
 **輸入 (文字)**  
 ![HTMLpageToolbarTextField 螢幕擷取畫面](../../ide/reference/media/vxtextfield.gif "vxTextfield")  
  
 在文件中，插入 `type="text"` 的 `input` 項目。 若要變更顯示的預設文字，請編輯 `value` 屬性。 根據預設，插入 `id="Text1"` 表示第一個文字欄位、插入 `id="Text2"` 表示第二個文字欄位，以此類推。  
  
 當您將 [輸入 (文字)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  
  
 如需詳細資訊，請參閱 [HTML Input 控制項](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) \(英文\)、[HtmlInputText 伺服器控制項宣告式語法](http://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e) \(機器翻譯\)、[TextBox Web 伺服器控制項概觀](http://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f) \(英文\)、<xref:System.Web.UI.HtmlControls.HtmlInputText> 與 <xref:System.Web.UI.WebControls.TextBox>。  
  
> [!IMPORTANT]
>  建議驗證所有使用者輸入。 如需詳細資訊，請參閱[驗證 ASP.NET 網頁中的使用者輸入](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)。  
  
 **輸入 (檔案)**  
 ![HTML 網頁檔案欄位](../../ide/reference/media/vxfilefield.gif "vxFilefield")  
  
 在文件中，插入 `type="file"` 的 `input` 項目。 根據預設，插入 `id="File1"` 表示第一個檔案欄位、插入 `id="File2"` 表示第二個檔案欄位，以此類推。  
  
 當您將 [輸入 (檔案)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<input id="File1" type="file" name="File1">  
```  
  
 如需詳細資訊，請參閱 [HTML Input 控制項](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) \(英文\)、[HtmlInputFile 伺服器控制項宣告式語法](http://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6) \(機器翻譯\) 與 <xref:System.Web.UI.HtmlControls.HtmlInputFile>。  
  
> [!IMPORTANT]
>  建議驗證所有使用者輸入。 如需詳細資訊，請參閱[驗證 ASP.NET 網頁中的使用者輸入](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)。  
  
 **輸入 (密碼)**  
 ![Visual Studio 密碼欄位](../../ide/reference/media/vxpassword.gif "vxPassword")  
  
 插入 `type="password"` 的 `input` 項目。 根據預設，插入 `id="Password1"` 表示第一個密碼欄位、插入 `id="Password2"` 表示第二個密碼欄位，以此類推。  
  
 當您將 [輸入 (密碼)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<input id="Password1" type="password" name="Password1">  
```  
  
 如需詳細資訊，請參閱 [HTML Input Controls](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) (HTML Input 控制項)、[HtmlInputPassword Server Control Declarative Syntax](http://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f) (HtmlInputHidden 伺服器控制項宣告式語法)、[How to:Set a TextBox Web Server Control for Password Entry](http://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310) (如何：設定 TextBox 網頁伺服器控制項以輸入密碼) 及 [Walkthrough:Validating User Input in a Web Forms Page](http://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436)(逐步解說：驗證 Web Forms 頁面中的使用者輸入)。  
  
> [!IMPORTANT]
>  如果您的應用程式傳輸使用者名稱和密碼，您應該設定網站使用安全通訊端層 (SSL) 來加密傳輸。 如需詳細資訊，請參閱 [IIS Operations Guide](http://go.microsoft.com/fwlink/?linkid=47856) (IIS 作業手冊) 中的 "Securing Connections with SSL" (保護與 SSL 的連線)。 此外，建議驗證所有使用者輸入。 如需詳細資訊，請參閱[驗證 ASP.NET 網頁中的使用者輸入](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)。  
  
 **輸入 (核取方塊)**  
 ![HTML 網頁工具箱核取方塊選項](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")  
  
 插入 `type="checkbox"` 的 `input` 項目。 若要變更顯示的文字，請編輯 `name` 屬性。 根據預設，插入 `id="Checkbox1"` 表示第一個核取方塊、插入 `id="Checkbox2"` 表示第二個核取方塊，以此類推。  
  
 當您將 [輸入 (核取方塊)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  
  
 如需詳細資訊，請參閱 [HTML Input 控制項](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) \(英文\)、[HtmlInputCheckBox 伺服器控制項宣告式語法](http://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6) \(機器翻譯\)、[CheckBox 和 CheckBoxList Web 伺服器控制項概觀](http://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf) \(英文\)、<xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> 與 <xref:System.Web.UI.WebControls.CheckBox>。  
  
 **輸入 (選項按鈕)**  
 ![VisualStudioHTMLpageRadioButton 螢幕擷取畫面](../../ide/reference/media/vxradio.gif "vxRadio")  
  
 插入 `type="radio"` 的 `input` 項目。 若要變更顯示的文字，請編輯 `name` 屬性。 根據預設，插入 `id="Radio1"` 表示第一個選項按鈕、插入 `id="Radio2"` 表示第二個選項按鈕，以此類推。  
  
 當您將 [輸入 (選項按鈕)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<input id="Radio1" type="radio" name="Radio1">  
```  
  
 如需詳細資訊，請參閱 [HTML Input 控制項](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) \(英文\)、[HtmlInputRadioButton 伺服器控制項宣告式語法](http://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33) \(機器翻譯\)、[RadioButton 和 RadioButtonList Web 伺服器控制項概觀](http://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747) \(英文\)、<xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> 與 <xref:System.Web.UI.WebControls.RadioButton>。  
  
 **輸入 (隱藏)**  
 ![HTML 網頁隱藏項目](../../ide/reference/media/vxhidden.gif "vxhidden")  
  
 插入 `type="hidden"` 的 `input` 項目。 根據預設，插入 `id="Hidden1"` 表示第一個隱藏欄位、插入 `id="Hidden2"` 表示第二個隱藏欄位，以此類推。  
  
 當您將 [輸入 (隱藏)] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  
  
 如需詳細資訊，請參閱 [HTML Input 控制項](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) \(英文\)、[HtmlInputHidden 伺服器控制項宣告式語法](http://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9) \(機器翻譯\) 與 <xref:System.Web.UI.HtmlControls.HtmlInputHidden>。  
  
 **文字區域**  
 ![HTML 網頁工具列文字區域](../../ide/reference/media/vxtextarea.gif "vxTextarea")  
  
 插入 `textarea` 項目。 您可以重新調整文字區域，或使用其捲軸來檢視超出顯示區域的文字。 若要變更顯示的預設文字，請編輯 `value` 屬性。 根據預設，插入 `id="textarea1"` 表示第一個文字區域、插入 `id=" textarea 2"` 表示第二個文字區域，以此類推。  
  
 當您將 [文字區域] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  
  
 如需詳細資訊，請參閱 [HtmlTextArea 伺服器控制項](http://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87) \(英文\)、<xref:System.Web.UI.HtmlControls.HtmlTextArea> 與 <xref:System.Web.UI.WebControls.TextBox>。  
  
> [!IMPORTANT]
>  建議驗證所有使用者輸入。 如需詳細資訊，請參閱[驗證 ASP.NET 網頁中的使用者輸入](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)。  
  
 **資料表**  
 ![HTMLpageToolbarTable 螢幕擷取畫面](../../ide/reference/media/vxtable.gif "vxTable")  
  
 插入 `table` 項目。  
  
 當您將 [資料表] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  
  
 如需詳細資訊，請參閱 [HtmlTable 伺服器控制項宣告式語法](http://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9) \(機器翻譯\)、[Table、TableRow 和 TableCell Web 伺服器控制項概觀](http://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a) \(英文\)、<xref:System.Web.UI.HtmlControls.HtmlTable> 與 <xref:System.Web.UI.WebControls.Table>。  
  
 **影像**  
 ![HTML 網頁影像項目](../../ide/reference/media/vximage.gif "vxImage")  
  
 插入 `img` 項目。 編輯這個項目來指定其 `src` 和其 `alt` 文字。  
  
 當您將 [影像] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<img alt="" src="">  
```  
  
 如需詳細資訊，請參閱 [HtmlImage 伺服器控制項宣告式語法](http://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6) \(機器翻譯\)、[Image Web 伺服器控制項概觀](http://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9) \(英文\)、<xref:System.Web.UI.HtmlControls.HtmlImage>、<xref:System.Web.UI.HtmlControls.HtmlInputImage> 與 <xref:System.Web.UI.WebControls.Image>。  
  
 **選取**  
 ![HTML 網頁工具箱下拉式清單](../../ide/reference/media/vxdropdown.gif "vxDropdown")  
  
 插入下拉式清單 `select` 項目 (不使用 `size` 屬性)。 根據預設，插入 `id="select1"` 表示第一個清單方塊、插入 `id="select2"` 表示第二個清單方塊，以此類推。  
  
 當您將 [選取] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<select id="select1" name="select1"><option selected></option></select>  
```  
  
 您可以增加 size 屬性的值來建立多行 `select` 項目。  
  
 如需詳細資訊，請參閱 [HtmlSelect Server Control Declarative Syntax](http://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5) (HtmlTextArea 伺服器控制項宣告式語法)、[NIB:HOW TO：Create Scripts and Edit Event Handlers](http://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d) (如何：建立指令碼及編輯事件處理常式)、[DropDownList Web Server Control Overview](http://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608) (DropDownList 網頁伺服器控制項概觀)、[ListBox Web Server Control Overview](http://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97) (ListBox 網頁伺服器控制項概觀)、<xref:System.Web.UI.HtmlControls.HtmlSelect> 及 <xref:System.Web.UI.WebControls.DropDownList>。  
  
 **水平尺規**  
 ![HTML 網頁水平尺規項目](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")  
  
 插入 `hr` 項目。 若要增加線條的粗細，請編輯 `size` 屬性。  
  
 當您將 [水平尺規] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<hr width="100%" size=1>   
```  
  
 如需詳細資訊，請參閱 [HTML Horizontal Rule 控制項](http://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f)。  
  
 **Div**  
 ![HTML 網頁標籤](../../ide/reference/media/vxlabel.gif "vxLabel")  
  
 插入包含 `ms_positioning="FlowLayout"` 屬性的 `div` 項目。 除了寬度和高度之外，這個項目等同於「流程配置面板」。 若要格式化 `div` 項目內所含的文字，請將 `class="stylename"` 屬性新增至開始標記。  
  
 當您將 [Div] 拖曳至 [設計] 檢視介面時，會將下列這類 HTML 標記插入文件中：  
  
```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  
  
 如需詳細資訊，請參閱 [HTML Div 控制項](http://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995) \(英文\)、[Label Web 伺服器控制項概觀](http://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac) \(英文\) 與 <xref:System.Web.UI.WebControls.Label>。  
  
## <a name="see-also"></a>請參閱  
 [工具箱](../../ide/reference/toolbox.md)   
 [工具箱、標準索引標籤](http://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870)   
 [HTML 控制項](http://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)
