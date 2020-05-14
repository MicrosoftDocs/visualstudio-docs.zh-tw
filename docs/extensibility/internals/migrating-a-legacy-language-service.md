---
title: 遷移傳統語言服務 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e2eff3f3a27b7d8a276c8ed776c1e11d5ce332e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707104"
---
# <a name="migrating-a-legacy-language-service"></a>移轉舊版語言服務
您可以通過更新專案並將 source.擴展.vsixmanifest 檔添加到專案中,將舊語言服務遷移到更高版本的 Visual Studio。 語言服務本身將繼續像以前那樣運行,因為 Visual Studio 編輯器會適應它。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解有關實現語言服務的新方法的詳細資訊,請參閱[編輯器和語言服務擴展](../../extensibility/editor-and-language-service-extensions.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>將視覺化工作室 2008 語言服務解決方案遷移到更高版本
 以下步驟演示如何調整名為 RegEx語言服務的視覺工作室 2008 示例。 您可以在 Visual Studio 2008 SDK 安裝中找到此範例,在*Visual Studio SDK 安裝路徑*[VisualStudio 集成]範例_IDE_CSharp_範例.RegEx語言服務]資料夾中找到此範例。

> [!IMPORTANT]
> 如果語言服務未定義顏色,則必須<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A>`true`在 VSPackage 上顯示式設定為:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>將 Visual Studio 2008 語言服務移到更高版本

1. 安裝較新版本的可視化工作室和可視化工作室 SDK。 有關安裝 SDK 的方法的詳細資訊,請參閱[安裝可視化工作室 SDK](../../extensibility/installing-the-visual-studio-sdk.md)。

2. 編輯 RegExLangServ.csproj 檔(無需在視覺工作室中載入)。

     在`Import`引用 Microsoft.VsSDK.target 檔的節點中,將值替換為以下文本。

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. 保存檔,然後關閉它。

4. 打開 RegExLangServ.sln 解決方案。

5. 將顯示**單向升級**視窗。 按一下 [確定]  。

6. 更新項目屬性。 通過在**解決方案資源管理器**中選擇專案節點(右鍵單擊和選擇屬性)打開 **「專案屬性****」** 視窗。

    - 在**應用程式應用程式選項**卡上,將**目標框架**更改為**4.6.1**。

    - 在 **"除錯'** 選項卡上,在 **"開始外部程式'** 框中,鍵入**\<可視化工作室安裝路徑>_Common7_IDE_devenv.exe.**

         在**指令列參數**框中, 鍵入 /**根綴 Exp**。

7. 更新以下參考:

    - 刪除對微軟的引用.VisualStudio.shell.9.0.dll,然後添加對微軟的引用。

    - 刪除對 Microsoft.VisualStudio.Package.語言服務.9.0.dll 的引用,然後添加對 Microsoft.VisualStudio.Package.語言服務.14.0.dll 的引用。

    - 添加對 Microsoft.VisualStudio.shell.Interop.10.0.dll 的引用。

8. 開啟VsPkg.cs檔並將`DefaultRegistryRoot`屬性的值改變為

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. 原始示例不註冊其語言服務,因此您必須向VsPkg.cs添加以下屬性。

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. 您必須添加源.擴展.vsixmanifest 檔案。

    - 將此檔從現有擴展名複製到專案目錄。 (獲取此檔的一種方法是創建一個 VSIX 專案(在 **"檔案**"下,按一下 **'新建**",然後單擊 **"專案**"。 在「視覺基本」或「C#」下單擊 **「可擴充性**」,然後選擇**VSIX 專案**。

    - 將檔案加入專案中。

    - 在檔案**的屬性**中,將**生成操作**設定為 **"無**"

    - 使用**VSIX 清單編輯器**開啟檔。

    - 變更以下欄位:

    - **ID**: RegExLangServ

    - **產品名稱**: RegExLangServ

    - **說明**:正則表達式語言服務。

    - 在 **"資產**'下,按下 **'新增**'),選擇「**鍵入****到 Microsoft.VisualStudio.VsPackage」,** 將**來源**設定為**目前解決方案中的項目**,然後將**項目**設定為**RegExLangServ**。

    - 儲存並關閉檔案。

11. 建置方案。 產生的檔案部署到 **%USERPROFILE%\AppData_本地\微軟_VisualStudio_14.0Exp_擴展\MSIT_RegExLangServ\\**。

12. 開始偵錯。 打開了視覺工作室的第二個實例。

## <a name="see-also"></a>另請參閱
- [舊版語言服務的擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)
