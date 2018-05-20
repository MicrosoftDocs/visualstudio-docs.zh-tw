---
title: Visual Studio 效能祕訣和訣竅
ms.date: 08/31/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2fbcb59e-e981-4b40-8b7a-c1140d31ec4b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec6563086968cb84c0ad2177d5a1c13e051012cf
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Visual Studio 效能祕訣和訣竅

Visual Studio 效能建議是要針對記憶體不足的情況，但這極少發生。 在這些情況下，您可以最佳化可能不會使用的特定 Visual Studio 功能。 下列祕訣不適合作為一般建議。

> [!NOTE]
> 如果您在使用產品時因記憶體問題而發生困難，請透過[意見反應工具](../ide/how-to-report-a-problem-with-visual-studio-2017.md)讓我們知道。

## <a name="optimize-your-environment"></a>將您的環境最佳化

- **使用 64 位元 OS**

    如果您將系統從 32 位元版本的 Windows 升級至 64 位元版本，請將 Visual Studio 可用的虛擬記憶體數量從 2 GB 擴充為 4 GB。 這可讓 Visual Studio 處理更大量的工作負載，即使它是 32 位元處理序也是一樣。

    如需詳細資訊，請參閱[記憶體限制](https://msdn.microsoft.com/library/windows/desktop/aa366778(v=vs.85).aspx#memory_limits)和 [Use /LARGEADDRESSAWARE on 64-bit Windows](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/) (在 64 位元 Windows 上使用 /LARGEADDRESSAWARE)。

## <a name="configure-solution-and-projects"></a>設定方案和專案

如果您的極大型方案包含多個專案，則進行下列最佳化會有所助益：

- **卸載專案**

    您可以從 [方案總管] 中，使用滑鼠右鍵操作功能表手動卸載極少使用的個別專案。

- **重構方案**

    您可以將您的方案分割成數個包含常用專案的較小方案檔。 這項重構應該可以大幅降低您工作流程的記憶體使用量。 較小方案的載入速度也會較快。

## <a name="configure-debugging-options"></a>設定偵錯選項

如果您在偵錯工作階段期間通常會記憶體不足，則可以進行一或多個組態變更來最佳化效能。

- **啟用 Just My Code**

    最簡單的最佳化是啟用 [Just My Code] 功能，這只會載入您專案的符號。 啟用此功能可以大幅降低用於偵錯 Managed 應用程式 (.NET) 的記憶體。 根據預設，某些專案類型已經啟用此選項。

    若要啟用 [Just My Code]，請選擇 [工具] > [選項] > [偵錯] > [一般]，然後選取 [啟用 Just My Code]。

- **指定要載入的符號**

    進行原生偵錯時，載入符號檔 (*.pdb*) 會耗用大量記憶體資源。 您可以設定偵錯工具符號設定來節省記憶體。 一般而言，您會將方案設定成只從您的專案載入模組。

    若要指定符號載入，請選擇 [工具] > [選項] > [偵錯] > [符號]。

    設定 [僅限指定的模組] 的選項，而不是 [所有模組]，然後指定您要載入的模組。 偵錯時，您也可以以滑鼠右鍵按一下 [模組] 視窗中的特定模組，以在符號載入中明確包含模組 (若要在偵錯時開啟此視窗，請選擇 [偵錯] > [視窗] > [模組])。

    如需詳細資訊，請參閱 [Understand symbol files](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/) (了解符號檔)。

- **停用診斷工具**

    建議您在使用之後停用 CPU 分析。 這項功能可能會耗用大量資源。 啟用 CPU 分析之後，會在後續偵錯工作階段之間持續保存此狀態，因此完成時適合明確地關閉它。 如果您不需要提供的功能，則在偵錯時停用診斷工具，即可節省一些資源。

    若要停用**診斷工具**，請啟動偵錯工作階段，並選擇 [工具] > [選項] > [啟用診斷工具]，然後取消選取此選項。

    如需詳細資訊，請參閱 [Profiling Tools](../profiling/profiling-tools.md) (分析工具)。

## <a name="disable-tools-and-extensions"></a>停用工具和延伸模組

若要改善效能，則可能需要關閉一些工具或延伸模組。

> [!TIP]
> 一次關閉一個延伸模組，然後重新檢查效能，通常可以隔離效能問題。

### <a name="managed-language-services-roslyn"></a>Managed 語言服務 (Roslyn)

如需 .NET Compiler Platform ("Roslyn") 效能考量的資訊，請參閱[大型解決方案的效能考量](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)。

- **停用完整解決方案分析**

    在叫用組建之前，Visual Studio 會對整個解決方案執行分析，以提供錯誤的豐富體驗。 這項功能十分適用於盡快識別錯誤。 不過，針對非常大型的方案，這項功能可能會耗用大量記憶體資源。 如果您遇到記憶體壓力或類似問題，則可以停用此體驗，來釋出這些資源。 根據預設，會針對 Visual Basic 啟用這個選項，但針對 C# 則會予以停用。

    若要停用 [完整解決方案分析]，請選擇 [工具] > [選項] > [文字編輯器] > [<Visual Basic 或 C#>]。 接著選擇 [進階]，然後取消選取 [啟用完整解決方案分析]。

- **停用 CodeLens**

    Visual Studio 會對顯示的每個方法執行 [尋找所有參考] 工作。 CodeLens 會提供參考數目內嵌顯示這類功能。 工作會在不同的處理序中執行 (例如，*ServiceHub.RoslynCodeAnalysisService32*)。 在極大型方案中或資源限制系統上，這項功能會對效能造成顯著影響，即使它是以低優先順序執行也是一樣。 如果您在此處理序中遇到高 CPU 或是遇到記憶體問題 (例如，在 4 GB 電腦上載入大型方案時)，可以嘗試停用這項功能來釋出資源。

    若要停用 **CodeLens**，請選擇 [工具] > [選項] > [文字編輯器] > [所有語言] > [CodeLens]，然後取消選取這項功能。

    這項功能適用於 Visual Studio Professional 和 Visual Studio Enterprise。

### <a name="other-tools-and-extensions"></a>其他工具和延伸模組

- **停用延伸模組**

    延伸模組是新增至 Visual Studio 的額外軟體元件，可提供新功能或延伸現有功能。 延伸模組通常可能是記憶體資源問題的來源。 如果您遇到記憶體資源問題，請嘗試一次停用一個延伸模組，以查看它對案例或工作流程的影響。

    若要停用延伸模組，請移至 [工具] > [延伸模組和更新]，然後停用特定延伸模組。

- **停用 XAML 設計工具**

    預設會啟用 XAML 設計工具，但只有在您開啟 *.xaml* 檔案時才會耗用資源。 如果您使用 XAML 檔案，但不想要使用設計工具功能，請停用這項功能，以釋出一些記憶體。

    若要停用 **XAML 設計工具**，請移至 [工具] > [選項] > [XAML 設計工具] > [啟用 XAML 設計工具]，然後取消選取此選項。

- **移除工作負載**

    您可以使用 Visual Studio 安裝程式以移除不再使用的工作負載。 這個動作可以略過不再需要的套件和組件，來簡化啟動和執行階段成本。

## <a name="force-a-garbage-collection"></a>強制執行記憶體回收

CLR 使用記憶體回收記憶體管理系統。 在此系統中，有時不再需要的物件會使用記憶體。 這種狀態是暫時的；記憶體回收行程會根據其效能和資源使用量啟發學習法來釋放這個記憶體。 您可以使用 Visual Studio 中的快速鍵，強制 CLR 收集任何未使用的記憶體。 如果有大量記憶體正在等待回收，而且您強制執行記憶體回收，則應該會在**工作管理員**中看到 *devenv.exe* 處理序的記憶體使用量下降。 很少需要使用這種方法。 不過，完成耗費資源的作業 (例如完整建置、偵錯工作階段或方案開啟事件) 之後，即可協助您判斷處理序實際正在使用的記憶體數量。 因為 Visual Studio 是混合的 (Managed 和原生)，所以原生配置器和記憶體回收行程可能偶而會競爭有限的記憶體資源。 在高記憶體使用量的情況下，它有助於強制執行記憶體回收行程。

若要強制執行記憶體回收，請使用快速鍵：**Ctrl**+**Alt**+**Shift**+**F12**、**Ctrl**+**Alt**+**Shift**+**F12** (按兩次)。

如果可靠地強制執行記憶體回收可讓您的案例運作，請透過 Visual Studio 意見反應工具提出報表，因為這種行為可能是 Bug。

如需 CLR 記憶體回收行程的詳細描述，請參閱[記憶體回收的基本概念](/dotnet/standard/garbage-collection/fundamentals)。

## <a name="see-also"></a>另請參閱

- [最佳化 Visual Studio 效能](../ide/optimize-visual-studio-performance.md)
- [Visual Studio 部落格 - 使用 Visual Studio 2017 15.6 版更快速地載入解決方案](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)