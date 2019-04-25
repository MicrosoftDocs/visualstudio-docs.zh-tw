---
title: 專案和解決方案簡介
ms.date: 12/11/2017
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 498f52a85f52206bf5c12a2d591ce169eb0775fc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943735"
---
# <a name="learn-about-projects-and-solutions"></a>了解專案與解決方案

在這篇簡介文章中，我們將探討在 Visual Studio 中建立「解決方案」和「專案」的意義。 解決方案是用來組織一或多個相關程式碼專案的容器，例如類別庫專案和對應的測試專案。 我們會查看專案的屬性以及它可包含的一些檔案。 我們也會建立兩個專案之間的參考。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)頁面免費進行安裝。

::: moniker-end

我們將會從頭建構方案和專案，作為教育練習以了解專案的概念。 在 Visual Studio 的一般使用中，您可能在建立新專案時使用 Visual Studio 所提供的一些各種專案「範本」。

> [!NOTE]
> 在 Visual Studio 中開發應用程式不需要方案和專案。 您也可以只開啟包含程式碼的資料夾，並開始撰寫程式碼、建置和偵錯。 例如，如果您複製 [GitHub](https://github.com/) 存放庫，則它可能不會包含 Visual Studio 專案和方案。 如需詳細資訊，請參閱[在 Visual Studio 中不使用專案或方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

## <a name="solutions-and-projects"></a>方案和專案

儘管名稱為方案，但其並非「解答」。 解決方案僅是 Visual Studio 用來組織一或多個相關專案的容器。 當您在 Visual Studio 中開啟解決方案時，會自動載入解決方案包含的所有專案。

### <a name="create-a-solution"></a>建立解決方案

我們會建立空白解決方案以開始探索。 在您了解 Visual Studio 之後，可能不會發現自己太過頻繁地建立空白方案。 當您建立新的專案時，Visual Studio 會自動建立要儲存專案的方案 (若尚未開啟方案)。

::: moniker range="vs-2017"

1. 開啟 Visual Studio。

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

   [ **新增專案** ] 對話方塊隨即開啟。

1. 在左窗格中，展開 [其他專案類型]，然後選擇 [Visual Studio 解決方案]。 在中央窗格中，選擇 [空白方案] 範本。 將方案命名為 **QuickSolution**，然後選擇 [確定] 按鈕。

   ![Visual Studio 中的空白方案範本](media/tutorial-projects-new-solution.png)

   [起始頁] 隨即關閉，而且方案會出現在 Visual Studio 視窗右側的 [方案總管] 中。 您可能會經常使用方案總管來瀏覽專案的內容。

::: moniker-end

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。

2. 在開始視窗中，選擇 [建立新專案]。

3. 在 [建立新專案] 頁面上，於搜尋方塊中輸入**空白的解決方案**、選取 [空白的解決方案] 範本，然後選擇 [下一步]。

4. 將解決方案命名為 **QuickSolution**，然後選擇 [建立]。

   解決方案隨即會出現在 Visual Studio 視窗右側的 [方案總管] 中。 您可能會經常使用方案總管來瀏覽專案的內容。

::: moniker-end

### <a name="add-a-project"></a>新增專案

現在讓我們將第一個專案新增至解決方案。 我們將從空白專案開始，並將需要的項目新增至專案。

1. 在 [方案總管] 中，從 [解決方案 'QuickSolution'] 的右鍵功能表或操作功能表中，選擇 [新增] > [新增專案]。

   [ **加入新的專案** ] 對話方塊隨即開啟。

1. 在左窗格中，展開 [Visual C#]，然後選擇 [Windows 桌面]。 然後，在中間窗格中，選擇 [空白專案 (.NET Framework)] 範本。 將專案命名為 **QuickDate**，然後選擇 [確定] 按鈕。

   名為 QuickDate 的專案隨即出現在 [方案總管] 中該方案的下方。 它目前包含稱為 *App.config* 的單一檔案。

   > [!NOTE]
   > 如果您在對話方塊的左窗格中看不到 [Visual C#]，則需要安裝 **.NET 桌面開發** Visual Studio「工作負載」。 Visual Studio 會使用工作負載安裝，只安裝您執行之開發類型所需的元件。 安裝新工作負載的簡單方式是選擇 [新增專案] 對話方塊左下角的 [開啟 Visual Studio 安裝程式] 連結。 Visual Studio Installer 啟動之後，請選擇 [.NET 桌面開發] 工作負載，然後選取 [修改] 按鈕。

   ![開啟 Visual Studio 安裝程式連結](media/tutorial-projects-open-installer.png)

## <a name="add-an-item-to-the-project"></a>將項目新增至專案

我們有空白專案。 請新增程式碼檔案。

1. 在 [方案總管] 中，從 [QuickDate] 的右鍵功能表或操作功能表中，選擇 [新增] > [新增項目]。

   [新增項目] 對話方塊隨即開啟。

1. 展開 [Visual C# 項目]，然後選擇 [程式碼]。 在中間窗格中，選擇 [類別] 項目範本。 將類別命名為 **Calendar**，然後選擇 [新增] 按鈕。

   名為 *Calendar.cs* 的檔案會新增至專案。 一端的 *.cs* 是提供給 C# 程式碼檔案的副檔名。 此檔案會出現在方案總管的視覺效果專案階層中，並在編輯器中開啟其內容。

1. 以下列程式碼取代 *Calendar.cs* 檔案的內容：

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

   您不需要了解程式碼的作用，但如果您想要，則可以按 **Ctrl**+**F5** 執行程式，並查看它是否將今天的日期列印至主控台 (或標準輸出) 視窗。

## <a name="add-a-second-project"></a>新增第二個專案

解決方案通常會包含多個專案，而且這些專案通常會彼此參考。 解決方案中有些專案可能是類別庫、有些是可執行的應用程式，有些可能是單元測試專案或網站。

請將單元測試專案新增至解決方案。 現在我們先從專案範本開始，因此不需要將額外程式碼檔案新增至專案。

1. 在 [方案總管] 中，從 [解決方案 'QuickSolution'] 的右鍵功能表或操作功能表中，選擇 [新增] > [新增專案]。

   [ **加入新的專案** ] 對話方塊隨即開啟。

1. 在左窗格中，展開 [Visual Basic]，然後選擇 [測試] 類別。 在中間窗格中，選擇 [單元測試專案 (.NET Framework)] 專案範本。 將專案命名為 **QuickTest**，然後選擇 [確定] 按鈕。

   第二個專案會新增至**方案總管**，並在編輯器中開啟名為 *UnitTest1.vb* 的檔案。 *.vb* 是提供給 Visual Basic 程式碼檔案的副檔名。

   ![包含兩個專案的 Visual Studio 方案總管](media/tutorial-projects-solution-explorer.png)

## <a name="add-a-project-reference"></a>新增專案參考

我們將使用新的單元測試專案來測試 **QuickDate** 專案中的方法，因此必須新增該專案的參考。 這會建立兩個專案之間的「組建相依性」，表示在建置方案時會先建置 **QuickDate** 再建置 **QuickTest**。

1. 選擇 [QuickTest] 專案中的 [參考] 節點，然後從右鍵功能表或操作功能表中選擇 [新增參考]。

   ![新增參考功能表](media/tutorial-projects-add-reference.png)

   [參考管理員] 對話方塊隨即開啟。

1. 在左窗格中，展開 [專案]，然後選擇 [解決方案]。 在中間窗格中，選擇 [QuickDate] 旁邊的核取方塊，然後選擇 [確定] 按鈕。

   隨即新增 **QuickDate** 專案的參考。

## <a name="add-test-code"></a>新增測試程式碼

1. 我們現在會將測試程式碼新增至 Visual Basic 程式碼檔案。 以下列程式碼取代 *UnitTest1.vb* 檔案的內容。

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   您會在一些程式碼下方看到紅色「曲線」。 我們將修正這個錯誤，方法是將測試專案設為 **QuickDate** 專案的 [friend 組件](/dotnet/standard/assembly/friend-assemblies)。

1. 回到 **QuickDate** 專案，開啟尚未開啟的 *Calendar.cs* 檔案，並將下列 [using 陳述式](/dotnet/csharp/language-reference/keywords/using-statement)和 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性新增至檔案頂端，以解決測試專案中的錯誤。

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   程式碼檔應該如下：

   ![CSharp 程式碼](media/tutorial-projects-cs-code.png)

## <a name="project-properties"></a>專案屬性

*Calendar.cs* 程式碼檔案中包含 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的行會參考 **QuickTest** 專案的組件名稱 (檔案名稱)。 組件名稱不一定會與專案名稱相同。 若要尋找專案的組件名稱，請開啟專案屬性。

1. 在方案總管中，選取 **QuickTest** 專案。 從右鍵功能表或操作功能表中，選擇 [屬性]，或只按 **Alt**+**Enter** 鍵。

   專案的「屬性頁」會在 [應用程式] 索引標籤上開啟。屬性頁包含專案的各種設定。 請注意，**QuickTest** 專案的組件名稱確實是 "QuickTest"。 如果您想要變更它，則這是進行變更的位置。 然後，當您建置測試專案時，所產生二進位檔案的名稱會從 *QuickTest.dll* 變更為您選擇的任何名稱。

   ![專案屬性](media/tutorial-projects-properties.png)

1. 探索專案屬性頁的一些其他索引標籤 (例如 [編譯] 和 [設定])。 不同專案類型的這些索引標籤不同。

## <a name="next-steps"></a>後續步驟

如果您想要確認單元測試是否正常運作，請從功能表列中選擇 [測試] > [執行] > [所有測試]。 稱為 [測試總管] 的視窗隨即開啟，而且您應該會看到 **TestGetCurrentDate** 測試通過。

![Visual Studio 的 [測試總管] 顯示已通過測試](media/tutorial-projects-test-explorer.png)

> [!TIP]
> 如果 [測試總管] 未自動開啟，請從功能表列選擇 [測試] > [Windows] > [測試總管] 開啟它。

## <a name="see-also"></a>另請參閱

- [建立專案和解決方案](../ide/creating-solutions-and-projects.md)
- [管理專案及解決方案屬性](../ide/managing-project-and-solution-properties.md)
- [管理專案中的參考](../ide/managing-references-in-a-project.md)
- [在 Visual Studio 中不使用專案或方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE 概觀](../get-started/visual-studio-ide.md)
