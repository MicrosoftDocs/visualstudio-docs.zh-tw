---
title: 擴充隔離式 Shell |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea55039de769598b26868727a93cfa11726e4838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838918"
---
# <a name="extending-the-isolated-shell"></a>擴充獨立模式 Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉由將 VSPackage、Managed Extensibility Framework (MEF) 元件部分或泛型 VSIX 專案加入至您的獨立 shell 應用程式，來擴充 Visual Studio 隔離式 shell。  
  
> [!NOTE]
> 下列步驟會 presuppose 您已使用 Visual Studio Shell 隔離專案範本建立基本的獨立模式 shell 應用程式。 如需此專案範本的詳細資訊，請參閱 [逐步解說：建立基本的獨立模式 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio Package 專案範本位置  
 Visual Studio Package 專案範本位在 [新增專案] **** 對話方塊的三個不同位置：  
  
1. 在 **Visual Basic**的 **擴充**性下。 專案的預設語言為 Visual Basic。  
  
2. **Visual c #** 下**的擴充性。** 專案的預設語言為 C#。  
  
3. 在 [ **其他專案類型**] 下，可 **延伸**。 專案的預設語言為 C++。  
  
## <a name="adding-a-vspackage"></a>新增 VSPackage  
 您可以將 VSPackage 新增至您的獨立 shell 應用程式。 下列步驟示範如何建立可新增功能表命令的。  
  
#### <a name="to-add-a-new-vspackage"></a>若要加入新的 VSPackage  
  
1. 新增名為的 Visual Studio 封裝專案 `MenuCommandsPackage` 。  
  
2. 在嚮導的 [ **基本 VSPackage 資訊** ] 頁面上，將 [ **公司名稱** ] 設定為 `Fabrikam` ，並將 [ **VSPackage 名稱** ] 設定為 `FabrikamMenuCommands` 。 選擇 [下一步]**** 按鈕。  
  
3. 在下一個頁面上，選取 [ **功能表命令** ]，然後選擇 **[下一步]**。  
  
4. 在下一個頁面上，將 [**命令名稱**] 設定為 `Fabrikam Command` ，然後選擇 [ **Command ID** `cmdidFabrikamCommand` **下一步]**。  
  
5. 在 [ **選取測試專案選項** ] 頁面上，清除 [測試選項]，然後選擇 [ **完成]** 按鈕。  
  
6. 在 ShellExtensionsVSIX 專案中，開啟 extension.vsixmanifest 檔案。  
  
     [ **資產** ] 區段應該包含 VSShellStub. AboutBoxPackage 專案的專案。  
  
7. 選擇 [ **新增** ] 按鈕。  
  
8. 在 [ **加入新資產** ] 視窗的 [ **類型** ] 清單中，選取 [ **VisualStudio. VsPackage**]。  
  
9. 在 [ **來源** ] 清單中，確認已選取 **[目前方案中的專案** ]。 在 [ **專案** ] 清單方塊中，選取 [ **MenuCommandsPackage**]。  
  
10. 儲存並關閉檔案。  
  
11. 重建方案，並開始對隔離式 shell 進行偵錯工具。  
  
12. 在功能表列上，依序選擇 [ **工具** ] 功能表和 [ **Fabrikam 命令**]。  
  
     應該會出現訊息方塊。  
  
13. 停止偵錯工具。  
  
## <a name="adding-a-mef-component-part"></a>新增 MEF 元件部分  
 下列步驟示範如何將 MEF 元件元件新增至您的獨立 shell 應用程式。  
  
#### <a name="to-add-a-mef-component"></a>新增 MEF 元件  
  
1. 在 [ **加入新專案** ] 對話方塊的 [ **Visual c #** **]、[** 擴充性] 下，使用 [ **編輯器邊界** ] 範本來加入專案。 將它命名為 `ShellEditorMargin`  
  
2. 在 ShellExtensionsVSIX 專案中，開啟設計檢視中的 extension.vsixmanifest 檔案，而不是程式碼視圖。  
  
3. 在 `Asset` 區段中，選擇 [ **加入內容**]。  
  
4. 在 [ **加入新資產** ] 視窗的 [ **類型** ] 清單中，選取 [ **VisualStudio. [microsoft.visualstudio.mefcomponent]**]。  
  
5. 在 [ **來源** ] 清單中，確認已選取 **[目前方案中的專案** ]。 在 [ **專案** ] 清單方塊中，選取 [ **ShellEditorMargin**]。  
  
6. 儲存並關閉檔案。  
  
7. 重建方案，並開始對隔離式 shell 進行偵錯工具。  
  
8. 開啟文字檔。  
  
     包含 "Hello world！" 文字的綠色邊界 應該會顯示在文字檔視窗的底部。  
  
9. 停止偵錯工具。  
  
## <a name="adding-a-generic-vsix-project"></a>加入泛型 VSIX 專案  
  
#### <a name="to-add-a-generic-vsix-project"></a>若要加入泛型 VSIX 專案  
  
1. 在 [ **加入新專案** ] 對話方塊的 [ **Visual c #**]、[擴充性] **下，使用** **VSIXProject** 範本來加入專案。 將它命名為 `EmptyVSIX`  
  
2. 在 ShellExtensionsVSIX 專案中，開啟設計檢視中的 extension.vsixmanifest 檔案，而不是程式碼視圖。  
  
3. 在 `Assets` 區段中，選擇 [ **新增**]。  
  
4. 在 [ **加入新資產** ] 視窗的 [ **類型** ] 清單中，選取您要新增的內容類型。  
  
5. 在 [ **來源**] 中，確認已選取 [ **目前方案中的專案** ] 選項。 在清單方塊中，選取 VSIX 專案的名稱。  
  
6. 儲存並關閉檔案。  
  
7. 如果這個專案包含已編譯的程式碼，您必須編輯專案，讓元件包含在輸出中。  
  
    1. 卸載 VSIX 專案，然後開啟專案檔。  
  
    2. 在第一個 `<PropertyGroup>` 區塊中，將的值變更 `<CopyBuildOutputToOutputDirectory>` 為 `true` 。  
  
    3. 儲存並重載專案。  
  
8. 建置並執行解決方案。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰建立基本的 Isolated Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
