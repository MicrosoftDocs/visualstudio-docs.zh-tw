---
title: Visual Basic 專案和解決方案教學課程
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 48b3f2c9aae099e3ae5f2cf2d8c438fb0f9062a2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590211"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>了解使用 Visual Basic 的專案與解決方案

在這篇簡介文章中，我們將探討在 Visual Studio 中建立「解決方案」和「專案」的意義。 解決方案是用來組織一或多個相關程式碼專案的容器，例如類別庫專案和對應的測試專案。 我們會查看專案的屬性以及它可包含的一些檔案。 我們也會建立兩個專案之間的參考。

::: moniker range="vs-2017"

> [!TIP]
> 如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> 如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

我們將會從頭建構方案和專案，作為教育練習以了解專案的概念。 在 Visual Studio 的一般使用中，您可能在建立新專案時使用 Visual Studio 所提供的一些各種專案「範本」。

> [!NOTE]
> 在 Visual Studio 中開發應用程式不需要方案和專案。 您也可以只開啟包含程式碼的資料夾，並開始撰寫程式碼、建置和偵錯。 例如，如果您複製 [GitHub](https://github.com/) 存放庫，則它可能不會包含 Visual Studio 專案和方案。 如需詳細資訊，請參閱[在 Visual Studio 中不使用專案或方案來開發程式碼](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

## <a name="solutions-and-projects"></a>方案和專案

儘管名稱為方案，但其並非「解答」。 解決方案僅是 Visual Studio 用來組織一或多個相關專案的容器。 當您在 Visual Studio 中開啟解決方案時，會自動載入解決方案包含的所有專案。

### <a name="create-a-solution"></a>建立解決方案

我們會建立空白解決方案以開始探索。 在您了解 Visual Studio 之後，可能不會發現自己太過頻繁地建立空白方案。 當您建立新的專案時，Visual Studio 會自動建立要儲存專案的方案 (若尚未開啟方案)。

::: moniker range="vs-2017"

1. 開啟 Visual Studio。

1. 在功能表列上 **，選擇 [** 檔案] > [**新增**>**專案**]。

   [ **新增專案** ] 對話方塊隨即開啟。

1. 在左窗格中，展開 [其他專案類型]，然後選擇 [Visual Studio 解決方案]。 在中央窗格中，選擇 [空白方案] 範本。 將解決方案命名為 **QuickSolution**，然後選擇 [確定]。

   ![Visual Studio 中的空白方案範本](../media/tutorial-projects-new-solution.png)

   [起始頁] 隨即關閉，而且方案會出現在 Visual Studio 視窗右側的 [方案總管] 中。 您可能會經常使用方案總管來瀏覽專案的內容。

::: moniker-end

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。

2. 在開始視窗中，選擇 [建立新專案]。

3. 在 [建立新專案] 頁面上，於搜尋方塊中輸入**空白的解決方案**、選取 [空白的解決方案] 範本，然後選擇 [下一步]。

   ![Visual Studio 2019 中的空白方案範本](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. 將解決方案命名為 **QuickSolution**，然後選擇 [建立]。

   解決方案隨即會出現在 Visual Studio 視窗右側的 [方案總管] 中。 您可能會經常使用方案總管來瀏覽專案的內容。

::: moniker-end

### <a name="add-a-project"></a>新增專案

現在讓我們將第一個專案新增至解決方案。 我們將從空白專案開始，並將需要的項目新增至專案。

::: moniker range="vs-2017"

1. 從**方案總管**中**方案 ' QuickSolution '** 的滑鼠右鍵或操作功能表，選擇 [**加入**>**新增專案**]。

   [ **加入新的專案** ] 對話方塊隨即開啟。

1. 在左窗格中，展開 [Visual Basic]，然後選擇 [Windows 桌面]。 然後，在中間窗格中，選擇 [空白專案 (.NET Framework)] 範本。 將專案命名為 **QuickDate**，然後選擇 [確定] 按鈕。

   名為 QuickDate 的專案隨即出現在 [方案總管] 中該方案的下方。 它目前包含稱為 *App.config* 的單一檔案。

   > [!NOTE]
   > 如果您在對話方塊的左窗格中看不到 [Visual Basic]，則需要安裝 **.NET 桌面開發** Visual Studio「工作負載」。 Visual Studio 會使用工作負載安裝，只安裝您執行之開發類型所需的元件。 安裝新工作負載的簡單方式是選擇 [新增專案] 對話方塊左下角的 [開啟 Visual Studio 安裝程式] 連結。 Visual Studio Installer 啟動之後，請選擇 [.NET 桌面開發] 工作負載，然後選取 [修改] 按鈕。
   >
   > ![開啟 Visual Studio 安裝程式連結](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. 從**方案總管**中**方案 ' QuickSolution '** 的滑鼠右鍵或操作功能表，選擇 [**加入**>**新增專案**]。

   隨即開啟一個對話方塊，表示要 [新增專案]。

1. 在頂端的搜尋方塊中輸入文字**空白**，然後在 [語言] 底下選取 [Visual Basic]。

1. 選取 [空白專案 (.NET Framework)] 範本，然後選擇 [下一步]。

1. 將專案命名為 **QuickDate**，然後選擇 [建立]。

   名為 QuickDate 的專案隨即出現在 [方案總管] 中該方案的下方。 它目前包含稱為 *App.config* 的單一檔案。

   > [!NOTE]
   > 如果您未看到 [空白專案 (.NET Framework)] 範本，您必須安裝 [.NET 桌面開發] 的 Visual Studio「工作負載」。 Visual Studio 會使用工作負載安裝，只安裝您執行之開發類型所需的元件。 建立新專案時安裝新工作負載的簡單方式，就是在顯示 [找不到您要尋找的項目嗎？] 文字底下，選擇 [安裝更多工具與功能] 連結。 Visual Studio Installer 啟動之後，請選擇 [.NET 桌面開發] 工作負載，然後選取 [修改] 按鈕。
   >
   > ![Visual Studio 2019 中的安裝程式連結](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>將項目新增至專案

我們有空白專案。 請新增程式碼檔案。

1. 在 [方案總管] 中，從 [QuickDate] 的右鍵功能表或操作功能表中，選擇 [新增] > [新增項目]。

   [新增項目] 對話方塊隨即開啟。

1. 展開 [一般項目]，然後選擇 [程式碼]。 在中間窗格中，選擇 [類別] 項目範本。 將類別命名為 **Calendar**，然後選擇 [新增] 按鈕。

   名為 *Calendar.vb* 的檔案會新增至專案。 尾端的 *.vb* 是提供給 Visual Basic 程式碼檔案的副檔名。 此檔案會出現在 [方案總管] 的視覺效果專案階層中，並在編輯器中開啟其內容。

1. 以下列程式碼取代 *Calendar.vb* 檔案的內容：

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   `Calendar` 類別包含單一函式 `GetCurrentDate`，它會傳回目前日期。

1. 在 [方案總管] 中按兩下 [我的專案]，開啟專案屬性。 在 [應用程式] 索引標籤上，將 [應用程式類型] 變更為 [類別庫]。 需要執行此步驟，才能成功建置專案。

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [QuickDate]，然後選擇 [建置] 來建置專案。 您應該會在 [輸出] 視窗看到成功建置訊息。

## <a name="add-a-second-project"></a>新增第二個專案

解決方案通常會包含多個專案，而且這些專案通常會彼此參考。 解決方案中有些專案可能是類別庫、有些是可執行的應用程式，有些可能是單元測試專案或網站。

請將單元測試專案新增至解決方案。 現在我們先從專案範本開始，因此不需要將額外程式碼檔案新增至專案。

1. 在 [方案總管] 中，從 [方案 'QuickSolution'] 的右鍵功能表或操作功能表中，選擇 [新增] > [新增專案]。

::: moniker range="Vs-2017"

2. 在左窗格中，展開 [Visual Basic]，然後選擇 [測試] 類別。 在中間窗格中，選擇 [單元測試專案 (.NET Framework)] 專案範本。 將專案命名為 **QuickTest**，然後選擇 [確定]。

   第二個專案會新增至**方案總管**，並在編輯器中開啟名為 *UnitTest1.vb* 的檔案。

   ![包含兩個專案的 Visual Studio 方案總管](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. 在 [新增專案] 對話方塊的頂端搜尋方塊中輸入文字**單元測試**，然後在 [語言] 底下選取 [Visual Basic]。

3. 選擇 [單元測試專案 (.NET Framework)] 專案範本，然後選擇 [下一步]。

4. 將專案命名為 **QuickTest**，然後選擇 [建立]。

   第二個專案會新增至**方案總管**，並在編輯器中開啟名為 *UnitTest1.vb* 的檔案。

::: moniker-end

## <a name="add-a-project-reference"></a>新增專案參考

我們將使用新的單元測試專案來測試 **QuickDate** 專案中的方法，因此必須新增該專案的參考。 這會建立兩個專案之間的「組建相依性」，表示在建置方案時會先建置 **QuickDate** 再建置 **QuickTest**。

1. 選擇 [QuickTest] 專案中的 [參考] 節點，然後從右鍵功能表或操作功能表中選擇 [新增參考]。

   ![新增參考功能表](media/tutorial-projects-add-reference-vb.png)

   [參考管理員] 對話方塊隨即開啟。

1. 在左窗格中，展開 [專案]，然後選擇 [解決方案]。 在中間窗格中，選擇 [QuickDate] 旁邊的核取方塊，然後選擇 [確定] 按鈕。

   隨即新增 **QuickDate** 專案的參考。

## <a name="add-test-code"></a>新增測試程式碼

1. 我們現在會將測試程式碼新增至 Visual Basic 程式碼檔案。 以下列程式碼取代 *UnitTest1.vb* 檔案的內容。

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   您會在一些程式碼下方看到紅色曲線。 我們將修正這個錯誤，方法是將測試專案設為 **QuickDate** 專案的 [friend 組件](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies)。

1. 回到 **QuickDate** 專案，開啟尚未開啟的 *Calendar.vb* 檔案，並新增下列 [Imports 陳述式](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)和 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性，以解決測試專案中的錯誤。

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   程式碼檔應該如下：

   ![Visual Basic 程式碼](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>專案屬性

*Calendar.vb* 檔案中包含 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 屬性的行會參考 **QuickTest** 專案的組件名稱 (檔案名稱)。 組件名稱不一定會與專案名稱相同。 若要尋找專案的組件名稱，請開啟專案屬性。

1. 在方案總管中，選取 **QuickTest** 專案。 從右鍵功能表或操作功能表中，選擇 [屬性]，或只按 **Alt**+**Enter** 鍵。 (您也可以在 [方案總管] 中按兩下 [我的專案]。)

   專案的*屬性頁*會在 [**應用程式**] 索引標籤上開啟。屬性頁包含專案的各種設定。 請注意， **QuickTest**專案的元件名稱實際上是「QuickTest」。 如果您想要變更它，則這是進行變更的位置。 然後，當您建置測試專案時，所產生二進位檔案的名稱會從 *QuickTest.dll* 變更為您選擇的任何名稱。

   ![專案屬性](../media/tutorial-projects-properties.png)

1. 探索專案屬性頁的一些其他索引標籤 (例如 [編譯] 和 [設定])。 不同專案類型的這些索引標籤不同。

## <a name="optional-run-the-test"></a>(選擇性) 執行測試

如果您想要確認單元測試是否正常運作，請從功能表列中選擇 [測試] > [執行] > [所有測試]。 稱為 [測試總管] 的視窗隨即開啟，而且您應該會看到 **TestGetCurrentDate** 測試通過。

![Visual Studio 中顯示已通過測試的 [測試總管]](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> 如果 [測試總管] 未自動開啟，請從功能表列選擇 [測試] > [Windows] > [測試總管] 開啟它。

## <a name="next-steps"></a>後續步驟

如果您想要進一步探索 Visual Studio，請考慮遵循其中一個 [Visual Basic 教學課程](index.yml)，來建立應用程式。

## <a name="see-also"></a>請參閱

- [建立專案和解決方案](../../ide/creating-solutions-and-projects.md)
- [管理專案及解決方案屬性](../../ide/managing-project-and-solution-properties.md)
- [管理專案中的參考](../../ide/managing-references-in-a-project.md)
- [在 Visual Studio 中不使用專案或方案來開發程式碼](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE 概觀](../../get-started/visual-studio-ide.md)
