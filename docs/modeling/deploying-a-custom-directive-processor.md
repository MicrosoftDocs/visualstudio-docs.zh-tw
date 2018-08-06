---
title: 部署自訂指示詞處理器
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3f4af12b7c73aa2da7f580b11b1984aa2c8238b7
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566823"
---
# <a name="deploying-a-custom-directive-processor"></a>部署自訂指示詞處理器

若要使用 Visual Studio 中的自訂指示詞處理器，在任何電腦上，您必須將它註冊其中一種方法，本主題中所述。

可供選擇的方法為：

-   [Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)。 此方法提供在自己的電腦以及其他電腦上安裝和解除安裝指示詞處理器的方式。 您通常可以在相同的 VSIX 中封裝其他功能。

-   [VSPackage](../extensibility/internals/vspackages.md)。 如果您要定義除了指示詞處理器之外還包含其他功能的 VSPackage，有個便利的方法可以註冊指示詞處理器。

-   設定登錄機碼： 使用這個方法時，您會加入指示詞處理器的登錄項目。

您需要使用其中一種方法，只有當您想要轉換文字範本在 Visual Studio 或 MSBuild。 如果您在自己的應用程式 (Application) 中使用自訂主應用程式 (Custom Host)，那麼自訂主應用程式就要負責為每個指示詞尋找指示詞處理器。

## <a name="deploying-a-directive-processor-in-a-vsix"></a>在 VSIX 中部署指示詞處理器

您可以新增自訂指示詞處理器[Visual Studio 擴充功能 (VSIX)](../extensibility/starting-to-develop-visual-studio-extensions.md)。

 您必須確認 .vsix 檔是否包含下列兩個項目：

-   含有自訂指示詞處理器類別的組件 (.dll)。

-   註冊指示詞處理器的 .pkgdef 檔。 檔案的主檔名必須與組件相同。 例如，您的檔案可以命名為 CDP.dll 和 CDP.pkgdef。

若要檢查或變更 .vsix 檔案的內容，請將副檔名變更為 .zip，然後開啟檔案。 編輯內容之後，再將檔名變更回 .vsix。

有數個建立 .vsix 檔的方法。 下列程序將說明其中一個方法。

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>若要在 VSIX 專案中開發自訂指示詞處理器

1.  Visual Studio 中建立 VSIX 專案。

    -   在**新的專案**對話方塊方塊中，展開**Visual Basic**或**Visual C#**，然後展開**擴充性**。 按一下  **VSIX 專案**。

2.  在  **source.extension.vsixmanifest**、 內容類型設定和支援的版本。

    1.  在 VSIX 資訊清單編輯器中，在**資產**索引標籤上，選擇**新增**並設定新的項目屬性：

         **內容類型** = **VSPackage**

         **來源專案** = \<*目前的專案*>

    2.  按一下 **選取的版本**並檢查您想要可指示詞處理器的安裝類型。

3.  加入 .pkgdef 檔案，並設定其要包含在 VSIX 中的屬性。

    1.  建立文字檔案並將它命名\< *assemblyName*>.pkgdef。

         \<*assemblyName*> 通常是專案的名稱相同。

    2.  在 [方案總管] 中選取它，然後設定其屬性，如下所示：

         **建置動作** = **內容**

         **複製到輸出目錄** = **一律複製**

         **包含在 VSIX** = **，則為 True**

    3.  設定 VSIX 的名稱，並確定 ID 是唯一的。

4.  將下列文字加入至 .pkgdef 檔：

    ```
    [$RootKey$\TextTemplating]
    [$RootKey$\TextTemplating\DirectiveProcessors]
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]
    @="Custom Directive Processor description"
    "Class"="NamespaceName.ClassName"
    "CodeBase"="$PackageFolder$\AssemblyName.dll"
    ```

     以自己的名稱取代下列名稱：`CustomDirectiveProcessorName`、`NamespaceName`、`ClassName`、`AssemblyName`。

5.  將下列參考加入至專案：

    -   **Microsoft.VisualStudio.TextTemplating.\*.0**

    -   **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0**

    -   **Microsoft.VisualStudio.TextTemplating.VSHost.\*.0**

6.  將自訂指示詞處理器類別加入至專案。

     這是應該實作 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 的公用類別。

#### <a name="to-install-the-custom-directive-processor"></a>若要安裝自訂指示詞處理器

1.  在 Windows 檔案總管中，開啟組建目錄 （通常是 bin\Debug 或 bin\Release）。

2.  如果您想要在另一台電腦上安裝指示詞處理器，請將 .vsix 檔複製到該電腦。

3.  按兩下 .vsix 檔。 Visual Studio 擴充功能安裝程式會出現。

4.  重新啟動 Visual Studio。 您現在可以執行包含參考自訂指示詞處理器之指示詞的文字範本。 每個指示詞的格式如下：

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>若要解除安裝或暫時停用自訂指示詞處理器

1.  在 Visual Studio**工具**功能表上，按一下**延伸模組管理員**。

2.  選取包含指示詞處理器的 VSIX，然後按一下**解除安裝**或是**停用**。

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>VSIX 中的指示詞處理器疑難排解
 如果指示詞處理器無法運作，下列建議可能會有幫助：

-   您在自訂指示詞中指定的處理器名稱應該與在 .pkgdef 檔中指定的 `CustomDirectiveProcessorName` 相符。

-   將 `IsDirectiveSupported` 的名稱傳遞給 `true` 方法時，此方法必須傳回 `CustomDirective`。

-   如果看不到管理員 」 中的延伸模組，延伸模組，但系統將不會允許您進行安裝，刪除從延伸模組 **%localappdata%\Microsoft\VisualStudio\\\*。 0\Extensions\\** .

-   開啟 .vsix 檔並檢查其內容。 若要開啟它，請將副檔名變更為 .zip。 確認其中是否包含 .dll、.pkgdef 和 extension.vsixmanifest 檔案。 extension.vsixmanifest 檔案在 SupportedProducts 節點中應包含適當清單，而在 Content 節點底下也應包含 VsPackage 節點。

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>在 VSPackage 中部署指示詞處理器
 如果指示詞處理器是將要安裝於 GAC 之 VSPackage 的一部分，您可以讓系統為您產生 .pkgdef 檔。

 請將下列屬性放在您的套件類別上：

```csharp
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]
```

> [!NOTE]
>  這個屬性要放在套件類別，而非指示詞處理器類別上。

 當您建置專案時，就會產生 .pkgdef 檔。 當您安裝 VSPackage 時，.pkgdef 檔將會註冊指示詞處理器。

 確認 .pkgdef 檔是否出現在組建資料夾中，這個資料夾通常是 bin\Debug 或 bin\Release。 如果沒有出現，請使用文字編輯器開啟 .csproj 檔，並移除下列節點：`<GeneratePkgDefFile>false</GeneratePkgDefFile>`。

 如需詳細資訊，請參閱 < [Vspackage](../extensibility/internals/vspackages.md)。

## <a name="setting-a-registry-key"></a>設定登錄機碼
 除非不得已，否則不建議使用這個方法來安裝自訂指示詞處理器。 它無法提供啟用和停用指示詞處理器的便利方式，也無法提供散發指示詞處理器給其他使用者的方法。

> [!CAUTION]
>  不當編輯登錄可能會造成系統嚴重受損。 變更登錄之前，務必先備份電腦上任何重要的資料。

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>若要設定登錄機碼來註冊指示詞處理器

1.  執行 `regedit`。

2.  在 regedit 中巡覽至

     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**

     如果您想要安裝 Visual Studio 的實驗版本中的指示詞處理器，請在"11.0"之後插入"Exp"。

3.  加入與指示詞處理器相同名稱的登錄機碼。

    -   在登錄樹狀目錄中，以滑鼠右鍵按一下**DirectiveProcessors**節點，指向**新增**，然後按一下**金鑰**。

4.  根據下表，在新節點中加入 Class 和 CodeBase 或 Assembly 的字串值。

    1.  以滑鼠右鍵按一下您所建立的節點，指向**的新**，然後按一下**字串值**。

    2.  輸入該值的名稱。

    3.  按兩下名稱，然後編輯資料。

 如果自訂指示詞處理器不在 GAC 中，則登錄子機碼看起來應該如下表所示：

|名稱|類型|資料|
|----------|----------|----------|
|(預設值)|REG_SZ|(值未設定)|
|類別|REG_SZ|**\<命名空間名稱 >。\<類別名稱 >**|
|程式碼基底|REG_SZ|**\<您的路徑 >\\< 組件名稱\>**|

 如果組件在 GAC 中，則登錄子機碼看起來應該如下表所示：

|名稱|類型|資料|
|----------|----------|----------|
|(預設值)|REG_SZ|(值未設定)|
|類別|REG_SZ|\<**您完整的類別名稱**>|
|Assembly|REG_SZ|\<**您在 GAC 中的組件名稱**>|

## <a name="see-also"></a>另請參閱

- [建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)