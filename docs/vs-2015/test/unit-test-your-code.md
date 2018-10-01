---
title: 對程式碼進行單元測試 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: gewarren
manager: douge
ms.openlocfilehash: a1c6c521e09795619af503e0a121e51f6edc33b9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491885"
---
# <a name="unit-test-your-code"></a>對程式碼進行單元測試
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[單元測試程式碼](https://docs.microsoft.com/visualstudio/test/unit-test-your-code)。  
  
單元測試提供開發人員及測試人員一個快速的方法，可在 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]、[!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] 和 [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)] 專案中查看類別之方法中的邏輯錯誤。  
  
 單元測試工具包括：  
  
1.  **測試總管。** 測試總管可讓您執行單元測試並檢視其結果。 測試總管可以使用任何具有測試總管配接器的單元測試架構，包括協力廠商架構。  
  
2.  **適用於 Managed 程式碼的 Microsoft 單元測試架構。** 適用於 Managed 程式碼的 Microsoft 單元測試架構是與 Visual Studio 一起安裝的，可提供用於測試 .NET 程式碼的架構。  
  
3.  **適用於 C++ 的 Microsoft 單元測試架構。** 適用於 C++ 的 Microsoft 單元測試架構是與 Visual Studio 一起安裝的，可提供用於測試機器碼的架構。  
  
4.  **程式碼涵蓋範圍工具。** 您可以使用測試總管中的一個命令來判斷單元測試所執行的產品程式碼數量。  
  
5.  **Microsoft Fakes 隔離架構。** Microsoft Fakes 隔離架構可以為在受測程式碼中建立相依性的生產環境和系統程式碼建立替代的類別和方法。 藉由實作函式的偽造委派，您可以控制相依性物件的行為和輸出。  
  
 您也可以使用 [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) 來探索 .NET 程式碼，以產生測試資料和單元測試套件。 其會為程式碼中的每一個陳述式產生一個用以執行該陳述式的測試輸入。 程式碼的每個條件分支都會執行大小寫分析。  
  
## <a name="key-tasks"></a>主要工作  
 下列主題可協助您了解及建立單元測試：  
  
|工作|相關主題|  
|-----------|-----------------------|  
|**快速入門和逐步解說：** 使用下列主題從程式碼範例來了解 Visual Studio 中的單元測試。|-   [逐步解說：針對 Managed 程式碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [快速入門：搭配測試總管進行以測試為導向的開發工作](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [將單元測試加入至現有的 C++ 應用程式](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [使用測試總管針對機器碼執行單元測試](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
|**使用測試總管進行單元測試：** 了解測試總管如何協助建立更具生產力且更有效率的單元測試。|-   [單元測試基本概念](../test/unit-test-basics.md)<br />-   [建立單元測試專案](../test/create-a-unit-test-project.md)<br />-   [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)<br />-   [安裝協力廠商單元測試架構](../test/install-third-party-unit-test-frameworks.md)<br />-   [升級 Visual Studio 2010 的單元測試](http://msdn.microsoft.com/en-us/9bb75856-f68a-4de2-a084-b08a947a1172)|  
|**對 Managed 程式碼進行單元測試：**|-   [使用適用於 Managed 程式碼的 Microsoft 單元測試架構撰寫適用於 .NET Framework 的單元測試](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**對 C++ 程式碼進行單元測試**|-   [使用適用於 C++ 的 Microsoft 單元測試架構撰寫適用於 C/C++ 的單元測試](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**隔離單元測試**|-   [使用 Microsoft Fakes 在測試期間隔離程式碼](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**使用程式碼涵蓋範圍來識別您的專案程式碼的哪個部分，是使用單元測試進行測試：** 了解 [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] 測試工具的程式碼涵蓋範圍功能。|-   [使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**在單元測試中運用負載測試來執行壓力與效能分析：** 您可以建立負載測試，並將單元測試加入其中，以便找出應用程式中的效能與壓力問題。 **注意：** 若要建立和使用負載測試，您必須安裝 Visual Studio Enterprise。|-   [建立和編輯負載測試](http://msdn.microsoft.com/en-us/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [如何：將 Web 效能測試和單元測試加入負載測試情節](http://msdn.microsoft.com/en-us/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [如何：將 Web 效能測試和單元測試從負載測試情節中移除](http://msdn.microsoft.com/en-us/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|  
|**設立並嚴守品質閘門：** 您可以樹立品質閘門，確定程式碼在簽入之前都必須先經過測試，以確保程式碼的品質。|-   [設立並嚴守品質閘門](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**擴充單元測試類型：** 您可以在測試中加入可能不存在單元測試架構中的功能。 例如，您可以加入測試屬性，以便指定測試是否應該以一般使用者身分執行。 或者，您也可以擴充架構，以便將資料列屬性加入至方法並且在測試內部使用該資料列的資料。|如需如何擴充單元測試架構的範例程式碼，請參閱下列 [Microsoft 網站](http://go.microsoft.com/fwlink/?LinkId=185591)。|  
|**設定測試選項：** 例如，您可以指定儲存測試結果的位置。|[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="related-tasks"></a>相關工作  
 [在 Microsoft Test Manager 中檢閱測試結果](http://msdn.microsoft.com/en-us/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)  
  
 描述測試結果以及使用這些結果的方式，包括如何檢視、儲存和刪除測試結果。  
  
 [使用 Microsoft Visual Studio 執行系統測試](http://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)  
  
 提供有關使用 Visual Studio 執行自動化測試 (相對於使用 [!INCLUDE[TCMext](../includes/tcmext-md.md)]) 的資訊連結。  
  
## <a name="reference"></a>參考資料  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 描述 UnitTesting 命名空間，此命名空間可提供屬性、例外狀況、判斷提示和其他支援單元測試的類別。  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 描述 UnitTesting.Web 命名空間，此命名空間可藉由提供對 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 和 Web 服務單元測試的支援，延伸 UnitTesting 命名空間。  
  
## <a name="external-resources"></a>外部資源  
  
### <a name="videos"></a>視訊  
 [Channel 9：Unit testing your Windows Store apps built using XAML (單元測試使用 XAML 建置的 Windows 市集應用程式)](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>論壇  
 [Visual Studio 單元測試](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="guidance"></a>指引  
 [使用 Visual Studio 2012 測試持續傳遞 - 第 2 章：單元測試：測試內部](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="reference"></a>參考資料  
 [單元測試的內容索引](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## <a name="see-also"></a>另請參閱  
 [改善程式碼品質](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)   
 [測試應用程式](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)



