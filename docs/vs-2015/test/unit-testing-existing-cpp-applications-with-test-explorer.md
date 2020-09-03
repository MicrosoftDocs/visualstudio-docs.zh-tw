---
title: 使用測試總管針對現有 C++ 應用程式執行單元測試 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 68bff8dbe2d0e5d85c8b18eeafaeaad06ba3982e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540071"
---
# <a name="unit-testing-existing-c-applications-with-test-explorer"></a>使用測試總管針對現有 C++ 應用程式執行單元測試
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

我們建議在變更現有的應用程式之前，您要確定它能夠良好地涵蓋單元測試。 這會讓您對於變更不會產生 Bug 有信心。 如果應用程式尚未具有單元測試，您可以使用本主題中所示範的技術來加入單元測試。 本主題說明如何為現有的 Visual C++ 程式碼加入單元測試，從決定如何測試程式碼開始，然後建立、撰寫測試，最後則執行測試。

## <a name="deciding-how-to-test-your-code"></a>決定如何測試程式碼
 開啟現有的 C++ 專案，並檢查它以決定您要如何加入單元測試。 您可能會想要使用某些模型工具，來協助您了解程式碼中的相依性，以及協助您了解組件的互動方式。 如需詳細資訊，請參閱[視覺化程式碼](../modeling/visualize-code.md)。

 我們建議您將變更工作拆解為小型的工作。 在進行每個小變更之前，都要針對會保持相同行為的各個方面來撰寫單元測試。 在您進行變更之後，這些測試仍持續會成功。 例如，如果您想要變更某個排序函式，讓它依姓氏而不是依名字來排序人員清單，那麼您就可以撰寫單元測試以驗證所有輸入名稱會出現在輸出中。 進行這項變更之後，您可能會想要針對新行為加入新的單元測試。

 如果可行，您的大部分或所有單元測試都應該只使用匯出的函式。 不過，如果您只是變更整個應用程式的一小部分，則您可能會想要使用不是匯出的函式。 例如，您可能需要會叫用內部函式的測試，或者是會設定並取得內部變數值的測試。

 有幾種方式可以測試產品程式碼，這取決於產品是否有公開您要測試的介面。 請選擇下列其中一種方式：

 **單元測試只會使用從受測程式碼匯出** 的函式：新增個別的測試專案。 在測試專案中，加入受測專案的參考。

 移至[從測試專案參考匯出的函式](#projectRef)程序。

 **測試中的程式碼是以 .exe 檔案的形式建立：** 新增個別的測試專案。 將它連結至輸出目的檔。

 移至[將測試連結至物件或程式庫檔案](#objectRef)程序。

 **單元測試必須使用私用函式和資料，且受測程式碼可以建立為靜態程式庫：** 變更受測專案，使其編譯為 .lib 檔案。 加入會參考受測專案的個別測試專案。

 這個方法有一個優點，就是可讓您的測試使用私用成員，但仍然將測試保留在個別專案中。 不過，這可能不適用於某些應用程式，在這類應用程式中您必須具有動態連結程式庫 (.dll)。

 請移至[將受測程式碼變更為靜態程式庫](#staticLink)程序。

 **單元測試必須使用私用函式和資料，而程式碼必須建立為動態連結程式庫， (DLL) ：** 將單元測試加入至與產品程式碼相同的專案中。

 請移至[在相同專案中新增單元測試](#sameProject)程序。

## <a name="creating-the-tests"></a>建立測試

### <a name="to-change-the-code-under-test-to-a-static-library"></a><a name="staticLink"></a> 將受測程式碼變更為靜態程式庫

- 如果您的測試必須使用不是由受測專案匯出的成員，並且受測專案是建置為動態程式庫，請考慮將它轉換成靜態程式庫。

  1. 在方案總管中，於受測專案的捷徑功能表上選擇 [屬性]****。 專案的屬性視窗便會開啟。

  2. 依序選擇 [組態屬性]**** 和 [一般]****。

  3. 將 [組態類型]**** 設定為 [靜態程式庫 (.lib)]****。

  繼續進行[將測試連結至物件或程式庫檔案](#objectRef)程序。

### <a name="to-reference-exported-functions-from-the-test-project"></a><a name="projectRef"></a> 從測試專案參考匯出的函式

- 如果受測專案會匯出您要測試的函式，那麼您就可以從測試專案加入程式碼專案的參考。

  1. 建立 C++ 測試專案。

      1. 在 [檔案]**** 功能表上，依序選擇 [新增]****、[專案]****、[Visual C++]、[測試]**** 和 [C++ 單元測試專案]****。

  2. 在方案總管中，於測試專案的捷徑功能表上，選擇 [參考]****。 專案的屬性視窗便會開啟。

  3. 依序選取 [通用屬性]****、[架構和參考]**** 和 [新增參考]**** 按鈕。

  4. 選取 [專案]****，然後選取要測試的專案。

       選擇 [新增] 按鈕。

  5. 在測試專案的屬性中，將受測專案的位置加入至 [Include 目錄] 中。

       依序選擇 [組態屬性]****、[VC++ 目錄]**** 和 [Include 目錄]****。

       選擇 [編輯]****，然後新增受測專案的標頭目錄。

  移至[撰寫單元測試](#addTests)程序。

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a> 將測試連結至物件或程式庫檔案

- 如果受測程式碼不會匯出您要測試的函式，您可以將輸出 **.obj** 或 **.lib** 檔案新增至測試專案的相依性。

  1. 建立 C++ 測試專案。

      1. 在 [檔案]**** 功能表上，依序選擇 [新增]****、[專案]****、[Visual C++]、[測試]**** 和 [C++ 單元測試專案]****。

  2. 在方案總管中，於測試專案的捷徑功能表上，選擇 [屬性]****。 專案的屬性視窗便會開啟。

  3. 依序選擇 [組態屬性]****、[連結器]****、[輸入]**** 和 [其他相依性]****。

       選擇 [編輯]****，然後新增 **.obj** 或 **.lib** 檔案的名稱。 不要使用完整路徑名稱。

  4. 依序選擇 [組態屬性]****、[連結器]****、[一般]**** 和 [其他程式庫目錄]****。

       選擇 [編輯]****，然後新增 **.obj** 或 **.lib** 檔案的目錄路徑。 該路徑通常是位於受測專案的組建資料夾內。

  5. 依序選擇 [組態屬性]****、[VC++ 目錄]**** 和 [Include 目錄]****。

       選擇 [編輯]****，然後新增受測專案的標頭目錄。

  移至[撰寫單元測試](#addTests)程序。

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a> 在相同專案中新增單元測試

1. 修改產品程式碼專案屬性，以包含單元測試所需的標頭和程式庫檔案。

   1. 在 [方案總管] 中，在受測專案的捷徑功能表中選擇 [屬性]。 專案的屬性視窗便會開啟。

   2. 依序選擇 [組態屬性]**** 和 [VC++ 目錄]****。

   3. 編輯 Include 目錄和程式庫目錄：

       |屬性|值|
       |-|-|
       |**包含目錄**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**程式庫目錄**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. 加入 C++ 單元測試檔案：

   - 在方案總管中，於專案的捷徑功能表中，依序選擇 [新增]****、[新增項目]**** 和 [C++ 單元測試]****。

   移至[撰寫單元測試](#addTests)程序。

## <a name="writing-the-unit-tests"></a><a name="addTests"></a> 撰寫單元測試

1. 在每個單元測試程式碼檔案中，為受測專案的標頭加入一個 `#include` 陳述式。

2. 在單元測試程式碼檔案中加入測試類別和方法。 例如：

   ```cpp
   #include "stdafx.h"
   #include "CppUnitTest.h"
   #include "MyProjectUnderTest.h"
   using namespace Microsoft::VisualStudio::CppUnitTestFramework;
   namespace MyTest
   {
     TEST_CLASS(MyTests)
     {
     public:
         TEST_METHOD(MyTestMethod)
         {
             Assert::AreEqual(MyProject::Multiply(2,3), 6);
         }
     };
   }
   ```

   如需詳細資訊，請參閱[使用測試總管針對機器碼執行單元測試](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)。

## <a name="run-the-tests"></a>執行測試

1. 在 [ **檢視** ] 功能表上，選擇 [ **其他視窗**]、[ **測試總管**]。

2. 在 [測試瀏覽器] 中，選擇 [ **全部執行**]。

   如需詳細資訊，請參閱[快速入門：搭配測試總管進行以測試為導向的開發工作](../test/quick-start-test-driven-development-with-test-explorer.md)。
