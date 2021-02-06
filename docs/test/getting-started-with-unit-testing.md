---
title: 開始使用單元測試
description: 使用 Visual Studio 來定義及執行單元測試，以維護程式碼健全狀況，並在客戶執行之前尋找錯誤和錯誤。
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 328f7540846f923fe186a76c4dcc03347f9c3214
ms.sourcegitcommit: 686aa3516594ab951d48b192fc60b102eedaf9b7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2021
ms.locfileid: "99628015"
---
# <a name="get-started-with-unit-testing"></a>開始使用單元測試

使用 Visual Studio 來定義和執行單元測試，藉以維護程式碼的健康狀態、確定程式碼涵蓋範圍，以及在客戶遭遇問題之前找出錯誤和失敗。 經常執行單元測試，以確定您的程式碼運作正常。

在本文中，程式碼和圖例使用 c #，但概念和功能適用于 .NET 語言、c + +、Python、JavaScript 和 TypeScript。

## <a name="create-unit-tests"></a>建立單元測試

本節說明如何建立單元測試專案。

1. 在 Visual Studio 中開啟您要測試的專案。

   為了示範範例單元測試的目的，本文會測試一個簡單的 "Hello World" c # 專案，名為 **helloworld**。 此類專案的範例程式碼如下所示：

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

1. 在 [方案總管] 中，選取解決方案節點。 然後，從頂端功能表列選取 [檔案  >  **加入**  >  **新專案**]。

1. 在 [新增專案] 對話方塊中，尋找您想要使用之測試架構的單元測試專案範本，例如 MSTest，然後選取它。

   從 Visual Studio 2017 14.8 版開始，.NET 語言包含 NUnit 和 xUnit 的內建範本。 針對 c + +，您必須選取語言所支援的測試架構。 針對 Python，請參閱 [設定 python 程式碼中的單元測試](../python/unit-testing-python-in-visual-studio.md) ，以設定您的測試專案。

   > [!TIP]
   > 針對 c #，您可以使用更快速的方法，從程式碼建立單元測試專案。 如需詳細資訊，請參閱 [建立單元測試專案和測試方法](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods)。 若要搭配 .NET Core 或 .NET Standard 使用此方法，則需要 Visual Studio 2019。

   下圖顯示的是在 .NET 中支援的 MSTest 單元測試。

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 的單元測試專案範本](media/vs-2019/add-new-test-project.png)

   按一下 [下一步]，選擇測試專案的名稱，然後按一下 [建立]。

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Visual Studio 2019 的單元測試專案範本](media/mstest-test-project-template.png)

   選擇測試專案的名稱，例如 HelloWorldTests，然後按一下 **[確定]**。

   ::: moniker-end

   專案已加入您的方案中。

   ![[方案總管] 中的單元測試專案](media/vs-2019/solution-explorer.png)

1. 在單元測試專案中，以滑鼠右鍵按一下 [參考] 或 [相依性]，然後選擇 [新增參考]，在您想要測試的專案中新增參考。

1. 選取包含您要測試之程式碼的專案，然後按一下 [確定]**OK**。

   ![在 Visual Studio 中新增專案參考](media/vs-2019/reference-manager.png)

1. 將程式碼新增至單元測試方法。

   例如，您可以選取符合測試架構的正確檔索引標籤，以使用下列程式碼：僅限 .NET) 上支援 MSTest、NUnit 或 xUnit (。

   # <a name="mstest"></a>[MSTest](#tab/mstest)

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

   # <a name="nunit"></a>[NUnit](#tab/nunit)

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

    # <a name="xunit"></a>[xUnit](#tab/xunit)

    ```csharp
    using System;
    using Xunit;
    using System.IO;
    
    namespace HelloWorldTests
    {
        public class UnitTest1
        {
            private const string Expected = "Hello World!";
            [Fact]
            public void Test1()
            {
                using (var sw = new StringWriter())
                {
                    Console.SetOut(sw);
                    HelloWorldCore.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

## <a name="run-unit-tests"></a>執行單元測試

1. 開啟 [ [測試瀏覽器](../test/run-unit-tests-with-test-explorer.md)]。

   ::: moniker range=">=vs-2019"
   若要開啟 test explorer， 請 > 從頂端功能表列中選擇 [test **test explorer** ] (或按下 **Ctrl** + **E**， **T**) 。
   ::: moniker-end
   ::: moniker range="vs-2017"
   若要開啟 test explorer， 請 >  > 從頂端功能表列中選擇 [測試 Windows **test explorer** ]。
   ::: moniker-end

1. 按一下 [**執行所有** (]，或按 **Ctrl**  +  **R**、 **V**) 來執行單元測試。

   ![在測試總管中執行單元測試](media/vs-2019/test-explorer-run-all.png)

   測試完成之後，綠色的核取記號表示測試通過。 紅色的 "x" 圖示表示測試失敗。

   ![在 [測試總管] 中檢閱單元測試結果](media/vs-2019/unit-test-passed.png)

> [!TIP]
> 您可以使用 [[測試總管]](../test/run-unit-tests-with-test-explorer.md) 從內建的測試架構 (MSTest) 或從協力廠商測試架構執行單元測試。 您也可以將測試分組成分類、篩選測試清單，以及建立、儲存和執行測試播放清單。 您也可以偵錯測試和分析測試效能和程式碼涵蓋範圍。

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>查看即時單元測試結果 (Visual Studio Enterprise) 

如果您在 Visual Studio 2017 或更新版本中使用 MSTest、xUnit 或 NUnit 測試架構，則可以查看單元測試的即時結果。

> [!NOTE]
> 若要遵循這些步驟，需要 Visual Studio Enterprise。

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

## <a name="use-a-third-party-test-framework"></a>使用協力廠商測試架構

您可以使用協力廠商測試架構（例如提升、Google 和 NUnit），根據您的程式設計語言，在 Visual Studio 中執行單元測試。 若要使用協力廠商架構：

- 使用 **NuGet 套件管理員** 安裝您選擇的架構 NuGet 套件。

- 從 Visual Studio 2017 14.6 版開始 ( .NET) ，Visual Studio 包含 NUnit 和 xUnit 測試架構的預先設定測試專案範本。 範本也包含必要的 NuGet 套件，以啟用支援。

-  (Visual Studio 2017 和更新版本中的 c + +) ，某些架構（例如提升）已包含在內。 如需詳細資訊，請參閱 [Visual Studio 中的 C/c + + 撰寫單元測試](../test/writing-unit-tests-for-c-cpp.md)。

若要加入單元測試專案：

1. 開啟包含您要測試之程式碼的解決方案。

2. 以滑鼠右鍵按一下 [方案總管] 中的解決方案，然後選擇 [新增] > [新增專案]。

3. 選取單元測試專案範本。

   在此範例中，選取 [NUnit](https://nunit.org/)

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

6. 從 **test Explorer** 執行測試，或以滑鼠右鍵按一下測試程式碼，然後選擇 [**執行測試 (s])** (或 **Ctrl**  +  **R**、 **T**) 。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [單元測試基本概念](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [針對受控碼建立和執行單元測試](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
