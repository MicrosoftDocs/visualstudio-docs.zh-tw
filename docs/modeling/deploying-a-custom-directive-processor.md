---
title: 部署自訂指示詞處理器
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a10252d8465373c8637681763e59511b1e2d621
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596667"
---
# <a name="deploying-a-custom-directive-processor"></a>部署自訂指示詞處理器

若要在任何電腦上使用 Visual Studio 中的自訂指示詞處理器，您必須依照本主題中所述的其中一種方法來進行註冊。

可供選擇的方法為：

- [Visual Studio 延伸](../extensibility/shipping-visual-studio-extensions.md)模組。 此方法提供在自己的電腦以及其他電腦上安裝和解除安裝指示詞處理器的方式。 您通常可以在相同的 VSIX 中封裝其他功能。

- [VSPackage](../extensibility/internals/vspackages.md)。 如果您要定義除了指示詞處理器之外還包含其他功能的 VSPackage，有個便利的方法可以註冊指示詞處理器。

- 設定登錄機碼： 使用這個方法時，您會加入指示詞處理器的登錄項目。

只有當您想要在 Visual Studio 或 MSBuild 中轉換文字模板時，才需要使用其中一種方法。 如果您在自己的應用程式 (Application) 中使用自訂主應用程式 (Custom Host)，那麼自訂主應用程式就要負責為每個指示詞尋找指示詞處理器。

## <a name="deploying-a-directive-processor-in-a-vsix"></a>在 VSIX 中部署指示詞處理器

您可以將自訂指示詞處理器加入[Visual Studio 延伸模組（VSIX）](../extensibility/starting-to-develop-visual-studio-extensions.md)。

 您必須確認 .vsix 檔是否包含下列兩個項目：

- 含有自訂指示詞處理器類別的組件 (.dll)。

- 註冊指示詞處理器的 .pkgdef 檔。 檔案的主檔名必須與組件相同。 例如，您的檔案可以命名為 CDP.dll 和 CDP.pkgdef。

若要檢查或變更 .vsix 檔案的內容，請將副檔名變更為 .zip，然後開啟檔案。 編輯內容之後，再將檔名變更回 .vsix。

有數個建立 .vsix 檔的方法。 下列程序將說明其中一個方法。

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>若要在 VSIX 專案中開發自訂指示詞處理器

1. 建立新的**VSIX 專案**專案。

2. 在**extension.vsixmanifest**中，設定內容類型和支援的版本。

    1. 在 VSIX 資訊清單編輯器的 [**資產**] 索引標籤上，選擇 [**新增**] 並設定新專案的屬性：

         **內容類型** = **VSPackage**

         *目前專案 \<的***來源專案** = >

    2. 按一下 [**選取的版本**]，然後檢查您要指示詞處理器可供使用的安裝類型。

3. 加入 .pkgdef 檔案，並設定其要包含在 VSIX 中的屬性。

    1. 建立文字檔，並將它命名 \<*assemblyName*>. .pkgdef。

         \<*assemblyName*> 通常與專案的名稱相同。

    2. 在 [方案總管] 中選取它，然後設定其屬性，如下所示：

         **建置動作** = **內容**

         **複製到輸出目錄** = **一律複製**

         **包含在 VSIX** = **True**

    3. 設定 VSIX 的名稱，並確定 ID 是唯一的。

4. 將下列文字加入至 .pkgdef 檔：

    ```
    [$RootKey$\TextTemplating]
    [$RootKey$\TextTemplating\DirectiveProcessors]
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]
    @="Custom Directive Processor description"
    "Class"="NamespaceName.ClassName"
    "CodeBase"="$PackageFolder$\AssemblyName.dll"
    ```

     以自己的名稱取代下列名稱：`CustomDirectiveProcessorName`、`NamespaceName`、`ClassName`、`AssemblyName`。

5. 將下列參考加入至專案：

    - **VisualStudio. TextTemplating.\*0**

    - **VisualStudio. TextTemplating 介面。\*0**

    - **VisualStudio. TextTemplating. .Vshost.exe.\*0**

6. 將自訂指示詞處理器類別加入至專案。

     這是應該實作 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 的公用類別。

#### <a name="to-install-the-custom-directive-processor"></a>若要安裝自訂指示詞處理器

1. 在 Windows Explorer 中，開啟組建目錄（通常是 bin\Debug 或 bin\Release）。

2. 如果您想要在另一台電腦上安裝指示詞處理器，請將 .vsix 檔複製到該電腦。

3. 按兩下 .vsix 檔。 Visual Studio 延伸模組安裝程式隨即出現。

4. 重新啟動 Visual Studio。 您現在可以執行包含參考自訂指示詞處理器之指示詞的文字範本。 每個指示詞的格式如下：

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>若要解除安裝或暫時停用自訂指示詞處理器

1. 在 [Visual Studio**工具**] 功能表中，按一下 [**擴充管理員**]。

2. 選取包含指示詞處理器的 VSIX，然後按一下 [**卸載**] 或 [**停**用]。

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>VSIX 中的指示詞處理器疑難排解
 如果指示詞處理器無法運作，下列建議可能會有幫助：

- 您在自訂指示詞中指定的處理器名稱應該與在 .pkgdef 檔中指定的 `CustomDirectiveProcessorName` 相符。

- 將 `IsDirectiveSupported` 的名稱傳遞給 `true` 方法時，此方法必須傳回 `CustomDirective`。

- 如果您在 [擴充管理員] 中看不到延伸模組，但系統不允許您安裝它，請從 **%localappdata%\Microsoft\VisualStudio\\\*.0 \** 延伸模組\\中刪除延伸模組。

- 開啟 .vsix 檔並檢查其內容。 若要開啟它，請將副檔名變更為 .zip。 確認其中是否包含 .dll、.pkgdef 和 extension.vsixmanifest 檔案。 extension.vsixmanifest 檔案在 SupportedProducts 節點中應包含適當清單，而在 Content 節點底下也應包含 VsPackage 節點。

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
> 這個屬性要放在套件類別，而非指示詞處理器類別上。

 當您建置專案時，就會產生 .pkgdef 檔。 當您安裝 VSPackage 時，.pkgdef 檔將會註冊指示詞處理器。

 確認 .pkgdef 檔是否出現在組建資料夾中，這個資料夾通常是 bin\Debug 或 bin\Release。 如果沒有出現，請使用文字編輯器開啟 .csproj 檔，並移除下列節點：`<GeneratePkgDefFile>false</GeneratePkgDefFile>`。

 如需詳細資訊，請參閱 [VSPackages](../extensibility/internals/vspackages.md)。

## <a name="setting-a-registry-key"></a>設定登錄機碼
 除非不得已，否則不建議使用這個方法來安裝自訂指示詞處理器。 它無法提供啟用和停用指示詞處理器的便利方式，也無法提供散發指示詞處理器給其他使用者的方法。

> [!CAUTION]
> 不當編輯登錄可能會對系統造成嚴重損害。 變更登錄之前，務必先備份電腦上任何重要的資料。

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>若要設定登錄機碼來註冊指示詞處理器

1. 執行 `regedit`。

2. 在 regedit 中巡覽至

    **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\\\*. 0 \ TextTemplating\DirectiveProcessors**

    如果您想要在 Visual Studio 的實驗版本中安裝指示詞處理器，請在 "11.0" 之後插入 "Exp"。

3. 加入與指示詞處理器相同名稱的登錄機碼。

   - 在登錄樹狀目錄中，以滑鼠右鍵按一下 [ **DirectiveProcessors** ] 節點，指向 [**新增**]，然後按一下 [機**碼**]。

4. 根據下表，在新節點中加入 Class 和 CodeBase 或 Assembly 的字串值。

   1. 以滑鼠右鍵按一下您建立的節點，指向 [**新增**]，然後按一下 [**字串值**]。

   2. 輸入該值的名稱。

   3. 按兩下名稱，然後編輯資料。

   如果自訂指示詞處理器不在 GAC 中，則登錄子機碼看起來應該如下表所示：

|Name|類型|Data|
|-|-|-|
|(預設)|REG_SZ|(值未設定)|
|類別|REG_SZ|**\<命名空間名稱 >。\<類別名稱 >**|
|程式碼基底|REG_SZ|**\<您的路徑 >\\< 元件名稱\>**|

 如果組件在 GAC 中，則登錄子機碼看起來應該如下表所示：

|Name|類型|Data|
|-|-|-|
|(預設)|REG_SZ|(值未設定)|
|類別|REG_SZ|\<**您的完整類別名稱**>|
|Assembly|REG_SZ|\<**GAC 中的元件名稱**>|

## <a name="see-also"></a>請參閱

- [建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)
