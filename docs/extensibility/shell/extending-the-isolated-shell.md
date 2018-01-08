---
title: "擴充 Isolated 的 Shell |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 04257a6ea4bfb3dbe788ba48ee3077b1847b000d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-isolated-shell"></a>擴充獨立的 Shell
您可以擴充 Visual Studio isolated shell 將 VSPackage、 Managed Extensibility Framework (MEF) 元件的組件或泛型的 VSIX 專案加入至您的獨立的 shell 應用程式。  
  
> [!NOTE]
>  下列步驟 presuppose 您已使用 Visual Studio Shell 外掛式主控專案範本建立基本獨立的 shell 應用程式。 如需有關這個專案範本的詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio Package 專案範本位置  
 Visual Studio Package 專案範本位在 [新增專案]  對話方塊的三個不同位置：  
  
1.  在下**Visual Basic**，**擴充性**。 專案的預設語言為 Visual Basic。  
  
2.  在下**Visual C#**，**擴充性**。 專案的預設語言為 C#。  
  
3.  在下**其他專案類型**，**擴充性**。 專案的預設語言為 C++。  
  
## <a name="adding-a-vspackage"></a>加入 VSPackage  
 您可以加入 VSPackage 獨立的 shell 應用程式。 下列步驟示範如何建立一個會將功能表命令。  
  
#### <a name="to-add-a-new-vspackage"></a>若要加入新的 VSPackage  
  
1.  加入名為的 Visual Studio Package 專案`MenuCommandsPackage`。  
  
2.  在**基本 VSPackage 資訊**頁面在精靈的設定**公司名稱**至`Fabrikam`和**VSPackage 名稱**至`FabrikamMenuCommands`。 選擇 [下一步] 按鈕。  
  
3.  在下一個頁面上，選取**功能表命令**，然後選擇 **下一步**。  
  
4.  在下一個頁面上，設定**命令名稱**至`Fabrikam Command`和**命令 ID**至`cmdidFabrikamCommand`，然後選擇 **下一步**。  
  
5.  在**選取測試專案選項**頁面上，清除測試選項，然後選擇**完成** 按鈕。  
  
6.  ShellExtensionsVSIX 專案中，開啟 source.extension.vsixmanifest 檔案。  
  
     **資產**部分應該包含 VSShellStub.AboutBoxPackage 專案的項目。  
  
7.  選擇**新增** 按鈕。  
  
8.  在**加入新資產**視窗，請在**類型**清單中，選取**Microsoft.VisualStudio.VsPackage**。  
  
9. 在**來源**清單中，請確定**目前方案中的專案**已選取。 在**專案**清單方塊中，選取**MenuCommandsPackage**。  
  
10. 儲存並關閉檔案。  
  
11. 重建方案，並開始偵錯在 isolated 的 shell。  
  
12. 在功能表列上選擇 **工具**功能表，然後**Fabrikam 命令**。  
  
     應該會出現訊息方塊。  
  
13. 停止偵錯應用程式。  
  
## <a name="adding-a-mef-component-part"></a>加入 MEF 元件組件  
 下列步驟顯示如何將 MEF 元件組件加入至您的獨立的 shell 應用程式。  
  
#### <a name="to-add-a-mef-component"></a>若要加入為 MEF 元件  
  
1.  在**加入新的專案**對話方塊的  **Visual C#**，**擴充性**，使用**編輯器邊界**將專案加入範本。 將它命名為 `ShellEditorMargin`。  
  
2.  ShellExtensionsVSIX 專案中，開啟 Source.extension.vsixmanifest 檔案中的，在設計檢視中，程式碼檢視。  
  
3.  在`Asset`區段中，選擇**將內容加入**。  
  
4.  在**加入新資產**視窗，請在**類型**清單中，選取**Microsoft.VisualStudio.MefComponent**。  
  
5.  在**來源**清單中，請確定**目前方案中的專案**已選取。 在**專案**清單方塊中，選取**ShellEditorMargin**。  
  
6.  儲存並關閉檔案。  
  
7.  重建方案，並開始偵錯在 isolated 的 shell。  
  
8.  開啟文字檔案。  
  
     包含文字"Hello world ！"綠色邊界 應該會顯示在文字檔案視窗的底部。  
  
9. 停止偵錯應用程式。  
  
## <a name="adding-a-generic-vsix-project"></a>加入泛型 VSIX 專案  
  
#### <a name="to-add-a-generic-vsix-project"></a>若要加入 泛型 VSIX 專案  
  
1.  在**加入新的專案**對話方塊的  **Visual C#**，**擴充性**，使用**VSIXProject**將專案加入範本。 將它命名為 `EmptyVSIX`。  
  
2.  ShellExtensionsVSIX 專案中，開啟 Source.extensions.vsixmanifest 檔案在設計檢視中，程式碼檢視。  
  
3.  在`Assets`區段中，選擇**新增**。  
  
4.  在**加入新資產**視窗，請在**類型**清單中，選取您想要新增的內容類型。  
  
5.  在**來源**，請確定**目前方案中的專案**選取選項。 在清單方塊中，選取 VSIX 專案的名稱。  
  
6.  儲存並關閉檔案。  
  
7.  如果此專案包含已編譯程式碼，您必須編輯專案，以便在輸出中包含組件。  
  
    1.  卸載 VSIX 專案，並開啟專案檔。  
  
    2.  在第一個`<PropertyGroup>`封鎖，請將值變更`<CopyBuildOutputToOutputDirectory>`至`true`。  
  
    3.  儲存並重新載入專案。  
  
8.  建置並執行方案。  
  
## <a name="see-also"></a>請參閱  
 [逐步解說︰建立基本的 Isolated Shell 應用程式](walkthrough-creating-a-basic-isolated-shell-application.md)