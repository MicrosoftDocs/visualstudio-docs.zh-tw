---
title: '[方案總管] 中的檔案巢狀規則'
ms.date: 05/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: douge
ms.openlocfilehash: 3ba20e0df156cf2bba77bb919e55016692630ce7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831150"
---
# <a name="customize-file-nesting-in-solution-explorer"></a>自訂 [方案總管] 中的檔案巢狀

[方案總管] 中的相關檔案巢狀不是新的功能，但在這之前您無法控制的巢狀規則。 您可以選擇預設的 [關閉]、[預設] 和 [Web]，但您也可以將巢狀完全自訂成您慣用的情況。 您甚至可以建立特定解決方案和特定專案的設定，但之後根據它們建立更多。 先看一下您現成取得的設定。

> [!NOTE]
> 功能目前僅支援 ASP.NET Core 專案。

## <a name="file-nesting-options"></a>檔案巢狀選項

![開啟/關閉檔案巢狀的按鈕](media/filenesting_onoff.png)

非自訂檔案巢狀的可用選項如下：

* **關閉**：此選項提供沒有任何巢狀的一般檔案清單。

* **預設**：此選項提供 [方案總管] 中的預設檔案巢狀行為。 如果沒有某個專案類型的設定存在，專案中的檔案便不會有巢狀結構。 如果有設定存在，例如 Web 專案，則會套用巢狀結構。

* **Web**：此選項會將 **Web** 檔案巢狀行為套用至目前解決方案中的所有專案。 它有許多規則，我們鼓勵您查看，並告訴我們您的想法。 下列螢幕擷取畫面只強調您用此選項時得到的幾個檔案巢狀行為範例：

   ![[方案總管] 中的檔案巢狀](media/filenesting.png)

## <a name="customize-file-nesting"></a>自訂檔案巢狀

如果您不喜歡現成取得的設定，可以自行建立自訂檔案巢狀設定，指示 [方案總管] 如何巢狀化檔案。 您可以盡情新增自訂檔案巢狀設定，並可可以視需要在它們之間切換。 若要建立新的自訂設定，就可以從空檔案開始，或者使用 [Web] 設定作為起點：

![新增自訂檔案巢狀規則](media/filenesting_addcustom.png)

我們建議您使用 [Web] 設定作為您的起點，因為使用已經有作用的東西比較容易。 如果您使用 [Web] 設定作為起點，*.filenesting.json* 檔看起來類似於下列檔案：

![使用現有的檔案巢狀規則作為自訂設定的基礎](media/filenesting_editcustom.png)

讓我們重點討論節點 **dependentFileProviders** 及其子節點。 每一個子節點都是 Visual Studio 可以用來巢狀化檔案的一種規則。 例如，**具有相同的檔名，但副檔名不同**是一種規則類型。 可用的規則如下：

* **extensionToExtension**：使用這種類型的規則，將 *file.js* 巢狀放在 *file.ts* 下

* **fileSuffixToExtension**：使用這種類型的規則，將 *file-vsdoc.js* 巢狀放在 *file.js* 下

* **addedExtension**：使用這種類型的規則，將 *file.html.css* 巢狀放在 *file.html* 下

* **pathSegment**：使用這種類型的規則，將 *jquery.min.js* 巢狀放在 *jquery.js* 下

* **allExtensions**：使用這種類型的規則，將 *file.** 巢狀放在 *file.js* 下

* **fileToFile**：使用這種類型的規則，將 *bower.json* 巢狀放在 *.bowerrc* 下

### <a name="the-extensiontoextension-provider"></a>extensionToExtension 提供者

此提供者可讓您使用特定副檔名來定義檔案巢狀規則。 參考下列範例：

![extentionToExtension 範例規則](media/filenesting_extensiontoextension.png) ![extentionToExtension 範例作用](media/filenesting_extensiontoextension_effect.png)

* *cart.js* 巢狀於 *cart.ts* 下，這是因為第一個 **extensionToExtension** 規則

* *cart.js* 不巢狀於 *cart.tsx* 下，因為規則中 **.ts** 在 **.tsx** 之前，且只能有一個父代

* *light.css* 巢狀於 *light.sass* 下，這是因為第二個 **extensionToExtension** 規則

* *home.html* 巢狀於 *home.md* 下，這是因為第三個 **extensionToExtension** 規則

### <a name="the-filesuffixtoextension-provider"></a>fileSuffixToExtension 提供者

此提供者運作方式就像 **extensionToExtension** 提供者，唯一的差異在於此規則會查看檔案的前置詞，而不只是副檔名。 參考下列範例：

![fileSuffixToExtension 範例規則](media/filenesting_filesuffixtoextension.png) ![fileSuffixToExtension 範例作用](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js* 巢狀於 *portal.js* 下，這是因為 **fileSuffixToExtension** 規則

* 規則的其他各方面運作方式都與 **extensionToExtension** 相同

### <a name="the-addedextension-provider"></a>addedExtension 提供者

此提供者會將有其他副檔名的檔案巢狀於沒有其他副檔名的檔案下。 其他副檔名只能出現在完整檔名的結尾處。 參考下列範例：

![addedExtension 範例規則](media/filenesting_addedextension.png) ![addedExtension 範例作用](media/filenesting_addedextension_effect.png)

* *file.html.css* 巢狀於 *file.html* 下，這是因為 **addedExtension** 規則

### <a name="the-pathsegment-provider"></a>pathSegment 提供者

此提供者會將有其他副檔名的檔案巢狀放在沒有其他副檔名的檔案下。 其他副檔名只能出現在完整檔名的中間。 參考下列範例：

![pathSegment 範例規則](media/filenesting_pathsegment.png) ![pathSegment 範例作用](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* 巢狀於 *jquery.js* 下，這是因為 **pathSegment** 規則

### <a name="the-allextensions-provider"></a>allExtensions 提供者

此提供者可讓您為具有任何副檔名但相同基底檔案名稱的檔案，定義檔案巢狀規則。 參考下列範例：

![allExtensions 範例規則](media/filenesting_allextensions.png) ![allExtensions 範例作用](media/filenesting_allextensions_effect.png)

* *template.cs* 和 *template.doc* 巢狀於 *template.tt* 下，這是因為 **allExtensions** 規則。

### <a name="the-filetofile-provider"></a>fileToFile 提供者

此提供者可讓您根據整個檔案名稱定義檔案巢狀規則。 參考下列範例：

![fileToFile 範例規則](media/filenesting_filetofile.png) ![fileToFile 範例作用](media/filenesting_filetofile_effect.png)

* *.bowerrc* 巢狀於 *bower.json* 下，這是因為 **fileToFile** 規則

### <a name="rule-order"></a>規則順序

順序在自訂設定檔的每個部分中都很重要。 您可以變更規則執行的順序，方法是在 **dependentFileProvider** 節點內向上或向下移動它們。 比方說，如果您有一項規則，讓 **file.js** 成為 **file.ts** 的父代；還有另一個規則，讓 **file.coffee** 成為 **file.ts** 的父代，它們在檔案中出現的順序規定了這三個檔案全都存在時的巢狀行為。 因為 **file.ts** 只能有一個父代，所以第一個執行的規則便會獲勝。

順序對於規則區段本身很重要，而不只是區段內的檔案。 只要有一對檔案符合檔案巢狀規則，便會忽略檔案中其他進一步向下的規則，然後處理下一對檔案。

### <a name="file-nesting-button"></a>檔案巢狀按鈕

您可以透過 [方案總管] 中的相同按鈕來管理所有設定，包括您自己的自訂設定：

![啟動自訂檔案巢狀規則](media/filenesting_activatecustom.png)

## <a name="create-solution-specific-and-project-specific-settings"></a>建立解決方案與專案特定的設定

您可以透過每個解決方案和專案的操作功能表，建立解決方案與專案特定的設定：

![解決方案與專案特定的巢狀規則](media/filenesting_solutionprojectspecific.png)

解決方案與專案特定的設定會與目前使用的 Visual Studio 設定結合。 例如，您可能有空白的專案特定設定檔，但 [方案總管] 仍會巢狀放置檔案。 巢狀行為來自解決方案特定的設定或 Visual Studio 設定。 合併檔案巢狀設定的優先順序如下：Visual Studio > 解決方案 > 專案。

即使檔案存在於磁碟上，您仍可以告訴 Visual Studio 忽略解決方案與專案特定的設定，方法是啟用 [工具] > [選項] > [ASP.NET Core] > [檔案巢狀] 下的 [忽略解決方案和專案設定] 選項。

您可以進行相反動作，並告訴 Visual Studio「只」使用解決方案或專案特定的設定，方法是將 **root** 節點設為 **true**。 Visual Studio 會在該層級停止合併檔案，且不會將其與階層中更高層級的檔案結合。

解決方案與專案特定的設定可以簽入到原始檔控制，處理程式碼基底的整個小組便可以共用它們。

## <a name="disable-global-file-nesting-rules-for-a-particular-solution-or-project"></a>停用特定解決方案或專案的全域檔案巢狀規則

您可以針對特定解決方案或專案停用現有的全域檔案巢狀規則，方法是使用提供者的 **remove** 動作，而不是 **add**。 例如，如果您將下列設定程式碼新增至專案，所有此特定專案的可能全域存在 **pathSegment** 規則都會停用：

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>另請參閱

- [個人化 IDE](../ide/personalizing-the-visual-studio-ide.md)
