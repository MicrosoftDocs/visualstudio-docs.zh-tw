---
title: 改善效能的祕訣
description: 瞭解如何優化某些 Visual Studio 可能不會用來協助改善效能的功能。
ms.custom: SEO-VS-2020
ms.date: 12/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e53a2e3b1a65e496b4ead3d3bca0e8b0254c39e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873862"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Visual Studio 效能祕訣和訣竅

Visual Studio 效能建議是要針對記憶體不足的情況，但這極少發生。 在這些情況下，您可以最佳化可能不會使用的特定 Visual Studio 功能。 下列祕訣不適合作為一般建議。

> [!NOTE]
> 如果您因為記憶體問題而無法使用此產品，請透過 [意見反應工具](../ide/how-to-report-a-problem-with-visual-studio.md)讓我們知道。

## <a name="use-a-64-bit-os"></a>使用 64 位元 OS

如果您將系統從 32 位元版本的 Windows 升級至 64 位元版本，請將 Visual Studio 可用的虛擬記憶體數量從 2 GB 擴充為 4 GB。 這可讓 Visual Studio 處理更大量的工作負載，即使是 32 位元處理序亦然。

如需詳細資訊，請參閱[記憶體限制](/windows/desktop/Memory/memory-limits-for-windows-releases)和 [Use /LARGEADDRESSAWARE on 64-bit Windows](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/) (在 64 位元 Windows 上使用 /LARGEADDRESSAWARE)。

## <a name="disable-automatic-file-restore"></a>停用自動檔案還原

Visual Studio 會自動重新開啟在上一個工作階段保持開啟的文件。 這可能會讓載入解決方案的時間延長達 30% 以上，依開啟的專案類型及文件而定。 Windows Forms 及 XAML 這類設計工具和某些 JavaScript 與 typescript 檔案可能會很慢才開啟。

Visual Studio 會在自動文件還原導致解決方案載入時間明顯變慢時，以黃色的列通知您。 您可遵循下列步驟停用自動檔案重新開啟：

1. 選取 [**工具**  >  **選項**] 以開啟 [**選項**] 對話方塊。

1. 在 [**專案和方案**  >  **一般**] 頁面上，取消選取 [**在解決方案載入時重新開啟檔**]。

若您停用自動檔案還原，則可以使用其中一個[移至](../ide/go-to.md)命令，快速瀏覽到您要開啟的檔案：

- 若是一般 **移至** 功能，請選取 [編輯] > [移至] > [移至全部]，或按 **Ctrl**+**T**。

- 使用 [**編輯**  >  **移** 至  >  **上一個編輯位置**] 或按 **Ctrl** + **Shift** + **倒退鍵**，跳至方案中的最後一個編輯位置。

- 使用 [移至最近使用的檔案]，查看最近在方案中瀏覽的檔案清單。 選取 [**編輯**  >  **移** 至  >  **最近使用** 的檔案]，或按 **ctrl** + **1**、 **ctrl** + **R**。

## <a name="configure-debugging-options"></a>設定偵錯選項

如果您在偵錯工作階段期間通常會記憶體不足，則可以進行一或多個組態變更來最佳化效能。

- **啟用 Just My Code**

    最簡單的最佳化是啟用 [Just My Code] 功能，這只會載入您專案的符號。 啟用此功能可以大幅降低用於偵錯 Managed 應用程式 (.NET) 的記憶體。 根據預設，某些專案類型已經啟用此選項。

    若要啟用 [Just My Code]，請選擇 [工具] > [選項] > [偵錯] > [一般]，然後選取 [啟用 Just My Code]。

- **指定要載入的符號**

    若為原生偵錯工具，載入符號檔 (*.pdb*) 在記憶體資源方面很昂貴。 您可以設定偵錯工具符號設定來節省記憶體。 一般而言，您會將方案設定成只從您的專案載入模組。

    若要指定符號載入，請選擇 [**工具**  >  **選項**  >  **調試**  >  **符號**]。

    設定 [僅限指定的模組] 的選項，而不是 [所有模組]，然後指定您要載入的模組。 偵錯時，您也可以以滑鼠右鍵按一下 [模組] 視窗中的特定模組，以在符號載入中明確包含模組  (在進行調試時開啟視窗，請選擇 [ **Debug**  >  **Windows**  >  **模組**]。 ) 

    如需詳細資訊，請參閱 [Understand symbol files](?view=vs-2019&preserve-view=true) (了解符號檔)。

- **停用診斷工具**

    建議您在使用之後停用 CPU 分析。 這項功能可能會耗用大量資源。 啟用 CPU 分析之後，會在後續偵錯工作階段之間持續保存此狀態，因此完成時適合明確地關閉它。 如果您不需要提供的功能，則在偵錯時停用診斷工具，即可節省一些資源。

    若要停用 **診斷工具**，請啟動調試過程、選取 [**工具**  >  **選項**]  >    >  **[一般**]，然後取消選取 [在 **調試時啟用診斷工具**] 選項。

    如需詳細資訊，請參閱 [Profiling Tools](../profiling/profiling-feature-tour.md) (分析工具)。

## <a name="disable-tools-and-extensions"></a>停用工具和延伸模組

若要改善效能，可以關閉一些工具或延伸模組。

> [!TIP]
> 一次關閉一個延伸模組，然後重新檢查效能，通常可以隔離效能問題。

### <a name="managed-language-service-roslyn"></a>受控語言服務 (Roslyn)

如需 .NET Compiler Platform ("Roslyn") 效能考量的資訊，請參閱[大型解決方案的效能考量](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)。

- **停用完整解決方案分析**

    在叫用組建之前，Visual Studio 會對整個解決方案執行分析，以提供錯誤的豐富體驗。 這項功能十分適用於盡快識別錯誤。 不過，對於大型解決方案，這項功能可能會耗用大量記憶體資源。 如果您遇到記憶體壓力或類似問題，則可以停用此體驗，來釋出這些資源。 根據預設，會針對 Visual Basic 啟用這個選項，但針對 C# 則會予以停用。

    若要停用 [完整解決方案分析]，請選擇 [工具] > [選項] > [文字編輯器]，然後選取 [Visual Basic] 或 [C#]。 選擇 [進階]，然後取消選取 [啟用完整解決方案分析]。

- **停用 CodeLens**

    Visual Studio 會對顯示的每個方法執行 [尋找所有參考] 工作。 CodeLens 會提供參考數目內嵌顯示這類功能。 工作會在不同的處理序中執行，例如 *ServiceHub.RoslynCodeAnalysisService32*。 在大型解決方案或資源受限的系統中，這項功能會對效能有顯著影響。 如果您遇到記憶體問題 (例如在 4 GB 電腦上載入大型解決方案時) 或此處裡序使用大量 CPU，可以停用 CodeLens 來釋出資源。

    若要停用 **CodeLens**，請選擇 [工具] > [選項] > [文字編輯器] > [所有語言] > [CodeLens]，然後取消選取這項功能。

    > [!NOTE]
    > CodeLens 適用於 Visual Studio 的 Professional 和 Enterprise 版本。

### <a name="other-tools-and-extensions"></a>其他工具和延伸模組

- **停用擴充功能**

    延伸模組是新增至 Visual Studio 的額外軟體元件，可提供新功能或延伸現有功能。 延伸模組通常可能是記憶體資源問題的來源。 如果您遇到記憶體資源問題，請嘗試一次停用一個延伸模組，以查看它對案例或工作流程的影響。

   ::: moniker range="vs-2017"

    若要停用擴充功能，移至 [工具]**[擴充功能和更新]** > ，然後停用特定擴充功能。

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    若要停用擴充功能，移至 [擴充功能]**[管理擴充功能]** > ，然後停用特定擴充功能。

   ::: moniker-end

- **停用地圖模式**

    [**地圖模式**](how-to-track-your-code-by-customizing-the-scrollbar.md#display-modes) 會以縮圖顯示捲軸上的程式程式碼。 預設會啟用地圖模式。

    若要停用地圖模式，請移至 [**工具**  >  **選項**  >  **文字編輯器**  >  **所有語言**  >  **捲軸**]，然後在 [**行為**] 區段中，取消選取 [**使用垂直捲動條的地圖模式]** 選項。

- **停用自動換行**

    [[**自動換**](./reference/how-to-manage-word-wrap-in-the-editor.md)行] 會顯示長行程式碼中，延伸超過 [程式碼編輯器] 視窗目前寬度的部分。 預設會開啟自動換行。

    若要針對目前正在處理的專案停用自動換行，請移至 [**編輯**  >  **自動換**  >  **行**]。  (您可以使用相同的功能表命令來切換此設定。 ) 

    若要停用所有專案的自動換行，請移至 [**工具**  >  **選項**  >  **一般**  >  **文字編輯器**  >  **所有語言**]，  >  然後在 [**設定**] 區段中，取消選取 [**自動換行**] 選項。

- **停用 XAML 設計工具**

    預設會啟用 XAML 設計工具，但只有在您開啟 *.xaml* 檔案時，才會耗用資源。 如果您使用 XAML 檔案，但不想要使用設計工具功能，請停用這項功能，以釋出一些記憶體。

    若要停用 XAML 設計工具，請移至 [**工具**  >  **選項**]  >  **XAML 設計工具**  >  **啟用 XAML 設計工具**]，然後取消選取此選項。

- **移除工作負載**

    您可以使用 Visual Studio 安裝程式以移除不再使用的工作負載。 這個動作可以略過不再需要的套件和組件，來簡化啟動和執行階段成本。

## <a name="force-a-garbage-collection"></a>強制執行記憶體回收

CLR 使用記憶體回收記憶體管理系統。 在此系統中，有時不再需要的物件會使用記憶體。 這種狀態是暫時的；記憶體回收行程會根據其效能和資源使用量啟發學習法來釋放這個記憶體。 您可以使用 Visual Studio 中的快速鍵，強制 CLR 收集任何未使用的記憶體。 如果有大量的垃圾等候回收，而您強制進行垃圾收集，您應該會在 **工作管理員** 中看到 *devenv.exe* 進程的記憶體使用量。 很少需要使用這種方法。 不過，完成耗費資源的作業 (例如完整建置、偵錯工作階段或方案開啟事件) 之後，即可協助您判斷處理序實際正在使用的記憶體數量。 因為 Visual Studio 是混合的 (Managed 和原生)，所以原生配置器和記憶體回收行程可能偶而會競爭有限的記憶體資源。 在高記憶體使用量的情況下，它有助於強制執行記憶體回收行程。

若要強制垃圾收集，請使用快速鍵： **ctrl** + **alt** + **shift** + **f12**、 **ctrl** + **alt** + **shift** + **f12** (按兩次) 。

如果可靠地強制執行記憶體回收可讓您的案例運作，請透過 Visual Studio 意見反應工具提出報表，因為這種行為可能是 Bug。

如需 CLR 記憶體回收行程的詳細描述，請參閱[記憶體回收的基本概念](/dotnet/standard/garbage-collection/fundamentals)。

## <a name="see-also"></a>另請參閱

- [最佳化 Visual Studio 效能](../ide/optimize-visual-studio-performance.md)
- [更快載入解決方案 (Visual Studio 部落格)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)