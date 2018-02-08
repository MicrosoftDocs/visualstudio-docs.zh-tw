---
title: "測試總管常見問題集 | Microsoft Docs"
ms.date: 1/15/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: ghogen
ms.openlocfilehash: db3cf85576e6c46aca14897f7244cd0f56d8d5c2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio 測試總管常見問題集

## <a name="test-discovery"></a>測試探索

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-have-theories-custom-adapters-custom-traits-use-ifdefs-or-are-dynamically-defined-how-can-i-discover-these-tests"></a>1.測試總管未探索包含理論、自訂配接器、自訂特徵、使用 #ifdefs 的，或以動態方式定義的測試。 我如何探索這些測試？

  建置專案，然後確定已在 [工具] > [選項] > [測試] 中開啟以組件為基礎的探索。

  [即時測試探索](https://go.microsoft.com/fwlink/?linkid=862824) \(英文\) 是以來源為基礎的測試探索，無法探索使用理論、自訂配接器、自訂特性、`#ifdef` 陳述式，或以其他方式動態定義的測試。 這些測試需要建置才能正確地被探索。 在 15.6 預覽中，以組件為基礎的探索 (傳統型探索) 只會在建置之後執行。 這表示當您在編輯時，即時測試探索會盡可能探索更多測試，而以組件為基礎的探索允許理論 (或任何以動態方式定義的測試) 在建置之後顯示。 即時測試探索改善了回應性，但仍然可讓您在建置之後取得完整且正確的結果。

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2.顯示在測試總管最上面一行的 [+] \(加號\) 符號代表什麼？

  [+] \(加號\) 符號代表建置之後可能探索到更多測試 (若已開啟以組件為基礎的探索)。 如果在您的專案中探索到以動態方式定義的測試，它就會出現。

  ![加號摘要行](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3.我的專案已經無法使用以組件為基礎的探索。 如何再將它開啟？

  移至 [工具] > [選項] > [測試]，然後選取 [建置之後額外探索組件的測試組建] 核取方塊。

  ![以組件為基礎的選項](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4.現在當我打字時，測試會顯示在測試總管中，而不需要建置我的專案。 哪些方面受到變更？

  此功能稱為[即時測試探索](https://go.microsoft.com/fwlink/?linkid=862824) \(英文\)。 它使用 Roslyn 分析器來探索測試並即時填入測試總管，因此不需要建置您的專案。 如需針對以動態方式定義之測試 (例如理論或自訂特徵) 的測試探索行為，請參閱常見問題集 #1。

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5.哪些程式設計語言和測試架構可以使用「即時測試探索」？

  [即時測試探索](https://go.microsoft.com/fwlink/?linkid=862824) \(英文\) 乃是以 Roslyn 編譯器建置，因此只適用於受控語言 (C# 和 Visual Basic)。 目前，「即時測試探索」只適用於 xUnit、NUnit 和 MSTest 架構。

## <a name="features"></a>功能

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>如何開啟功能旗標以試用新的測試功能？

功能旗標是用來將產品的實驗性或未完成的部分，遞送給想在功能正式推出前提供意見反應的熱衷使用者。 它們可能會造成 IDE 體驗不穩定。 建議您只在安全的開發環境 (如虛擬機器) 中使用它們。 功能旗標一律是「自行承擔使用風險」的設定。 您可以使用 [Feature Flags 延伸模組](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)，或開發人員命令提示字元來開啟實驗性功能。

![Feature Flag 延伸模組](media/testex-featureflag.png)

若要透過 Visual Studio 開發人員命令提示字元來開啟功能旗標，請使用以下命令。 變更 Visual Studio 在機器上的安裝路徑，並變更要使用的功能旗標之登錄機碼。

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise” HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> 您可以使用相同的命令來關閉旗標，方法是在 dword 之後使用 0 作為值而不是 1。
  
## <a name="see-also"></a>另請參閱

<xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>  
[針對現有的程式碼建立和執行單元測試](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
[對程式碼進行單元測試](unit-test-your-code.md)
[即時單元測試常見問題集](live-unit-testing-faq.md)
