---
title: 設定偵錯和發行組態 |Microsoft Docs
ms.custom: ''
ms.date: 10/05/2018
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
ms.openlocfilehash: 18689a82fe2ae7c66eb8e8d6ef9bd115e2950cac
ms.sourcegitcommit: 50b19010b2e2b4736835350710e2edf93b980b56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2018
ms.locfileid: "49073985"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>設定偵錯和發行 Visual Studio 中的組態

Visual Studio 專案針對您的程式具有不同的版本和偵錯組態。 建立偵錯的偵錯版本和最後發行散發的發行版本。

在偵錯組態中，您的程式會使用完整符號偵錯資訊，在沒有最佳化編譯。 最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。

您的程式的發行組態沒有符號偵錯資訊，而且會完全最佳化。 偵錯資訊可產生.pdb 檔案[編譯器選項而定](#BKMK_symbols_release)所使用的。 建立.pdb 檔案可能會很有用，如果您日後必須偵錯您的發行版本。

如需組建組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。

您可以變更組建組態從**建置**功能表、 從工具列中，或在專案屬性頁中。 專案屬性頁因語言而異。 下列程序示範如何從功能表和工具列變更組建組態。 如需如何變更不同語言中的專案組建組態的詳細資訊，請參閱[另請參閱](#see-also)下一節。

## <a name="change-the-build-configuration"></a>變更組建組態

若要變更組建組態，可能是：

* 從**建置**功能表上，選取**Configuration Manager**，然後選取**偵錯**或是**發行**。

或

* 在工具列上，選擇 **偵錯**或是**發行**從**方案組態**清單。

  ![工具列組建組態](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>產生組建的符號 (.pdb) 檔

您可以選擇產生符號 (.pdb) 檔，以及偵錯應包含的資訊。 對於大部分的專案類型，編譯器會產生符號檔預設為偵錯和發行組建，而其他預設設定會因專案類型] 和 [Visual Studio 版本。

> [!IMPORTANT]
> 偵錯工具只會載入與可執行檔建置時所建立的 .pdb 檔案完全相同之可執行檔的 .pdb 檔案 (也就是說，.pdb 必須是原始 .pdb 檔案或該檔案的複本)。 如需詳細資訊，請參閱[為什麼 Visual Studio 需要建置的二進位檔完全相符項目偵錯工具符號檔案？](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

每個專案類型可能會有不同的方式設定這些選項。

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>產生 C#、 ASP.NET 或 Visual Basic 專案的符號檔

如需以 C# 或 Visual Basic 的偵錯組態的專案設定的詳細資訊，請參閱[偵錯組態的專案設定，適用於 C#](../debugger/project-settings-for-csharp-debug-configurations.md)或[Visual basic 專案設定偵錯組態](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. 在 [方案總管] 中選取專案。

2. 選取 **屬性**圖示 (或按**Alt + Enter**)。

3. 在側邊窗格中，選擇**建置**(或**編譯**Visual Basic 中)。

4. 在 **組態**清單中，選擇**偵錯**或是**版本**。

5. 選取 [**進階**] 按鈕 (或**進階編譯選項**Visual Basic 中的按鈕)。

6. 在 **偵錯資訊**清單 (或**產生偵錯資訊**Visual Basic 中的清單)，選擇**完整**，**僅限 Pdb**，或**可攜式**。

   可移植的格式是最新的跨平台格式，適用於.NET Core。 如需有關選項的詳細資訊，請參閱 <<c0> [ 進階建置設定對話方塊 (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)。

   ![在 C# 中的組建產生 Pdb](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. 建置您的專案。

   編譯器會建立可執行檔或主要輸出檔相同資料夾中的符號檔。

### <a name="generate-symbol-files-for-a-c-project"></a>產生 c + + 專案的符號的檔

1. 在 [方案總管] 中選取專案。

2. 選取 **屬性**圖示 (或按**Alt + Enter**)。

3. 在 **組態**清單中，選擇**偵錯**或是**版本**。

4. 在側邊窗格中，選擇**連結器 > 偵錯**，然後選取 選項**產生偵錯資訊**。

   如需 c + + 中的偵錯組態的專案設定的詳細資訊，請參閱[偵錯組態的 c + + 專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)。

5. 設定選項**產生程式資料庫檔**。

   在大部分的 c + + 專案中，預設值是`$(OutDir)$(TargetName).pdb`，如此就會產生.pdb 檔案的輸出資料夾中。

   ![C + + 中的組建產生 Pdb](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. 建置您的專案。

   編譯器會建立可執行檔或主要輸出檔相同資料夾中的符號檔。

## <a name="see-also"></a>另請參閱
 
[在 Visual Studio debugger 中指定符號 (.pdb) 檔和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
[偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)<br/>
[C++ 偵錯設定的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
[C# 偵錯組態的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
[Visual Basic 偵錯設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
[如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)
