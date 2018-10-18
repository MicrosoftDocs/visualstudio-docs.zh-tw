---
title: 移轉舊版語言服務 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 39f2cc0932e875a33621241d6cba0cb0b692ff6a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247298"
---
# <a name="migrating-a-legacy-language-service"></a>移轉舊版語言服務
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您可以移轉至較新版的 Visual Studio 的舊版語言服務，藉由更新專案，並將 source.extension.vsixmanifest 檔案加入專案。 語言服務本身將會繼續如往常一般，運作中，因為 Visual Studio 編輯器配合它。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解實作語言服務的新方式，請參閱[編輯器和語言服務延伸模組](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>移轉至較新版的 Visual Studio 2008 語言服務解決方案  
 下列步驟顯示如何調整名為 RegExLanguageService Visual Studio 2008 範例。 您可以找到在 Visual Studio 2008 SDK 安裝中，此範例中*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ 資料夾。  
  
> [!IMPORTANT]
>  如果您的語言服務不會定義的色彩，您必須明確設定<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A>至`true`vspackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>若要移轉至較新版的 Visual Studio 2008 語言服務  
  
1.  安裝 Visual Studio 和 Visual Studio SDK 的較新版本。 如需有關如何安裝 SDK 的詳細資訊，請參閱[安裝 Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md)。  
  
2.  編輯 RegExLangServ.csproj 檔案 （而不需要在 Visual Studio 中載入。  
  
     在  `Import` Microsoft.VsSDK.targets 檔案中，是指的節點值取代成下列文字。  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  儲存檔案，並再將它關閉。  
  
4.  開啟 RegExLangServ.sln 方案。  
  
5.  **單向升級** 視窗隨即出現。 按一下 [確定 **Deploying Office Solutions**]。  
  
6.  更新專案屬性。 開啟**專案屬性**藉由選取專案節點中的視窗**方案總管**，以滑鼠右鍵按一下，然後選取**屬性**。  
  
    -   在 **應用程式**索引標籤中變更**目標 framework**來**4.6.1**。  
  
    -   在 **偵錯**索引標籤中，於**啟動外部程式**方塊中，輸入 **\<Visual Studio 安裝路徑 > \Common7\IDE\devenv.exe。**。  
  
         在 **命令列引數**方塊中，輸入 /**rootsuffix Exp**。  
  
7.  更新下列參考：  
  
    -   移除 Microsoft.VisualStudio.Shell.9.0.dll 的參考，然後將參考加入 Microsoft.VisualStudio.Shell.14.0.dll 和 Microsoft.VisualStudio.Shell.Immutable.11.0.dll。  
  
    -   移除 Microsoft.VisualStudio.Package.LanguageService.9.0.dll 的參考，然後將參考加入 Microsoft.VisualStudio.Package.LanguageService.14.0.dll。  
  
    -   加入 Microsoft.VisualStudio.Shell.Interop.10.0.dll 的參考。  
  
8.  開啟 VsPkg.cs 檔案，然後將值變更`DefaultRegistryRoot`屬性  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. 原始範例不會註冊其語言服務，因此您必須將下列屬性新增至 VsPkg.cs。  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. 您必須新增 source.extension.vsixmanifest 檔案中。  
  
    -   從現有的擴充功能的這個檔案複製到您的專案目錄中。 (若要取得這個檔案的一個方式是建立 VSIX 專案 (底下**檔案**，按一下**新增**，然後按一下**專案**。 在 Visual Basic 或 C# 按一下**擴充性**，然後選取**VSIX 專案**。)  
  
    -   您可以將檔案加入您的專案。  
  
    -   中的檔案**屬性**，將**建置動作**來**None**。  
  
    -   開啟副檔名**VSIX 資訊清單編輯器**。  
  
    -   變更下列欄位：  
  
    -   **識別碼**: RegExLangServ  
  
    -   **產品名稱**: RegExLangServ  
  
    -   **描述**： 規則運算式語言服務。  
  
    -   底下**資產**，按一下**新增**，選取**型別**至**Microsoft.VisualStudio.VsPackage**，將**來源**要**目前的方案中的專案**，然後將**專案**來**RegExLangServ**。  
  
    -   儲存並關閉檔案。  
  
11. 建置方案。 內建的檔案都部署到 **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**。  
  
12. 開始偵錯。 開啟 Visual Studio 的第二個執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [舊版語言服務的擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)

