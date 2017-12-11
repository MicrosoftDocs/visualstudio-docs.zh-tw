---
title: "升級 Visual Studio 2010 單元測試專案 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1502b51-d6db-4894-9fbf-4a5723e4bb1a
caps.latest.revision: "8"
ms.author: douge
manager: douge
ms.openlocfilehash: 2e3e99bfad1ebf33f23c3b38189568935d0cedee
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2017
---
# <a name="upgrade-visual-studio-2010-unit-test-projects"></a>升級 Visual Studio 2010 單元測試專案
[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 包含與 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 測試專案的測試專案相容性。 例如，您透過 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 建立的測試專案可以使用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 開啟，不需要任何升級。 因此，您的小組可以同時使用 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 處理相同的測試專案。 如需詳細資訊，請參閱[從 Visual Studio 2010 升級測試](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)。  
  
 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 導入了幾項單元測試的變更。 由於這些變更，請務必了解舊版 Visual Studio 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 之間的相容性問題。 在這些單元測試的變更中，一個重大的變更是 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 包含多個測試專案範本 (包括單元測試專案範本)。 新的單元測試已加入至新的單元測試專案範本。 單元測試也可以包含在另一個新的測試專案範本，稱為自動程式化 UI 測試專案範本。 如需新測試專案範本的詳細資訊，請參閱[從舊版 Visual Studio 升級測試](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)。 根據預設，新的單元測試專案不再包含測試設定檔。 藉由排除測試設定檔，可改善您的單元測試的效能。 針對相容性，您仍然可以使用您利用 Visual Studio 2010 建立的現有測試專案。 不過，建議您針對效能原因移除與測試專案相關聯的測試設定檔，除非您有該測試設定檔的特殊需求。 例如，如果您的單位測試在分散式環境中執行，或者您需要收集特定診斷資料，您可能選擇保留測試設定檔。 如果您針對使用新的單位測試專案範本或自動程式化 UI 測試專案範本具有類似需求，您也可以手動將測試設定檔加入它們。  
  
> [!NOTE]
>  [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 測試專案中的現有單位測試將能夠順暢地在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 之間運作。 當包含您單元測試的 Visual Studio 2010 測試專案在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中開啟時，系統將不會對它做出任何變更 (反之亦然)。  
  
> [!CAUTION]
>  Visual Studio 2010 無法開啟以 11.0 工具組為目標的 C++/CLI 專案，也就是在 Visual Studio 2012 或更新版本中建立的專案。 這項限制適用於所有 C++/CLI 專案，而不只是 C++/CLI 單元測試專案。  
  
> [!NOTE]
>  您可以從命令列使用 vstest.console.exe 執行新的單元測試。 如需使用 vstest.console.exe 的詳細資訊，請參閱 [VSTest.Console.exe 命令列選項](/devops-test-docs/test/vstest-console-exe-command-line-options)，或使用說明參數執行該命令︰**vstest.console.exe /?**。 您可以使用 MStest.exe 繼續執行現有的單元測試。 如需詳細資訊，請參閱[從命令列使用 MSTest 執行自動化測試](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest)和 [MSTest.exe 命令列選項](/devops-test-docs/test/mstest-exe-command-line-options)。  
  
 另一個重大的變更是新的 [測試總管]。 在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中，部分您所熟悉的舊版測試視窗已淘汰，例如 [測試檢視] 視窗。 [測試總管] 的設計可進一步支援開發人員和小組在其軟體開發實務中併入「單元測試」(unit testing)。 如需詳細資訊，請參閱[使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)。  
  
## <a name="compatibility-issues-between-visual-studio-2010-sp1-and-visual-studio-2012-or-later"></a>Visual Studio 2010 SP1 和 Visual Studio 2012 或更新版本之間的相容性問題  
 以下是一些您在 Visual Studio 2010 SP1 和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 之間移轉單元測試時須注意的問題：  
  
|單元測試功能|問題|方案|  
|-----------------------------|-----------|--------------|  
|測試清單 (.vsmdi files) 已在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中淘汰。|您將再也無法從 Visual Studio 建立新的測試清單 (.vsmdi 檔案) 或執行測試清單。 **提示：**  測試分類與舊版 Microsoft Visual Studio 中的測試清單功能相比，可提供更大的彈性。 您可以搭配使用邏輯運算子與測試分類，一起執行來自多個分類的測試，或將執行的測試限制為屬於多個分類的測試。 同時，當您建立測試方法時也可輕鬆地加入測試分類，在已建立測試方法之後不需要維護測試清單。 使用測試分類，您不需要簽入和簽出維護測試清單的 **\<solution name>.vsmdi** 檔案。 如需詳細資訊，請參閱[定義測試分類以分組測試](/devops-test-docs/test/defining-test-categories-to-group-your-tests)。|-   若要維持與使用測試清單之現有測試專案的相容性，您仍然能夠使用 Visual Studio 編輯 .vsmdi 檔案。<br />-   雖然您無法從 Visual Studio 執行已移轉的測試清單，您仍然可以從命令列使用 mstest.exe 執行測試清單。 如需詳細資訊，請參閱[從命令列使用 MSTest 執行自動化測試](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest)<br />-   如果您在組建定義中使用測試清單，您可以繼續使用它。 如需詳細資訊，請參閱[如何：在建置應用程式之後設定和執行已排程的測試](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)和[在建置流程中執行測試](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38)。|  
|私用存取子已在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中淘汰。<br /><br /> 在舊版的 Visual Studio 中，您可以使用 Publicize 指定內部應用程式開發介面 (API)，並建立您可以在測試中呼叫的公用對應項目 API，而該 API 會接著呼叫到您產品的內部 API。 您接著可以使用程式碼產生來建立測試虛設常式，並在該虛設常式內產生程式碼片段。|您不再能夠建立私用存取子。|<ul><li>Visual Studio 2010 測試專案會在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中編譯與運作。 建置將會包含輸出警告。</li><li>如果您仍然需要測試內部 API，您有下列選項︰<br /><br /> <ul><li>使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> 類別協助存取程式碼中的內部和私人 API。 這會在 Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll 組件中找到。</li><li>建立能夠反映您程式碼的反映架構，以存取內部或私用 API。</li><li>如果您嘗試存取的是內部程式碼，您也許能夠使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 存取您的 API，這樣您的測試程式碼就能存取內部 API。</li></ul></li></ul>|  
|測試影響已移除|||  
|從 [測試總管] 透過 TRX 記錄檔共用執行結果。||您仍然可以從命令列和 Team Build 取得 TRX 記錄檔。|  
  
## <a name="see-also"></a>另請參閱  
 [移植、移轉和升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [對程式碼進行單元測試](../test/unit-test-your-code.md)   
 [從舊版 Visual Studio 升級測試](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [升級 Visual Studio 2010 的自動程式化 UI 測試](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)
