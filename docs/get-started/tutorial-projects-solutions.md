---
title: 專案和解決方案簡介
description: 瞭解專案和解決方案之間的差異，以及如何在 Visual Studio 中使用它們。
ms.date: 11/17/2020
ms.technology: vs-ide-general
ms.custom:
- acquisition
- get-started
- SEO-VS-2020
ms.topic: tutorial
f1_keywords:
- project.addnewitem
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f962d9e534262fd12cd0ce5c808c9c604db466b
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308398"
---
# <a name="introduction-to-projects-and-solutions"></a>專案和解決方案簡介

在這篇簡介文章中，我們將探討在 Visual Studio 中建立「解決方案」和「專案」的意義。 解決方案是用來組織一或多個相關程式碼專案的容器，例如類別庫專案和對應的測試專案。 我們會查看專案的屬性以及它可包含的一些檔案。 我們也會建立兩個專案之間的參考。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2022"

如果您尚未安裝 Visual Studio 2022 Preview，請前往 [Visual Studio 2022 preview 下載](https://visualstudio.microsoft.com/vs/preview/vs2022) 頁面，免費進行安裝。

::: moniker-end

我們將會從頭建構方案和專案，作為教育練習以了解專案的概念。 在 Visual Studio 的一般使用中，您可能在建立新專案時使用 Visual Studio 所提供的一些各種專案「範本」。

> [!NOTE]
> 在 Visual Studio 中開發應用程式不需要方案和專案。 您也可以只開啟包含程式碼的資料夾，並開始撰寫程式碼、建置和偵錯。 例如，如果您複製 [GitHub](https://github.com/) 存放庫，它可能不會包含 Visual Studio 專案和方案。 如需詳細資訊，請參閱[在 Visual Studio 中不使用專案或方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

## <a name="solutions-and-projects"></a>方案和專案

儘管名稱為方案，但其並非「解答」。 解決方案僅是 Visual Studio 用來組織一或多個相關專案的容器。 當您在 Visual Studio 中開啟解決方案時，會自動載入解決方案包含的所有專案。

### <a name="create-a-solution"></a>建立方案

我們會建立空白解決方案以開始探索。 在您了解 Visual Studio 之後，可能不會發現自己太過頻繁地建立空白方案。 當您建立新的專案時，Visual Studio 會自動建立要儲存專案的方案 (若尚未開啟方案)。

::: moniker range="vs-2017"

1. 開啟 Visual Studio。

1. 在頂端功能表列上 **，選取 [** 檔案 > **新增** > **專案**]。

   此時會開啟 [新增專案] 對話方塊。

1. 在左窗格中，展開 [ **其他專案類型**]，然後選取 [ **Visual Studio 方案**]。 在中間窗格中，選取 [ **空白方案** ] 範本。 為您的方案 **QuickSolution** 命名，然後選取 [ **確定]** 按鈕。

   ![Visual Studio 2017 中的空白解決方案範本](media/tutorial-projects-new-solution.png "Visual Studio 2017 中的空白方案範本。")

   [起始頁] 隨即關閉，而且方案會出現在 Visual Studio 視窗右側的 [方案總管] 中。 您可能會經常使用方案總管來瀏覽專案的內容。

::: moniker-end

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。

2. 在 [開始] 視窗中，選取 [ **建立新專案**]。

3. 在 [ **建立新專案** ] 頁面的 [搜尋] 方塊中，輸入 **空白的方案** ，並選取 [ **空白方案** ] 範本，然後選取 **[下一步]**。

   ![Visual Studio 2019 中的空白方案範本](media/vs-2019/tutorial-projects-blank-solution-template.png "Visual Studio 2019 中的空白方案範本。")

    > [!TIP]
    > 如果您已安裝數個工作負載，則 **空白的解決方案** 範本可能不會出現在搜尋結果清單的頂端。 嘗試根據清單的搜尋區段來滾動至 **其他結果** 。 它應該會出現在該處。

4. 將方案命名為 **QuickSolution**，然後選取 [ **建立**]。

   解決方案隨即會出現在 Visual Studio 視窗右側的 [方案總管] 中。 您可能會經常使用方案總管來瀏覽專案的內容。

::: moniker-end

### <a name="add-a-project"></a>新增專案

現在讓我們將第一個專案新增至解決方案。 我們將從空白專案開始，並將需要的項目新增至專案。

::: moniker range="vs-2017"

1. 在 **方案總管** 的 **方案 ' QuickSolution '** 的滑鼠右鍵功能表或內容功能表中，選取 [**加入** > **新專案**]。

   [ **加入新的專案** ] 對話方塊隨即開啟。

1. 在左窗格中，展開 [ **Visual c #** ]，然後選取 [ **Windows 桌面**]。 然後，在中間窗格中，選取 **空的專案 ( .NET Framework)** 範本。 將專案命名為 **QuickDate**，然後選取 **[確定]**。

   名為 QuickDate 的專案會出現在 **方案總管** 的方案下方。 它目前包含稱為 *App.config* 的單一檔案。

   > [!NOTE]
   > 如果您在對話方塊的左窗格中看不到 **Visual c #** ，則必須安裝 **.net 桌面開發** Visual Studio 工作負載。 Visual Studio 使用以工作負載為基礎的安裝，只安裝您所需的開發類型所需的元件。 安裝新工作負載的簡單方式，就是在 [**加入新專案**] 對話方塊的左下角選取 **開啟的 Visual Studio 安裝程式** 連結。 Visual Studio 安裝程式啟動之後，請選取 **.net 桌面開發** 工作負載，然後選取 [ **修改** ] 按鈕。
   >
   > ![開啟 Visual Studio 安裝程式連結](media/tutorial-projects-open-installer.png "Visual Studio 2017 中 [加入新的專案] 對話方塊中的 [開啟 Visual Studio 安裝程式] 連結。")

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 **方案總管** 的 **方案 ' QuickSolution '** 的滑鼠右鍵功能表或內容功能表中，選取 [**加入** > **新專案**]。

   隨即開啟一個對話方塊，表示要 [新增專案]。

1. 在頂端的搜尋方塊中輸入文字 **空白**，然後在 [語言] 底下選取 [C#]。

1. 選取 **( .NET Framework) 範本的空白專案** ，然後選取 **[下一步]**。

1. 將專案命名為 **QuickDate**，然後選取 [ **建立**]。

   名為 QuickDate 的專案會出現在 **方案總管** 的方案下方。 它目前包含稱為 *App.config* 的單一檔案。

   > [!NOTE]
   > 如果您沒有看到 **空白專案 ( .NET Framework)** 範本，則必須安裝 **.net 桌面開發** Visual Studio 工作負載。 Visual Studio 使用以工作負載為基礎的安裝，只安裝您所需的開發類型所需的元件。
   >
   >當您建立新專案時，安裝新工作負載的簡單方式，就是在顯示 **未找到您要尋找** 之專案的文字下，選取 [**安裝更多工具和功能**] 連結。 Visual Studio 安裝程式啟動之後，請選取 **.net 桌面開發** 工作負載，然後選取 [ **修改** ] 按鈕。
   >
   > ![開啟 Visual Studio 安裝程式連結](media/vs-2019/tutorial-projects-open-installer.png "在 Visual Studio 的 [建立新專案] 對話方塊中的 [開啟 Visual Studio 安裝程式] 連結。")

::: moniker-end

## <a name="add-an-item-to-the-project"></a>將項目新增至專案

我們有空白專案。 請新增程式碼檔案。

1. 在 **方案總管** 中，從 **QuickDate** 專案的滑鼠右鍵功能表或操作功能表中，選取 [**加入**  >  **新專案**]。

   [ **加入新專案** ] 對話方塊隨即開啟。

1. 展開 [ **Visual c # 專案**]，然後選取 [程式 **代碼**]。 在中間窗格中，選取 [ **類別** 專案] 範本。 將類別命名為行事 **曆**，然後選取 [ **加入** ] 按鈕。

   名為行事 *曆* 的檔案會加入至專案。 一端的 *.cs* 是提供給 C# 程式碼檔案的副檔名。 此檔案會出現在方案總管的視覺效果專案階層中，並在編輯器中開啟其內容。

1. 以下列程式碼取代行事 *曆 .cs* 檔案的內容：

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   您不需要瞭解程式碼的作用，但如果想要的話，您可以按下 **Ctrl** F5 來執行程式， + 看看它會將今天的日期列印到主控台 (或標準輸出) 視窗。

## <a name="add-a-second-project"></a>新增第二個專案

解決方案通常會包含多個專案，而且這些專案通常會彼此參考。 解決方案中有些專案可能是類別庫、有些是可執行的應用程式，有些可能是單元測試專案或網站。

請將單元測試專案新增至解決方案。 現在我們先從專案範本開始，因此不需要將額外程式碼檔案新增至專案。

1. 在 **方案總管** 的 **方案 ' QuickSolution '** 的滑鼠右鍵功能表或內容功能表中，選取 [**加入**  >  **新專案**]。

::: moniker range="vs-2017"

2. 在左窗格中，展開 [ **Visual c #** ]，然後選取 [ **測試** ] 類別。 在中間窗格中，選取 [ **( .Net Core) 專案範本的 MSTest 測試專案** ]。 將專案命名為 **QuickTest**，然後選取 **[確定]**。

   第二個專案會新增至 [方案總管]，並在編輯器中開啟名為 *UnitTest1.cs* 的檔案。

   ![包含兩個專案的 Visual Studio 方案總管](media/tutorial-projects-solution-explorer.png "方案總管 Visual Studio 2017 中的兩個專案。")

::: moniker-end

::: moniker range=">=vs-2019"

2. 在 [新增專案] 對話方塊的頂端搜尋方塊中輸入文字 **單元測試**，然後在 [語言] 底下選取 [C#]。

3. 選取 .NET Core 的 **單元測試專案** 專案範本，然後選取 **[下一步]**。

   > [!NOTE]
   > 從 Visual Studio 2019 16.9 版開始，MSTest 專案範本名稱從 **Mstest 單元測試專案變更 ( .Net Core)** 變更為 **單元測試專案**。 在此更新中，專案建立中的數個步驟有所變更。

4. 將專案命名為 **QuickTest**，然後選取 **[下一步]**。

5. 選擇建議的目標架構 ( .NET Core 3.1) 或 .NET 5，然後選擇 [ **建立**]。

   第二個專案會新增至 [方案總管]，並在編輯器中開啟名為 *UnitTest1.cs* 的檔案。

   ![包含兩個專案的 Visual Studio 方案總管](media/vs-2019/tutorial-projects-solution-explorer.png "方案總管 Visual Studio 中有兩個專案。")

::: moniker-end

## <a name="add-a-project-reference"></a>新增專案參考

我們將使用新的單元測試專案來測試 **QuickDate** 專案中的方法，因此必須新增該專案的參考。 這會建立兩個專案之間的「組建相依性」，表示在建置方案時會先建置 **QuickDate** 再建置 **QuickTest**。

::: moniker range="vs-2017"

1. 選取 **QuickTest** 專案中的 [相依性] 節點，然後從滑鼠右鍵功能表或操作功能表中，選取 [**加入參考** **]** 。

   [參考管理員] 對話方塊隨即開啟。

1. 在左窗格中，展開 [ **專案** ]，然後選取 [ **方案**]。 在中間窗格中，選取 [ **QuickDate**] 旁邊的核取方塊，然後選取 **[確定]**。

   隨即新增 **QuickDate** 專案的參考。

   ![方案總管的螢幕擷取畫面，其中顯示 Visual Studio 中的專案參考](media/vs-2019/tutorial-projects-solution-explorer-reference.png "方案總管的螢幕擷取畫面，其中顯示 Visual Studio 中的專案參考。")

::: moniker-end

::: moniker range=">=vs-2019"

1. 選取 **QuickTest** 專案中的 [相依性] 節點，然後從滑鼠右鍵按一下或操作功能表中，選取 [**加入專案參考**... **]** 。

   [參考管理員] 對話方塊隨即開啟。

1. 展開左窗格中的 [ **專案**]，然後選取 [ **方案**]。 在中間窗格中，選取 [ **QuickDate**] 旁邊的核取方塊，然後選取 **[確定]**。

   隨即新增 **QuickDate** 專案的參考。

   ![顯示 Visual Studio 2019 中專案參考方案總管的螢幕擷取畫面](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

::: moniker-end

## <a name="add-test-code"></a>新增測試程式碼

1. 我們現在會將測試程式碼新增至 C# 測試程式碼檔案。 以下列程式碼取代 *UnitTest1.cs* 檔案的內容：

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace QuickTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestGetCurrentDate()
           {
               Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate());
           }
       }
   }
   ```

   您會在一些程式碼下方看到紅色曲線。 我們將修正這個錯誤，方法是將測試專案設為 **QuickDate** 專案的 [friend 組件](/dotnet/standard/assembly/friend-assemblies)。

1. 回到 [QuickDate] 專案，開啟  檔案 (如果尚未開啟的話)。 將下列 [using 陳述式](/dotnet/csharp/language-reference/keywords/using-statement)和 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性新增至檔案頂端，以解決測試專案中的錯誤。

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   程式碼檔應該如下：

   ![CSharp 程式碼](media/tutorial-projects-cs-code.png "本文的「加入測試程式碼」一節中的程式碼片段。")

## <a name="project-properties"></a>專案屬性

*Calendar.cs* 程式碼檔案中包含 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的行會參考 **QuickTest** 專案的組件名稱 (檔案名稱)。 組件名稱不一定會與專案名稱相同。 若要尋找專案的組件名稱，請開啟專案屬性。

1. 在方案總管中，選取 **QuickTest** 專案。 從右鍵功能表或操作功能表中，選擇 [屬性]，或只按 **Alt**+**Enter** 鍵。

   專案的 *屬性頁* 會在 [ **應用程式** ] 索引標籤上開啟。屬性頁包含專案的各種設定。 請注意，**QuickTest** 專案的組件名稱確實是 "QuickTest"。 如果您想要變更它，則這是進行變更的位置。 然後，當您建置測試專案時，所產生二進位檔案的名稱會從 *QuickTest.dll* 變更為您選擇的任何名稱。

   ![專案屬性](media/tutorial-projects-netcore-properties.png "Visual Studio 中的 [專案屬性] 對話方塊。")

1. 探索專案屬性頁的一些其他索引標籤 (例如 [建置] 和 [偵錯])。 不同專案類型的這些索引標籤不同。

## <a name="next-steps"></a>後續步驟

::: moniker range="vs-2017"

如果您想要檢查單元測試是否正常運作，請從功能表列選擇 [**測試**  >  **執行**  >  **所有測試**]。 稱為 [測試總管] 的視窗隨即開啟，而且您應該會看到 **TestGetCurrentDate** 測試通過。

::: moniker-end

::: moniker range=">=vs-2019"

如果您想要檢查單元測試是否正常運作，請從功能表列選擇 [**測試**  >  **執行所有測試**]。 稱為 [測試總管] 的視窗隨即開啟，而且您應該會看到 **TestGetCurrentDate** 測試通過。

::: moniker-end

![Visual Studio 的 [測試總管] 顯示已通過測試](media/tutorial-projects-test-explorer.png "Visual Studio 中的 test Explorer 顯示通過的測試。")

::: moniker range="vs-2017"

> [!TIP]
> 如果 [測試總管] 未自動開啟，請從功能表列選擇 [測試] > [Windows] > [測試總管] 開啟它。

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> 如果 [ **test explorer** ] 未自動開啟，請從功能表列選擇 [ **test**  >  **test explorer** ] 來開啟它。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [使用專案和方案](../ide/creating-solutions-and-projects.md)
- [管理專案和解決方案屬性](../ide/managing-project-and-solution-properties.md)
- [管理專案中的參考](../ide/managing-references-in-a-project.md)
- [在 Visual Studio 中不使用專案或方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE 概觀](../get-started/visual-studio-ide.md)
