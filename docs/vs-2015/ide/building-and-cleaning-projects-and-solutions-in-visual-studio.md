---
title: 建置全新的專案的解決方案
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ba3a7c26f56b923b9286a5e2f290502f2765e2b9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753189"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>在 Visual Studio 中建置和清除專案與方案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用本主題中的程序來建置、重建或清除所有或部分專案，或方案中的專案項目。 如需逐步教學課程，請參閱[逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)。

> [!NOTE]
>  您 Visual Studio 版本中的 UI 可能不同於本主題所述，視您目前使用的設定而定。 若要變更設定，請開啟 [工具] 功能表，然後選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>建置、重建或清除整個方案

1.  在方案總管中，選擇或開啟方案。

2.  在功能表列上選擇 [建置]，然後選擇下列其中一個命令︰

    -   選擇 [建置] 或 [建置方案]，只編譯自從最近建置後已變更的那些專案檔案和元件。

        > [!NOTE]
        >  當方案包含多個專案時，[建置] 命令會變成 [建置方案]。

    -   選擇 [重建方案] 以「清除」方案，然後建置所有專案檔和元件。

    -   選擇 [清除方案] 以刪除任何中繼和輸出檔。 只留下專案和元件檔案，即可建立新的中繼檔和輸出檔執行個體。

## <a name="to-build-or-rebuild-a-single-project"></a>建立或重建單一專案

1.  在方案總管中，選擇或開啟專案。

2.  在功能表列上選擇 [建置]，然後選擇 [建置 _ProjectName_] 或 [重建 _ProjectName_]。

    -   選擇 [建置 _ProjectName_ ]，只編譯自從最近建置後已變更的那些專案元件。

    -   選擇 [重建 _ProjectName_] 以「清除」專案，然後建置專案檔和所有專案元件。

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>僅建置啟始專案和其相依性

1. 在功能表列上選擇 [工具] 、[選項] 。

2. 在 [選項] 對話方塊方塊中，展開 [專案和方案] 節點，然後選擇 [建置並執行] 頁面。

    [建置並執行]、[專案和方案]、[選項] 對話方塊隨即開啟。

3. 選取 [僅在執行時建置啟始專案和相依性] 核取方塊。

    如果選取此核取方塊，當您執行下列步驟之一時，只會建置目前的啟始專案和其相依性︰

   - 在功能表列上選擇 **偵錯** > **開始偵錯**(F5)。

   - 在功能表列上選擇 **建置** > **建置方案**(CTRL + SHIFT + B)。

     如果清除此核取方塊，當您執行其中一個上述命令時，會建置所有專案、其相依性及方案檔。 根據預設，會清除此核取方塊。

## <a name="to-build-only-the-selected-visual-c-project"></a>只建置選取的 Visual C++ 專案

1. 選擇 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 專案，然後在功能表列上選擇 [建置]、[僅限專案]，以及下列其中一個命令︰

   - 僅限建置 <專案名稱>

   - 僅限重建 <專案名稱>

   - 僅清除 <專案名稱>

   - 僅連結 <專案名稱>

     這些命令只適用於您選擇的 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 專案，而不建置、重建、清除或連結任何專案相依性或方案檔。 根據您的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 版本，[僅限專案] 子功能表可能包含更多命令。

## <a name="to-compile-multiple-c-project-items"></a>編譯多個 C++ 專案項目

1.  在方案總管中，選擇具有可編譯動作的多個檔案、開啟這些檔案之一的捷徑功能表，然後選擇 [編譯]。

     如果檔案具有相依性，就會將檔案依照相依性順序編譯。 如果檔案需要先行編譯標頭檔，但在您進行編譯時無法使用，則編譯作業會失敗。 編譯作業會使用目前的作用中方案組態。

## <a name="to-stop-a-build"></a>停止建置

1.  執行下列任一步驟：

    -   在功能表列上，選擇 [建置]、[取消]。

    -   選擇 Ctrl + Break 鍵。

## <a name="see-also"></a>另請參閱
 [如何：檢視、 儲存和設定組建記錄檔](../ide/how-to-view-save-and-configure-build-log-files.md)[取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)[編譯和建置](../ide/compiling-and-building-in-visual-studio.md)[了解組建組態](../ide/understanding-build-configurations.md) [偵錯和發行專案組態](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) [C/c + + 建置參考](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)[方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
