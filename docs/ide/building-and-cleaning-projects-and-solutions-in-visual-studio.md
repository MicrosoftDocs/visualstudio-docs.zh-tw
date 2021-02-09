---
title: 建置和清除專案與方案
description: 瞭解如何建立、重建或清除方案中的所有專案或專案專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ba53fefcc5d29cb47bd3a6912ad7af34dd8deabb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850382"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>在 Visual Studio 中建置和清除專案與方案

您可以使用本主題中的程序來建置、重建或清除所有或部分專案，或方案中的專案項目。 如需逐步教學課程，請參閱[逐步解說︰建置應用程式](../ide/walkthrough-building-an-application.md)。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[在 Visual Studio for Mac 中建置和清除專案和方案](/visualstudio/mac/building-and-cleaning-projects-and-solutions)。

> [!NOTE]
> 您 Visual Studio 版本中的 UI 可能不同於本主題所述，視您目前使用的設定而定。 若要變更您的設定 (例如變更為 [一般] 或 [Visual C++] 設定)，請選擇 [工具] > [匯入和匯出設定]，然後選擇 [重設所有設定]。

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>建置、重建或清除整個方案

1. 在方案總管中，選擇或開啟方案。

2. 在功能表列上選擇 [建置]，然後選擇下列其中一個命令︰

    - 選擇 [建置] 或 [建置方案]，只編譯自從最近建置後已變更的那些專案檔案和元件。

        > [!NOTE]
        > 當方案包含多個專案時，[建置] 命令會變成 [建置方案]。

    - 選擇 [重建方案] 以「清除」方案，然後建置所有專案檔和元件。

    - 選擇 [清除方案] 以刪除任何中繼和輸出檔。 只留下專案和元件檔案，即可建立新的中繼檔和輸出檔執行個體。

## <a name="to-build-or-rebuild-a-single-project"></a>建立或重建單一專案

1. 在方案總管中，選擇或開啟專案。

2. 在功能表列上，選擇 **[組建**]，然後選擇 **[組建***專案名稱*] 或 [**重建***專案名稱*]。

    - 選擇 **組建***專案名稱*，只建立自最新組建之後變更的專案元件。

    - 選擇 [ **重建** 專案 *名稱* ] 以「清除」專案，然後建立專案檔和所有專案元件。

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>僅建置啟始專案和其相依性

1. 在功能表列上，選擇 [**工具**  >  **選項**]。

2. 在 [選項] 對話方塊方塊中，展開 [專案和方案] 節點，然後選擇 [建置並執行] 頁面。

     [**組建和執行**  >  **專案和方案**  >  **選項**] 對話方塊隨即開啟。

3. 選取 [僅在執行時建置啟始專案和相依性] 核取方塊。

     如果選取此核取方塊，當您執行下列步驟之一時，只會建置目前的啟始專案和其相依性︰

    - 在功能表列上，選擇 [ **Debug**  >  **開始**] (**F5**) 。

    - 在功能表列上，選擇 [**組建**  >  **組建方案**] (**Ctrl** + **Shift** + **B**) 。

    如果清除此核取方塊，當您執行其中一個上述命令時，會建置所有專案、其相依性及方案檔。 根據預設，會清除此核取方塊。

## <a name="to-build-only-the-selected-visual-c-project"></a>只建置選取的 Visual C++ 專案

選擇 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 專案，然後在功能表列上，選擇 [僅 **建立**  >  **專案**] 和下列其中一個命令：

- 僅限建置 **<專案名稱>** 

- 僅限重建 **<專案名稱>** 

- 僅清除 **<專案名稱>** 

- 僅連結 **<專案名稱>** 

這些命令只適用於您選擇的 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 專案，而不建置、重建、清除或連結任何專案相依性或方案檔。 根據您的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本，[僅限專案] 子功能表可能包含更多命令。

## <a name="to-compile-multiple-c-project-items"></a>編譯多個 C++ 專案項目

在方案總管中，選擇具有可編譯動作的多個檔案、開啟這些檔案之一的捷徑功能表，然後選擇 [編譯]。

如果檔案具有相依性，就會將檔案依照相依性順序編譯。 如果檔案需要先行編譯標頭檔，但在您進行編譯時無法使用，則編譯作業會失敗。 編譯作業會使用目前的作用中方案組態。

## <a name="to-stop-a-build"></a>停止建置

執行下列任一步驟：

- 在功能表列上，選取 [**組建**  >  **取消**]。

- 按下 **Ctrl** + **Break**。

## <a name="see-also"></a>另請參閱

- [如何：查看、儲存和設定組建記錄檔](../ide/how-to-view-save-and-configure-build-log-files.md)
- [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)
- [編譯和建立](../ide/compiling-and-building-in-visual-studio.md)
- [了解組建組態](../ide/understanding-build-configurations.md)
- [如何：設定偵錯和發行設定](../debugger/how-to-set-debug-and-release-configurations.md)
- [C/c + + 建立參考](/cpp/build/reference/c-cpp-building-reference)
- [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)
- [方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
- [建置和清除專案與方案 (Visual Studio for Mac)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)
