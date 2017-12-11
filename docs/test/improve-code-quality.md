---
title: "改善程式碼品質 | Microsoft Docs"
ms.custom: na
ms.date: 02/17/2017
ms.reviewer: na
ms.suite: na
ms.technology: vs-devops-test
ms.tgt_pltfrm: na
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- team-based development
ms.assetid: 73baa961-c21f-43fe-bb92-3f59ae9b5945
caps.latest.revision: "39"
ms.author: douge
manager: douge
ms.openlocfilehash: 93847beaef971f9370d59a8c5c8ac9f3a59a0967
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="improve-code-quality"></a>改善程式碼品質
什麼是程式碼品質？ 正確性、可維護性，甚至是優雅與否，都是建立出色應用程式所必須考量的事項。 不論您如何定義它，Visual Studio 測試工具都可以協助您和小組開發及維持絕佳的高標準程式碼表現。  
  
 **Requirements**  
  
-   本節所說明的某些工具和功能只適用於特定 Visual Studio 版本，並不是所有 Visual Studio 版本都提供這些功能。 我們在這些工具和功能的文件中列出特定版本需求。  
  
## <a name="in-this-section"></a>本節內容  
 在下面的表格中，您可以找到常見工作的描述，以及包含如何順利完成那些工作之資訊的連結。  
  
|||  
|-|-|  
|[對程式碼進行單元測試](../test/unit-test-your-code.md)|測試總管可讓您輕鬆地將單元測試整合在開發實務中。 您可以使用 Microsoft 單元測試架構，或使用多種協力廠商架構和開放原始碼架構的其中一種。|  
|[Visual Studio 的 Live Unit Testing](../test/live-unit-testing.md)|Live Unit Testing 會自動在背景執行單元測試，並在 Visual Studio 程式碼編輯器中以圖形方式顯示程式碼涵蓋範圍和測試結果。|  
|[分析應用程式品質](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|靜態程式碼分析工具可尋找 C++ 和 Managed 程式碼中的設計、使用方式、可維護性和樣式等問題。 許多這些問題可能會造成難以在標準測試環境重現的 Bug。|  
|[測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|程式碼度量資訊是一組軟體測量數據，可以讓開發人員更深入了解他們正在開發的程式碼。 度量資訊包括函式和類別的可維護性指數、函式的循環複雜度、類別的繼承深度，以及類別間的結合程度。|  
  
## <a name="related-scenarios"></a>相關案例  
 [Team Services 與 TFS 的 DevOps 概觀](https://www.visualstudio.com/docs/devops-alm-overview)  
 如果您不熟悉 Visual Studio Team Foundation 和 Visual Studio Team Services,，可以深入了解如何在小組開發環境中使用它來改善生產力，並且降低應用程式開發伴隨的風險。  
  
 [分析架構並製作架構模型](../modeling/analyze-and-model-your-architecture.md)  
 您可以使用 [!INCLUDE[vsPreExt](../test/includes/vspreext_md.md)] 管理設計軟體所面臨的挑戰和複雜度。 您可以使用 [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] 以視覺化方式，依據現有的內容和未來希望擁有的內容來建立應用程式模型。 您還可以建立和維護圖表，在應用程式的邏輯模型對應到實體模型時協助您將模型視覺化；如此可讓您變更、驗證和分析「正在設計」的軟體。  
  
 [測試應用程式](https://www.visualstudio.com/docs/test/overview)  
 您可以使用 [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] 和 [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] 在整個測試生命週期中提高生產力， [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] 或 [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] 可讓您計劃投入測試的時間。 此外還可以建立、管理、編輯和執行手動和自動化測試。 您還可以根據您的計劃檢閱測試進度。  
  
 [使用 PreEmptive Protection - Dotfuscator 保護應用程式](../ide/dotfuscator/index.md)  
 您可以使用免費的 Dotfuscator Community Edition 協助保護商業機密和其他智慧財產 (IP)、減少盜版和仿冒，並防止竄改及未經授權的偵錯。  Dotfuscator 不需要其他程式設計作業，甚至不需要存取原始程式碼，就可以保護並強化編譯的組件。
  
 [建置應用程式](https://www.visualstudio.com/docs/build/overview)  
 您可以使用 [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] 來建立和管理程式碼的自動化組建。 [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] 可讓您建立置放伺服器以部署組建。 此外，您也可以分析組建趨勢。  
  
 [使用 Visual Studio Online 或 Team Foundation Server 追蹤工作](https://www.visualstudio.com/docs/work/overview)  
 您可以使用 [!INCLUDE[vstsTfsLong](../test/includes/vststfslong_md.md)] 計劃和追蹤專案，無論使用的是彈性程序、正式程序或是這些程序的變化。 透過計劃專案、依據計劃追蹤進度及進行必要的調整，就可以降低風險、避免發生意外狀況，以及管理專案的成本。
