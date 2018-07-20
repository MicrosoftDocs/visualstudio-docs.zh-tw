---
title: 設定偵錯和發行組態 |Microsoft Docs
ms.custom: ''
ms.date: 04/10/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea27fdccaadc70f22d9c9c02d75ddef98a11be13
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153094"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>設定偵錯和發行 Visual Studio 中的組態
Visual Studio 專案針對您的程式具有不同的版本和偵錯組態。 依照名稱提示，您可以建置用來偵錯的偵錯版本，和最後發行散發的發行版本。  
  
程式的偵錯組態會使用完整符號偵錯資訊，在沒有最佳化的情況下進行編譯。 最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。  
  
程式的發行組態不包含符號偵錯資訊，而且會完全最佳化。 偵錯資訊可產生.pdb 檔案[編譯器選項而定](#BKMK_symbols_release)所使用的。 建立.pdb 檔案可能會非常有用，如果您日後必須偵錯您的發行版本。  
  
如需組建組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。  
  
您可以變更組建組態從**建置**功能表、 從工具列中，或在專案屬性頁中。 專案屬性頁因語言而異。 下列程序示範如何從功能表和工具列變更組建組態。 如需如何變更不同語言中的專案組建組態的詳細資訊，請參閱 < 另請參閱下一節。  
  
## <a name="change-the-build-configuration"></a>變更組建組態  
  
1.  從**建置**功能表上，選取**Configuration Manager**，然後選取**偵錯**或是**發行**。  
  
2.  在工具列上，選擇 **偵錯**或是**發行**從**方案組態**清單方塊。  
  
     ![工具列組建組態](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     在 Express 版中無法使用此工具列。 您可以使用**建置方案 F6**並**開始偵錯 F5**功能表項目選擇組態。

## <a name="BKMK_symbols_release"></a>產生組建的符號 (.pdb) 檔

對於大部分的專案類型，.pdb 檔案產生的預設值為這兩個偵錯和發行組建，但預設設定是您的特定專案類型和 Visual Studio 版本而有所不同。 您可以設定編譯器是否會產生.pdb 檔案以及哪一種要包含偵錯資訊。

> [!IMPORTANT] 
> 偵錯工具只會載入與可執行檔建置時所建立的 .pdb 檔案完全相同之可執行檔的 .pdb 檔案 (也就是說，.pdb 必須是原始 .pdb 檔案或該檔案的複本)。 如需詳細資訊，請參閱 [Why does Visual Studio require debugger symbol files to exactly match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

每個專案類型可能會有不同的方式設定這些選項。

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>產生 C#、 ASP.NET 或 Visual Basic 專案的符號檔

如需 C# 中的偵錯組態的專案設定的詳細資訊，請參閱[專案 C# 偵錯組態設定](../debugger/project-settings-for-csharp-debug-configurations.md)。 Visual basic，請參閱[本主題](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)。

1. 以滑鼠右鍵按一下方案總管] 中的專案，然後選擇 [**屬性**。

2. 選擇**發行**或是**偵錯**來建立**Configuration**清單。

2. 選擇**建置**設定，然後按一下**進階** 按鈕。

    在 Visual Basic 中，您可以選擇**編譯**設定而**進階編譯選項**按鈕。

3. 選擇**完整**，**可攜式**，或**pdb_only**中**偵錯資訊**清單方塊 (**產生偵錯資訊**在 Visual Basic 中)。

    可移植的格式是最新的跨平台格式，適用於.NET Core。 如需有關選項的詳細資訊，請參閱 <<c0> [ 進階建置設定對話方塊 (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)。

    ![在 C# 中的組建產生 Pdb](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. 建置您的專案。

    可執行檔或主要輸出檔相同資料夾中建立的符號檔。

### <a name="generate-symbol-files-for-a-c-project"></a>產生 c + + 專案的符號的檔

1. 以滑鼠右鍵按一下方案總管] 中的專案，然後選擇 [**屬性**。

2. 選擇**發行**或是**偵錯**來建立**Configuration**清單。

2. 底下**連結器 > 偵錯**，選取所需的選項**產生偵錯資訊**。

    如需 c + + 中的偵錯組態的專案設定的詳細資訊，請參閱[c + + 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)。

4. 設定產生程式資料庫檔案的選項

    在大部分的 c + + 專案中，預設值是`$(OutDir)$(TargetName).pdb`，如此就會產生.pdb 檔案的輸出資料夾中。

    ![C + + 中的組建產生 Pdb](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. 建置您的專案。

    可執行檔或主要輸出檔相同資料夾中建立的符號檔。
  
## <a name="see-also"></a>另請參閱  
 [在 Visua Studio debugger 中指定符號 (.pdb) 檔和原始程式檔](../debugger/debugger-settings-and-preparation.md)  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [C + + 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C# 偵錯設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)
