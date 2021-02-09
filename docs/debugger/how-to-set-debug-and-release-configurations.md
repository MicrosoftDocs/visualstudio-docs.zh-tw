---
title: 設定 debug 和 release 設定 |Microsoft Docs
description: 在 Visual Studio 中設定 debug 和 release 設定。 您會建立偵錯工具的偵錯工具版本，以及最終發行版本散發的發行版本。
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6f96570f517d24492ecdacb4e45450fa7b7ba1cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908395"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>在 Visual Studio 中設定偵錯和發行組態

Visual Studio 專案針對您的程式具有不同的版本和偵錯組態。 您會建立偵錯工具的偵錯工具版本，以及最終發行版本散發的發行版本。

在 [偵錯工具] 設定中，您的程式會使用完整符號的 debug 資訊進行編譯，而不是優化 最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。

您程式的發行設定沒有符號的 debug 資訊，而且已完全優化。 針對 managed 程式碼和 c + + 程式碼，您可以根據所使用 [的編譯器選項](#BKMK_symbols_release) ，在 .pdb 檔案中產生 debug 資訊。 如果您稍後需要對發行版本進行偵錯工具，建立 .pdb 檔案可能會很有用。

如需組建組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。

您可以從 [建置] 功能表、從工具列，或在專案的屬性頁中變更組建組態。 專案屬性頁因語言而異。 下列程序示範如何從功能表和工具列變更組建組態。 如需有關如何以不同語言變更專案中之組建設定的詳細資訊，請參閱下面的「另 [請參閱](#see-also) 」一節。

## <a name="change-the-build-configuration"></a>變更組建設定

若要變更組建設定，請執行下列其中一項：

* 從 [ **組建** ] 功能表中，選取 [ **設定管理員**]，然後選取 [ **Debug** ] 或 [ **發行**]。

或

* 在工具列的 [解決方案組態] 清單中，選擇 [偵錯] 或 [發行]。

  ![工具列組建設定](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="generate-symbol-pdb-files-for-a-build-c-c-visual-basic-f"></a><a name="BKMK_symbols_release"></a>產生組建的符號 ( .pdb) 檔案 (c #、c + +、Visual Basic、F # ) 

您可以選擇產生符號 ( .pdb) 檔案，以及要包含哪些調試資訊。 針對大部分的專案類型，編譯器預設會針對 debug 和發行組建產生符號檔，而其他預設設定會依專案類型和 Visual Studio 版本而不同。

> [!IMPORTANT]
> 偵錯工具只會載入與可執行檔建置時所建立的 .pdb 檔案完全相同之可執行檔的 .pdb 檔案 (也就是說，.pdb 必須是原始 .pdb 檔案或該檔案的複本)。 如需詳細資訊，請參閱 [為什麼 Visual Studio 需要偵錯工具符號檔才能完全符合用來建立它們的二進位檔案？](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)。

每個專案類型可能會有不同的方式來設定這些選項。

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>產生 c #、ASP.NET 或 Visual Basic 專案的符號檔

如需有關 c # 或 Visual Basic 中的 debug 設定之專案設定的詳細資訊，請參閱 [c # debug 設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md) 或 [Visual Basic Debug](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)設定的專案設定。

1. 在 [方案總管] 中選取專案。

2. 選取 [ **屬性** ] 圖示 (或按 **Alt + Enter**) 。

3. 在側邊窗格中，選擇 [ **組建** (] 或 [在 Visual Basic) **編譯** ]。

4. 在 [設定 **] 清單中，選擇 [** **Debug** ] 或 [ **發行**]。

5. 在 Visual Basic) 中選取 [ **advanced** ] 按鈕 (或 [ **advanced Compile 選項** ] 按鈕。

6. 在 [ **調試資訊** 清單 (或 Visual Basic) 中的 [ **產生調試資訊** ] 清單中，選擇 [ **完整**]、[ **僅限 Pdb**] 或 [ **可移植**]。

   可移植格式是適用于 .NET Core 的最新跨平臺格式。 如需選項的詳細資訊，請參閱 [ (c # ) 的 [Advanced Build Settings] 對話方塊 ](../ide/reference/advanced-build-settings-dialog-box-csharp.md)。

   ![為 C 中的組建產生 Pdb#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. 建置您的專案。

   編譯器會在與可執行檔或主要輸出檔案相同的資料夾中，建立符號檔 (s) 。

### <a name="generate-symbol-files-for-a-c-project"></a>產生 c + + 專案的符號檔

1. 在 [方案總管] 中選取專案。

2. 選取 [ **屬性** ] 圖示 (或按 **Alt + Enter**) 。

3. 在 [設定 **] 清單中，選擇 [** **Debug** ] 或 [ **發行**]。

4. 在側邊窗格中，選擇 [ **連結器 > 的調試** 程式]，然後選取 [ **產生偵錯工具資訊** 的選項]。

   如需 c + + 中的 debug 設定之專案設定的詳細資訊，請參閱 [c + + 偵錯工具的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)。

5. 設定 **產生程式資料庫** 檔案的選項。

   在大部分的 c + + 專案中，預設值是 `$(OutDir)$(TargetName).pdb` ，它會在輸出檔案夾中產生 .pdb 檔。

   ![在 c + + 中產生組建的 Pdb](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. 建置您的專案。

   編譯器會在與可執行檔或主要輸出檔案相同的資料夾中，建立符號檔 (s) 。

## <a name="see-also"></a><a name="see-also"></a>另請參閱

- [在 Visual Studio 偵錯工具中指定 ( .pdb) 檔案和原始程式檔的符號](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)<br/>
- [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [C # 偵錯工具設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [如何：建立和編輯設定](../ide/how-to-create-and-edit-configurations.md)