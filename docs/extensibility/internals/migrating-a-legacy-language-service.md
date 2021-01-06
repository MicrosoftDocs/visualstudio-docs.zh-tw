---
title: 遷移舊版語言服務 |Microsoft Docs
description: 瞭解如何更新專案並新增 extension.vsixmanifest 檔案，以將語言服務更新為最新版本的 Visual Studio。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ced200ff24b17f312e63642c8083f038a6fc6a4d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877828"
---
# <a name="migrating-a-legacy-language-service"></a>移轉舊版語言服務
您可以藉由更新專案並將 extension.vsixmanifest 檔案新增至專案，將舊版語言服務遷移至更新版的 Visual Studio。 語言服務本身將會繼續如之前一樣運作，因為 Visual Studio 編輯器會調整它。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解如何執行語言服務的新方法，請參閱 [編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>將 Visual Studio 2008 語言服務解決方案遷移至較新版本
 下列步驟顯示如何調整名為 RegExLanguageService 的 Visual Studio 2008 範例。 您可以在 *VISUAL STUDIO sdk 安裝路徑*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ 資料夾的 VISUAL STUDIO 2008 sdk 安裝中找到此範例。

> [!IMPORTANT]
> 如果您的語言服務未定義色彩，您必須 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> 在 VSPackage 上明確地將設定為 `true` ：

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>將 Visual Studio 2008 語言服務遷移至更新版本

1. 安裝較新版本的 Visual Studio 和 Visual Studio SDK。 如需安裝 SDK 方式的詳細資訊，請參閱 [安裝 VISUAL STUDIO sdk](../../extensibility/installing-the-visual-studio-sdk.md)。

2. 編輯 RegExLangServ .csproj 檔案 (而不在 Visual Studio 中載入。

     在 `Import` 參考 VsSDK 檔案的節點中，以下列文字取代此值。

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. 儲存檔案，然後關閉它。

4. 開啟 RegExLangServ .sln 方案。

5. [ **單向升級** ] 視窗隨即出現。 按一下 [確定]。

6. 更新專案屬性。 選取 [**方案總管** 中的專案節點，按一下滑鼠右鍵，然後選取 [**屬性**]，開啟 [**專案屬性**] 視窗。

    - 在 [ **應用程式** ] 索引標籤上，將 [ **目標 framework** ] 變更為 **4.6.1**。

    - 在 [**調試** 程式] 索引標籤的 [**啟動外部程式**] 方塊中，輸入 **\<Visual Studio installation path>\Common7\IDE\devenv.exe。**

         在 [ **命令列引數** ] 方塊中，輸入/**rootsuffix Exp**。

7. 更新下列參考：

    - 移除 Microsoft.VisualStudio.Shell.9.0.dll 的參考，然後新增 Microsoft.VisualStudio.Shell.14.0.dll 和 Microsoft.VisualStudio.Shell.Immutable.11.0.dll 的參考。

    - 移除 Microsoft.VisualStudio.Package.LanguageService.9.0.dll 的參考，然後新增 Microsoft.VisualStudio.Package.LanguageService.14.0.dll 的參考。

    - 新增 Microsoft.VisualStudio.Shell.Interop.10.0.dll 的參考。

8. 開啟 VsPkg.cs 檔案，並將屬性的值變更 `DefaultRegistryRoot` 為

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. 原始範例不會註冊其語言服務，因此您必須將下列屬性新增至 VsPkg.cs。

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. 您必須新增 extension.vsixmanifest 檔案。

    - 將此檔案從現有的延伸模組複製到您的專案目錄。  (取得此檔案的方法之一是在 [檔案 **] 下建立** VSIX 專案 (，按一下 [ **新增**]，然後按一下 [ **專案**]。 在 Visual Basic 或 c # **中，** 按一下 [擴充性]，然後選取 [ **VSIX 專案**]。 ) 

    - 將檔案加入專案中。

    - 在檔案的 [ **屬性**] 中，將 [ **組建動作** ] 設定為 [ **無**]。

    - 使用 **VSIX 資訊清單編輯器** 開啟檔案。

    - 變更下欄欄位：

    - **識別碼**： RegExLangServ

    - **產品名稱**： RegExLangServ

    - **描述**：正則運算式語言服務。

    - 在 [**資產**] 底下，按一下 [**新增**]，選取 **VisualStudio VsPackage** 的 **類型**，將 [**來源**] 設定為 [**目前方案中的專案**]，然後將 **專案** 設定為 [ **RegExLangServ**]。

    - 儲存並關閉檔案。

11. 建置方案。 建立的檔案會部署至 **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ \\**。

12. 開始偵錯。 Visual Studio 開啟的第二個實例。

## <a name="see-also"></a>請參閱
- [舊版語言服務的擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)
