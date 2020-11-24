---
title: 開始使用單元測試
description: 使用 Visual Studio 來定義和執行單元測試，藉以維護程式碼的健康狀態、確定程式碼涵蓋範圍，以及在客戶遭遇問題之前找出錯誤和失敗。
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3daff1a7b7c2e62b4ca4a508c5c8dd31261a40dd
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441777"
---
# <a name="get-started-with-unit-testing"></a>開始使用單元測試

使用 Visual Studio 來定義和執行單元測試，藉以維護程式碼的健康狀態、確定程式碼涵蓋範圍，以及在客戶遭遇問題之前找出錯誤和失敗。 經常執行單元測試，以確定您的程式碼運作正常。

## <a name="create-unit-tests"></a>建立單元測試

本節說明如何建立單元測試專案。

1. 在 Visual Studio 中開啟您要測試的專案。

   為了示範範例單元測試的目的，本文會測試名為 **helloworld** 的簡單 "Hello World" 專案。 此類專案的範例程式碼如下所示：

   ```csharp
   namespace HelloWorldCore

      public class Program
      {
         public static void Main()
         {
            Console.WriteLine("Hello World!");
         }
      }
   ```

1. 在 [方案總管] 中，選取解決方案節點。 然後，從頂端功能表列選取 [檔案 **File**  >  **加入**  >  **新專案**]。

1. 在新的專案對話方塊中，尋找並選取您希望使用之測試架構的單元測試專案範本。

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 的單元測試專案範本](media/vs-2019/add-new-test-project.png)

   按一下 [下一步]，選擇測試專案的名稱，然後按一下 [建立]。

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Visual Studio 2019 的單元測試專案範本](media/mstest-test-project-template.png)

   選擇測試專案的名稱，然後按一下 [確定]。

   ::: moniker-end

   專案已加入您的方案中。

   ![[方案總管] 中的單元測試專案](media/vs-2019/solution-explorer.png)

1. 在單元測試專案中，以滑鼠右鍵按一下 [參考] 或 [相依性]，然後選擇 [新增參考]，在您想要測試的專案中新增參考。

1. 選取包含您要測試之程式碼的專案，然後按一下 [確定]**OK**。

   ![在 Visual Studio 中新增專案參考](media/vs-2019/reference-manager.png)

1. 將程式碼新增至單元測試方法。

   例如，您可以使用下列程式碼，針對 MSTest 專案使用下列程式碼。

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class UnitTest1
      {
         private const string Expected = "Hello World!";
         [TestMethod]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

   或者，若為 NUnit 專案，您可以使用下列程式碼。

   ```csharp
   using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      public class Tests
      {
         private const string Expected = "Hello World!";

         [SetUp]
         public void Setup()
         {
         }
         [Test]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

> [!TIP]
> 如需有關建立單元測試的詳細資訊，請參閱 [針對 managed 程式碼建立和執行單元測試](walkthrough-creating-and-running-unit-tests-for-managed-code.md)。

## <a name="run-unit-tests"></a>執行單元測試

1. 開啟 [ [測試瀏覽器](../test/run-unit-tests-with-test-explorer.md)]。

   ::: moniker range=">=vs-2019"
   若要開啟 [測試流覽 **Test** 器]，請 > 從頂端功能表列中選擇 [測試 **測試瀏覽器**]。
   ::: moniker-end
   ::: moniker range="vs-2017"
   若要開啟 test explorer， **Test** 請 > **Windows** > 從頂端功能表列中選擇 [測試 Windows **test explorer** ]。
   ::: moniker-end

1. 按一下 [全部執行] 執行您的單元測試。

   ![在測試總管中執行單元測試](media/vs-2019/test-explorer-run-all.png)

   測試完成之後，綠色的核取記號表示測試通過。 紅色的 "x" 圖示表示測試失敗。

   ![在 [測試總管] 中檢閱單元測試結果](media/vs-2019/unit-test-passed.png)

> [!TIP]
> 您可以使用 [[測試總管]](../test/run-unit-tests-with-test-explorer.md) 從內建的測試架構 (MSTest) 或從協力廠商測試架構執行單元測試。 您也可以將測試分組成分類、篩選測試清單，以及建立、儲存和執行測試播放清單。 您也可以偵錯測試和分析測試效能和程式碼涵蓋範圍。

## <a name="view-live-unit-test-results"></a>檢視即時單元測試結果

如果您在 Visual Studio 2017 或更新版本中使用 MSTest、xUnit 或 NUnit 測試架構，則可以查看單元測試的即時結果。

> [!NOTE]
> 只有 Enterprise Edition 才能使用 Live Unit Testing。

1. 從 [測試] 功能表中選擇 [測試] > [Live Unit Testing] > [啟動] 來開啟 Live Unit Testing。

   ::: moniker range="vs-2017"

   ![開啟即時單元測試](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![在 Visual Studio 2019 中啟動 Live Unit Testing](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. 當您撰寫和編輯程式碼時，在程式碼編輯器視窗中檢視測試的結果。

   ![檢閱測試的結果](media/vs-2019/live-unit-testing-results.png)

1. 按一下測試結果指標查看詳細資訊，例如涵蓋該方法的測試名稱。

   ![選擇測試結果指標](media/vs-2019/live-unit-testing-details.png)

如需 Live Unit Testing 的詳細資訊，請參閱 [Live Unit Testing](../test/live-unit-testing-intro.md)。

## <a name="generate-unit-tests-with-intellitest"></a>使用 IntelliTest 產生單元測試

當您執行 IntelliTest 時，您可以看到失敗的測試，並新增任何必要的程式碼來修正它們。 您可以選取產生的測試，將其儲存到測試專案中做為迴歸套件。 當您變更程式碼時，請重新執行 IntelliTest，如此所產生的測試才能與您的程式碼變更保持同步。 若要了解做法，請參閱[使用 IntelliTest 為程式碼產生單元測試](../test/generate-unit-tests-for-your-code-with-intellitest.md)。

> [!TIP]
> IntelliTest 僅供以 .NET Framework 為目標的受控程式碼使用。

![使用 IntelliTest 產生單元測試](media/intellitest.png)

## <a name="analyze-code-coverage"></a>分析程式碼涵蓋範圍

若要判斷單元測試等自動程式碼測試實際測試的專案程式碼比例，您可以使用 Visual Studio 程式碼涵蓋範圍功能。 為有效防範錯誤 (bug)，您的測試應該要使用大部分的程式碼。 若要瞭解作法，請參閱 [使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

## <a name="use-a-third-party-test-framework"></a>使用協力廠商測試架構

您可以使用協力廠商測試架構 (例如 Boost、Google 與 NUnit)，在 Visual Studio 中執行單元測試。 使用 **NuGet 套件管理員** 安裝您選擇的架構 NuGet 套件。 或者，針對 NUnit 和 xUnit 測試架構，Visual Studio 包含預先設定的測試專案範本，這些範本包含必要的 NuGet 套件。

建立使用 [NUnit](https://nunit.org/) 的單元測試：

1. 開啟包含您要測試之程式碼的解決方案。

2. 以滑鼠右鍵按一下 [方案總管] 中的解決方案，然後選擇 [新增] > [新增專案]。

3. 選取 [NUnit 測試專案] 專案範本。

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 的 NUnit 測試專案範本](media/vs-2019/nunit-test-project-template.png)

   按一下 [下一步]、命名專案，然後按一下 [建立]。

   ::: moniker-end

   ::: moniker range="vs-2017"

   命名專案，然後按一下 [確定] 建立專案。

   ::: moniker-end

   專案範本包括 NUnit 和 NUnit3TestAdapter 的 NuGet 參考。

   ![[方案總管] 中的 NUnit NuGet 相依性](media/vs-2019/nunit-nuget-dependencies.png)

4. 從測試專案將參考新增至包含您想要測試之程式碼的專案。

   以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取 [新增] > [參考]。 (您也可以從 [參考] 或 [相依性] 節點的滑鼠右鍵功能表中加入參考。)

5. 將程式碼新增至您的測試方法。

   ![將程式碼新增至您的單元測試程式碼檔案](media/vs-2019/unit-test-method.png)

6. 從 [測試總管] 執行測試，或在測試程式碼上按一下滑鼠右鍵，然後選擇 [執行測試]。

## <a name="see-also"></a>另請參閱

* [逐步解說：針對受控碼建立和執行單元測試](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [建立單元測試命令](create-unit-tests-menu.md)
* [使用 IntelliTest 產生測試](generate-unit-tests-for-your-code-with-intellitest.md)
* [使用 [測試總管] 執行測試](run-unit-tests-with-test-explorer.md)
* [分析程式碼涵蓋範圍](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
