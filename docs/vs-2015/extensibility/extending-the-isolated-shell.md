---
title: 擴充 Isolated 的 Shell |Microsoft Docs
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
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc700e0a1b8753a26067eff90df9ff58765de8d1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792017"
---
# <a name="extending-the-isolated-shell"></a>擴充 Isolated 的 Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以擴充 Visual Studio 隔離 shell 藉由將 VSPackage、 Managed Extensibility Framework (MEF) 元件的組件或泛型的 VSIX 專案新增至您的獨立的 shell 應用程式。  
  
> [!NOTE]
>  下列步驟 presuppose 已使用 Visual Studio Shell 獨立模式的專案範本，來建立基本的 isolated 的 shell 應用程式。 如需有關這個專案範本的詳細資訊，請參閱 <<c0> [ 逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio Package 專案範本位置  
 Visual Studio Package 專案範本位在 [新增專案]  對話方塊的三個不同位置：  
  
1.  底下**Visual Basic**，**擴充性**。 專案的預設語言為 Visual Basic。  
  
2.  底下**Visual C#**，**擴充性**。 專案的預設語言為 C#。  
  
3.  底下**其他專案類型**，**擴充性**。 專案的預設語言為 C++。  
  
## <a name="adding-a-vspackage"></a>加入 VSPackage  
 您可以加入您的獨立的 shell 應用程式的 VSPackage。 下列步驟示範如何建立一個會將功能表命令。  
  
#### <a name="to-add-a-new-vspackage"></a>若要新增新的 VSPackage  
  
1.  新增名為 Visual Studio Package 專案`MenuCommandsPackage`。  
  
2.  上**基本 VSPackage 資訊**精靈的頁面設定**公司名稱**來`Fabrikam`並**VSPackage 名稱**至`FabrikamMenuCommands`。 選擇 [下一步] 按鈕。  
  
3.  在下一步 頁面上，選取**功能表命令**，然後選擇**下一步**。  
  
4.  在下一步 頁面上，設定**命令名稱**來`Fabrikam Command`和**命令 ID**來`cmdidFabrikamCommand`，然後選擇**下一步**。  
  
5.  在 **選取測試專案選項**頁面上，清除測試選項，然後選擇**完成** 按鈕。  
  
6.  在 ShellExtensionsVSIX 專案中，開啟 source.extension.vsixmanifest 檔案中。  
  
     **資產**區段應包含 VSShellStub.AboutBoxPackage 專案的項目。  
  
7.  選擇**新增** 按鈕。  
  
8.  在 [**加入新資產**] 視窗，請在**型別**清單中，選取**Microsoft.VisualStudio.VsPackage**。  
  
9. 在 **來源**清單中，請確定**目前方案中的專案**已選取。 在 **專案**清單方塊中，選取**MenuCommandsPackage**。  
  
10. 儲存並關閉檔案。  
  
11. 重建方案，並開始偵錯 isolated 的 shell。  
  
12. 在功能表列上選擇 **工具**功能表，然後**Fabrikam 命令**。  
  
     訊息方塊應該會出現。  
  
13. 停止偵錯應用程式。  
  
## <a name="adding-a-mef-component-part"></a>加入 MEF 元件組件  
 下列步驟示範如何將 MEF 元件組件新增至您的獨立的 shell 應用程式。  
  
#### <a name="to-add-a-mef-component"></a>若要新增為 MEF 元件  
  
1.  在 **加入新的專案**對話方塊的  **Visual C#**，**擴充性**，使用**編輯器邊界**範本加入專案。 將它命名為 `ShellEditorMargin`。  
  
2.  在 ShellExtensionsVSIX 專案中，開啟 Source.extension.vsixmanifest 檔案中，在 [設計] 檢視中，不是程式碼檢視中。  
  
3.  在 `Asset`區段中，選擇**加入內容**。  
  
4.  在 [**加入新資產**] 視窗，請在**型別**清單中，選取**Microsoft.VisualStudio.MefComponent**。  
  
5.  在 **來源**清單中，請確定**目前方案中的專案**已選取。 在 **專案**清單方塊中，選取**ShellEditorMargin**。  
  
6.  儲存並關閉檔案。  
  
7.  重建方案，並開始偵錯 isolated 的 shell。  
  
8.  開啟文字檔案。  
  
     綠色的邊界，其中包含文字"Hello world ！" 應該會顯示在視窗底部的文字檔案。  
  
9. 停止偵錯應用程式。  
  
## <a name="adding-a-generic-vsix-project"></a>新增泛型的 VSIX 專案  
  
#### <a name="to-add-a-generic-vsix-project"></a>若要加入泛型的 VSIX 專案  
  
1.  在 **加入新的專案**對話方塊的  **Visual C#**，**擴充性**，使用**VSIXProject**範本加入專案。 將它命名為 `EmptyVSIX`。  
  
2.  在 ShellExtensionsVSIX 專案中，開啟 Source.extensions.vsixmanifest 檔案在 [設計] 檢視中，不是程式碼檢視中。  
  
3.  在 `Assets`區段中，選擇**新增**。  
  
4.  在 **加入新資產**視窗，請在**型別**清單中，選取您想要新增的內容類型。  
  
5.  在 **來源**，請確定**目前方案中的專案**選項。 在清單方塊中，選取您的 VSIX 專案的名稱。  
  
6.  儲存並關閉檔案。  
  
7.  如果此專案包含已編譯程式碼，您必須編輯專案，以便在輸出中包含組件。  
  
    1.  卸載 VSIX 專案，然後開啟專案檔。  
  
    2.  在第一個`<PropertyGroup>`區塊中，變更的值`<CopyBuildOutputToOutputDirectory>`至`true`。  
  
    3.  儲存並重新載入專案。  
  
8.  建置並執行方案。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰建立基本的 Isolated Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

