---
title: 移轉舊版語言服務 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 412b09016a3f889e0d6c5e40ff75895d5ae8ff48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135846"
---
# <a name="migrating-a-legacy-language-service"></a>移轉舊版語言服務
您可以移轉至較新版的 Visual Studio 的舊版語言服務更新專案，並將 source.extension.vsixmanifest 檔案加入專案。 語言服務本身將會繼續如往常一般，運作，因為 Visual Studio 編輯器會調整它。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要了解有關實作語言服務的新方法的詳細資訊，請參閱[編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>移轉至更新版本的 Visual Studio 2008 語言服務方案  
 下列步驟顯示如何調整名為 RegExLanguageService Visual Studio 2008 範例。 您可以尋找在 Visual Studio 2008 SDK 安裝中，此範例在*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ 資料夾。  
  
> [!IMPORTANT]
>  如果您的語言服務不會定義色彩，您必須明確設定<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A>至`true`vspackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>若要移轉至更新版本的 Visual Studio 2008 語言服務  
  
1.  安裝新版本的 Visual Studio 和 Visual Studio SDK。 如需安裝 SDK 的方式的詳細資訊，請參閱[安裝 Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md)。  
  
2.  編輯 RegExLangServ.csproj 檔案 （而不需要在 Visual Studio 中載入。  
  
     在`Import`Microsoft.VsSDK.targets 檔案，是指的節點值取代為下列文字。  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  儲存檔案，然後關閉它。  
  
4.  開啟 RegExLangServ.sln 方案。  
  
5.  **單向升級** 視窗隨即出現。 按一下 [確定 **Deploying Office Solutions**]。  
  
6.  更新的專案屬性。 開啟**專案屬性**所選取專案節點中的視窗**方案總管 中**、 按一下滑鼠右鍵，然後選取**屬性**。  
  
    -   在**應用程式**索引標籤上，變更**目標 framework**至**4.6.1**。  
  
    -   在**偵錯**索引標籤的**啟動外部程式**方塊中，輸入 **\<Visual Studio 安裝路徑 > \Common7\IDE\devenv.exe**。  
  
         在**命令列引數**方塊中，輸入 /**rootsuffix Exp**。  
  
7.  更新下列參考：  
  
    -   移除參考 Microsoft.VisualStudio.Shell.9.0.dll，然後將參考加入 Microsoft.VisualStudio.Shell.14.0.dll 和 Microsoft.VisualStudio.Shell.Immutable.11.0.dll。  
  
    -   移除參考 Microsoft.VisualStudio.Package.LanguageService.9.0.dll，然後加入 Microsoft.VisualStudio.Package.LanguageService.14.0.dll 的參考。  
  
    -   加入 Microsoft.VisualStudio.Shell.Interop.10.0.dll 的參考。  
  
8.  開啟 VsPkg.cs 檔案，然後將值變更`DefaultRegistryRoot`屬性  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. 原始範例並未登錄其語言服務，因此您必須將下列屬性加入 VsPkg.cs。  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. 您必須新增 source.extension.vsixmanifest 檔案。  
  
    -   將這個檔案從現有的延伸模組複製您的專案目錄。 (若要取得這個檔案的一種方式為建立 VSIX 專案 (下**檔案**，按一下 **新增**，然後按一下 **專案**。 在 Visual Basic 或 C# 按一下**擴充性**，然後選取**VSIX 專案**。)  
  
    -   將檔案加入您的專案。  
  
    -   在檔案的**屬性**，將**建置動作**至**無**。  
  
    -   開啟檔案所使用**VSIX 資訊清單編輯器**。  
  
    -   變更下列欄位：  
  
    -   **識別碼**: RegExLangServ  
  
    -   **產品名稱**: RegExLangServ  
  
    -   **描述**： 規則運算式語言服務。  
  
    -   在下**資產**，按一下**新增**，選取**類型**至**Microsoft.VisualStudio.VsPackage**，將**來源**至**目前方案中的專案**，然後設定**專案**至**RegExLangServ**。  
  
    -   儲存並關閉檔案。  
  
11. 建置方案。 已建置的檔案會部署到 **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**。  
  
12. 開始偵錯。 開啟 Visual Studio 的第二個執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [舊版語言服務的擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)