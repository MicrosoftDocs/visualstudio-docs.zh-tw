---
title: "使用 EditorConfig 建立可攜式自訂編輯器設定 | Microsoft Docs"
ms.custom: 
ms.date: 10/27/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editor
ms.assetid: 
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 2c1df6f8e34d2b8e72486dd804ba57f0dcf2406b
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>使用 EditorConfig 建立可攜式自訂編輯器設定
在 Visual Studio 中的文字編輯器設定適用於特定類型的所有專案。 因此，比方說，如果您變更 C# 文字編輯器設定，該設定會適用於 Visual Studio 中的「所有」C# 專案。 不過，在某些情況下，您可能需要使用不同於您自己的個人編輯器喜好設定的慣例。 [EditorConfig](http://editorconfig.org/) 檔案藉由根據每個專案提供一般文字編輯器選項，而讓您能做到這點。 在新增到您程式碼基底的 .editorconfig 檔案中，所包含的 EditorConfig 設定會取代全域 Visual Studio 文字編輯器設定。 這表示您可以自訂每個程式碼基底，以使用您偏好的文字編輯器設定。 不需要外掛程式即可在 Visual Studio 中使用這項功能。

## <a name="coding-consistency"></a>程式碼撰寫的一致性
EditorConfig 檔案中的設定可讓您在程式碼基底中維護語言的一致程式碼樣式和設定，例如縮排樣式、Tab 跳位寬度、行結尾字元、編碼等等，而不論您使用的編輯器或 IDE 為何。 比方說，當以 C++ 編寫程式碼時，如果您的程式碼基底慣例偏好縮排一律包含五個空白字元、文件使用 UTF-8 編碼方式，且每一行的結尾一律為 CR/LF，您可以設定 .editorconfig 檔案來做到這點。

您在個人專案上使用的編碼慣例，可能與用於小組專案的不同。 例如，您編寫程式碼時，可能會偏好按下 Tab 鍵將新增一個 TAB 字元。 不過，您的小組可能會偏好縮排時新增四個空白字元，而不是 TAB 字元。 EditorConfig 檔案讓您能擁有每個案例的組態，以解決此問題。

因為設定是包含在程式碼基底的檔案中，所以它們會隨著該程式碼基底四處移動。 只要您在符合 EditorConfig 規範的編輯器中開啟程式碼檔案，便會實作文字編輯器設定。 如需 EditorConfig 檔案的詳細資訊，請參閱 [EditorConfig.org](http://editorconfig.org/) 網站。

## <a name="override-editorconfig-settings"></a>覆寫 EditorConfig 設定
當您將 .editorconfig 檔案新增到檔案階層中的資料夾時，其設定會適用於該層級和以下的所有適用檔案。 若要覆寫特定專案或程式碼庫的 EditorConfig 設定，使其使用與最上層 .editorconfig 檔案不同的慣例，只要將 .editorconfig 檔案新增至程式碼庫之存放庫或專案目錄的根目錄即可。 請務必將 ```root=true```屬性放入檔案中，讓 Visual Studio 不會在目錄結構中進一步往上尋找任何 .editorconfig 檔案。 新的 .editorconfig 檔案設定將套用到它所在的層級和其所有子目錄中的檔案。

```
# top-most EditorConfig file
root = true
```

![EditorConfig 階層](../ide/media/vside_editorconfig_hierarchy.png)

EditorConfig 檔案是由上往下讀取，而且最接近的 EditorConfig 檔案最後才讀取。 會以讀取順序套用相符 EditorConfig 區段的慣例，因此最接近之檔案的慣例優先。

## <a name="supported-settings"></a>支援的設定
Visual Studio 中的編輯器支援一組核心 [EditorConfig 屬性](http://editorconfig.org/#supported-properties)中的下列項目：  

- indent_style
- indent_size
- tab_width
- end_of_line
- 字元集
- 根

此外，它支援 [.NET 程式碼樣式慣例](../ide/editorconfig-code-style-settings-reference.md)。  

除了 XML 以外的所有 Visual Studio 支援語言都支援 EditorConfig 設定。

## <a name="intellisense"></a>IntelliSense
Visual Studio 提供有限的 IntelliSense 來編輯 .editorconfig 檔案。 如果您編輯許多 .editorconfig 檔案，可能會發現 [EditorConfig Language Service](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) (EditorConfig 語言服務) 延伸模組很有幫助。

## <a name="example"></a>範例
以下範例顯示 C# 程式碼片段在將 .editorconfig 檔案新增至專案之前和之後的縮排狀態。 Visual Studio 文字編輯器 [選項] 對話方塊的 [定位字元] 設定已設為在您於程式碼中按下 **Tab** 鍵時，會產生空白字元。

![文字編輯器定位字元設定](../ide/media/vside_editorconfig_tabsetting.png)

如同預期，在下一行按下 **Tab** 鍵會藉由新增四個額外的空白字元來縮排該行。

![使用 EditorConfig 前的程式碼](../ide/media/vside_editorconfig_before.png)

我們會將稱為 .editorconfig 的新檔案新增到專案中，其中包含下列內容。 `[*.cs]` 設定表示這項變更只會套用到此專案中的 .cs 檔案。  

![新增 .editorconfig 檔案至專案](../ide/media/vside_editorconfig_addconfig.png)

現在，當您按下 **Tab** 鍵，會得到定位點字元，而不是空白。

![TAB 新增定位字元](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  將 .editorconfig 檔案新增到專案或程式碼基底並不會將現有的樣式轉換為新樣式，它只適用於剛剛新增的行。 如果您從專案或程式碼基底移除 .editorconfig 檔案，必須重新載入程式碼檔案，編輯器設定才會還原成全域設定。 在 Visual Studio 中的 [錯誤清單] 視窗內會報告 .editorconfig 檔案的任何錯誤。

## <a name="troubleshooting-editorconfig-settings"></a>疑難排解 EditorConfig 設定
如果目錄結構中的任何位置或在專案位置上方有一個 EditorConfig 檔案，Visual Studio 會將該檔案中的編輯器設定套用到您的編輯器。 在此情況下，您可能會看到狀態列中出現下列訊息：

**「此檔案類型的使用者偏好由此專案的編碼慣例覆寫。」**

這表示，如果 [工具]、[選項]、[文字編輯器] 中的任何編輯器設定 (例如縮排大小、定位點大小，縮排樣式 &mdash; 定位點或空格，或是使用 `var` 之類的編碼慣例) 指定所在的 EditorConfig 檔案等於或高於目錄結構中的專案，則 EditorConfig 檔案中的慣例將會覆寫選項中的設定。 您可以藉由切換 [工具]、[選項]、[文字編輯器] 中的 [遵循專案編碼慣例] 選項來控制這個行為。 取消選取此選項，將會關閉 Visual Studio 的　EditorConfig 支援。

![編碼選項 - 遵循專案編碼慣例](media/coding_conventions_option.png)

您可以透過開啟命令提示字元，並從包含專案的磁碟根目錄中執行下列命令，在父目錄中尋找.editorconfig 檔案：

```
dir .editorconfig /s
```

您可以在存放庫根目錄或專案所在目錄的 .editorconfig 檔案中設定 ```root=true``` 屬性，藉以控制 EditorConfig 慣例範圍。 Visual Studio 會在已開啟檔案的目錄和每個父目錄中尋找名為 .editorconfig 的檔案。 Visual Studio 會在達到根檔案路徑或找到含有 ```root=true``` 的 .editorconfig 檔案時停止搜尋。

## <a name="support-editorconfig-for-your-language-service"></a>語言服務的 EditorConfig 支援
在大部分情況下，當您實作 Visual Studio 語言服務時，並不需要進行任何額外的作業即可支援 EditorConfig 通用屬性。 當使用者開啟檔案時，核心編輯器會自動探索並讀取 .editorconfig 檔案，然後設定適當的文字緩衝區和檢視選項。 不過，當使用者編輯或格式化文字時，有些語言服務會選擇適當的內容文字檢視選項，而不使用定位點和空格這類項目的全域設定。 在這種情況下，您必須更新語言服務才能支援 EditorConfig 檔案。

以下是更新語言服務以支援 EditorConfig 檔案所需的變更，方法為將全域 [特定語言] 選項取代為 [內容] 選項：  

### <a name="indent-style"></a>縮排樣式
取代：  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs  
_或_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs  

成為：  

!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  
_或_  
!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  

### <a name="indent-size"></a>縮排大小
取代：  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize  
_或_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize  

成為：  

textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)  
_或_  
textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)  

### <a name="tab-size"></a>定位點大小
取代：  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize  
_或_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize  

成為：  

textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)  
_或_  
textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)  

## <a name="see-also"></a>請參閱
[.NET 程式碼樣式慣例](../ide/editorconfig-code-style-settings-reference.md)  
[EditorConfig.org](http://editorconfig.org/)  
[在編輯器中撰寫程式碼](writing-code-in-the-code-and-text-editor.md)