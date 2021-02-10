---
title: 尋找 CodeLens 的程式碼變更和其他記錄
description: 深入瞭解 CodeLens，以及如何使用它來探索程式碼的歷程記錄，而不需要離開編輯器。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59df5a4b0b0c873de69c5e574ad5c2cccbc43567
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945873"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>尋找 CodeLens 的程式碼變更和其他記錄

CodeLens 可讓您在了解程式碼發生什麼事時，也能保持專注在工作上，且無須離開編輯器。 您可以尋找程式碼片段的參考、程式碼的變更、已連結的錯誤、工作項目、程式碼檢閱和單元測試。

::: moniker range=">=vs-2019"

> [!NOTE]
> CodeLens 可在 Visual Studio Community 版本中使用，但在此版本中無法使用 *原始檔控制* 指標。

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> CodeLens 只能在 Visual Studio Enterprise 與 Professional 版中使用。 其不適用於 Visual Studio Community 版。

::: moniker-end

請參閱在解決方案中的何處使用程式碼的各個部分，及使用方式：

![[程式碼編輯器] 中的 CodeLens 指標](../ide/media/codelens-overview.png)

連絡您的小組有關程式碼的變更，而無須離開編輯器：

![CodeLens - 連絡您的小組](../ide/media/codelens-contact-info.png)

若要選擇您想要查看的指標，或關閉或開啟 codelens，請移至 [**工具**  >  **選項**  >  **文字編輯器**  >  **所有語言**]  >  **codelens**。

## <a name="find-references-to-your-code"></a>尋找您程式碼的參考

您可以在 C# 或 Visual Basic 程式碼中找到參考。

1. 選擇 **參考** 指標或按 **Alt**+**2**。

   ![CodeLens 參考](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > 如果指標顯示 **0 個參考**，代表您沒有來自 C# 或 Visual Basic 程式碼的參考。 不過，其他項目 (例如 *.xaml* 和 *.aspx* 檔案) 可能會有參考。

2. 若要檢視參考程式碼，請將滑鼠移至清單中的該參考上方。

   ![CodeLens - 查看參考](../ide/media/codelens-peek-reference.png)

3. 若要開啟包含參考的檔案，請按兩下參考。

### <a name="code-maps"></a>Code Map

若要查看此程式碼與其參考之間的關聯性，請[建立 Code Map](../modeling/map-dependencies-across-your-solutions.md)。 在 Code Map 捷徑功能表中，選取 [顯示所有參考]。

![CodeLens - Code Map 上的參考](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>尋找您程式碼中的變更

請檢查您的程式碼記錄，以了解程式碼發生了什麼事。 或者，請先檢閱變更內容，再將其合併到您的程式碼中，如此可更了解其他分支中的變更可能會如何影響您的程式碼。

您需要：

- Visual Studio Enterprise 或 Professional 版本

- Azure DevOps Services、Team Foundation Server 2013 或更新版本，或 Git

- [商務用 Skype](/skypeforbusiness/)，以從程式碼編輯器與您的小組連絡

針對 Team Foundation 版本控制 (TFVC) 或 Git 儲存的 C# 或 Visual Basic 程式碼，您將在類別與方法層級取得 CodeLens 詳細資訊 (「程式碼項目層級」指標)。 如果您的 Git 儲存機制裝載在 TfGit 中，您也會取得 TFS 工作項目的連結。

![程式碼項目層級指標](../ide/media/codelens-element-level-indicators.png)

對於 *.cs* 或 *.vb* 之外的檔案類型，您可於視窗的下方取得整個檔案的 CodeLens 詳細資料 (「檔案層級」指標)。

![檔案層級的 CodeLens 指標](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>程式碼項目層級指標

程式碼項目層級指標可讓您查看哪些人變更了您的程式碼，以及他們進行了哪些變更。 程式碼項目層級指標適用於 C# 和 Visual Basic 程式碼。

當您使用 Team Foundation Server 或 Azure DevOps Services 中的 Team Foundation 版本控制 (TFVC) 時，您會看到：

![CodeLens：取得 TFVC 中的程式碼變更記錄](../ide/media/codelens-code-changes.png)

預設的時間週期為 12 個月。 如果程式碼儲存在 Team Foundation Server 中，您就可以執行 [TFSConfig 命令](/azure/devops/server/command-line/tfsconfig-cmd) 與 [CodeIndex 命令](../ide/codeindex-command.md) 和 **/indexHistoryPeriod** 旗標，變更此時間週期。

若要查看所有變更的詳細記錄，包括一年以上的變更，請選擇 [ **顯示所有檔案變更**]：

![顯示所有程式碼變更](../ide/media/codelens-show-all-file-changes.png)

[記錄] 視窗隨即開啟：

![所有程式碼變更的歷程記錄視窗](../ide/media/codelenscodechangeshistory.png)

當您的檔案放在 Git 存放庫中，而您選擇程式碼項目層級變更指標時，這就是您所看到的樣子：

![CodeLens：取得 Git 中的程式碼變更記錄](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>檔案層級指標

在視窗下方的檔案層級指標中，尋找整個檔案的變更：

![CodeLens：取得程式碼檔案詳細資料](../ide/media/codelens-file-level.png)

> [!NOTE]
> 檔案層級指標適用於 C# 和 Visual Basic 檔案。

若要取得變更的更多詳細資料，請在該項目上按一下滑鼠右鍵。 視您使用的 TFVC 或 Git 之不同，有一些選項可用來比較檔案的版本、檢視詳細資料及追蹤變更集，取得檔案所選的版本，並以對作者發送電子郵件表示出現該變更。 其中有些詳細資料會出現在 **Team Explorer** 中。

您也可以看到在這段時間裡是誰變更了您的程式碼。 這可協助您找出小組變更的模式，並評估其影響。

![CodeLens：以圖形方式檢視程式碼變更記錄](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>尋找您目前分支中的變更

您的小組可能有多個分支 (例如，主要分支和子系開發分支) 可減少中斷穩定程式碼的風險。

![CodeLens：尋找您最新分支中的變更](../ide/media/codelensfirstbranchconceptual.png)

您可以按下 **Alt** 6，找出有多少人變更您的程式碼，以及主要分支中所做的變更數目 + ****：

![CodeLens：了解您的分支中有多少變更](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>尋找何時將您的程式碼進行分支處理

若要尋找何時將您的程式碼進行分支處理，請巡覽至您在子分支中的程式碼。 然後，選取 **變更** 指標或按 **Alt**+**6**：

![CodeLens：了解您的程式碼於何時分支](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>尋找其他分支傳入的變更

![CodeLens：尋找其他分支的程式碼變更](../ide/media/codelensbranchchangecheckinconceptual.png)

您可以檢視傳入的變更。 在下列螢幕擷取畫面中，已在 "Dev" 分支中進行 Bug 修正：

![CodeLens：移入其他分支中的變更](../ide/media/codelens-branch-changes-dev.png)

您可以檢閱這項變更，而不離開目前分支 ("Main")：

![CodeLens：查看從其他分支連入的變更](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>尋找何時合併變更

您可以看到何時合併變更，因此您可以判斷您的分支中包含哪些變更：

![CodeLens-尋找變更何時合併](../ide/media/codelensbranchmergedconceptual.png)

例如，您在 Main 分支中的程式碼現在具有來自 "Dev" 分支的 Bug 修正：

![CodeLens - 分支之間合併的變更](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>比較傳入變更與您的本機版本

按 **Shift** + **F10**，或按兩下變更集，以將內送變更與您的本機版本進行比較。

![CodeLens：比較連入變更與本機變更](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>分支圖示

**分支** 資料行中的圖示告訴您該分支與您正在處理的分支的相關性。

|**圖示**|**變更來源：**|
|--------------| - |
|![CodeLens - 從目前分支變更圖示](../ide/media/codelensbranchcurrenticon.png)|目前分支|
|![CodeLens： 從父分支變更圖示](../ide/media/codelensbranchparenticon.png)|父分支|
|![CodeLens - 從子分支變更圖示](../ide/media/codelensbranchchildicon.png)|子分支|
|![CodeLens：從對等分支變更圖示](../ide/media/codelensbranchpeericon.png)|對等分支|
|![CodeLens：從遠離的分支變更圖示](../ide/media/codelensbranchfurtherawayicon.png)|比父分支、子分支或對等分支更遠的分支|
|![CodeLens - 從父分支合併圖示](../ide/media/codelensbranchmergefromparenticon.png)|從父分支到子分支的合併|
|![CodeLens - 從子分支合併圖示](../ide/media/codelensbranchmergefromchildicon.png)|從子分支到父分支的合併|
|![CodeLens - 從非相關的分支合併圖示](../ide/media/codelensbranchmergefromunrelatedicon.png)|從不相關分支的合併 (無基礎的合併)|

## <a name="linked-work-items"></a>連結的工作項目

選取 **工作項目** 指標，或按 **Alt**+**8**，尋找連結的工作項目。

![CodeLens - 尋找特定程式碼的工作項目](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>已連結的程式碼檢閱

選取 **檢閱** 指標，尋找已連結的程式碼檢閱。 若要使用鍵盤，請按住 **Alt** 鍵，然後按 **向左鍵** 或 **向右鍵** 以巡覽指標選項。

![CodeLens - 檢閱程式碼檢閱要求](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>已連結的錯誤

選取 **錯誤** 指標，或按 **Alt**+**7**，尋找已連結的錯誤。

![CodeLens - 尋找已連結至變更集的 Bug](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>連絡項目擁有者

選取 **作者** 指標或按 **Alt**+**5**，尋找項目的作者。

![連絡項目擁有者](../ide/media/codelens-contact-item-owner.png)

開啟項目的捷徑功能表，查看連絡人選項。 如果您安裝了 Lync 或商務用 Skype，您會看到下列選項：

![項目的連絡選項](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>相關聯的單元測試

您可以了解因您的 C# 或 Visual Basic 程式碼而存在的單元測試，而不需要開啟 [測試總管]。

1. 移至包含相關聯[單元測試程式碼](../test/unit-test-your-code.md)的應用程式程式碼。

2. 若您尚未這麼做，請建置應用程式以載入 CodeLens 測試指標。

3. 按下 **Alt** 3 來檢查程式碼的測試 + ****。

     ![CodeLens - 在 [程式碼編輯器] 中選擇測試狀態](../ide/media/codelens-choose-test-indicator.png)

4. 如果您看到警告圖示 ![警告圖示](../ide/media/codelenstestwarningicon.png)，表示測試尚未執行，因此請執行它們。

     ![CodeLens - 檢視尚未執行的單元測試](../ide/media/codelens-tests-not-yet-run.png)

5. 若要檢閱測試的定義，請按兩下 CodeLens 指示器視窗中的測試項目，在編輯器中開啟程式碼檔案。

     ![CodeLens - 移至單元測試定義](../ide/media/codelens-unit-test-definition.png)

6. 若要檢查測試的結果，請選擇測試狀態指標 (![ 測試失敗圖示 ](../ide/media/codelenstestfailedicon.png) 或 ![ 測試通過圖示 ](../ide/media/codelenstestpassedicon.png)) 或按 **Alt** + **1**。

     ![CodeLens - 查看單元測試結果](../ide/media/codelens-unit-test-result.png)

7. 若要查看有多少人變更此測試、誰變更此測試，或是對此測試做了多少變更，請 [尋找程式碼的歷程記錄](#find-changes-in-your-code) 和連結的專案。

## <a name="keyboard-shortcuts"></a>鍵盤快速鍵

若要使用鍵盤來選取指標，請按住 **Alt** 鍵來顯示相關數字鍵，然後按下與您要選取的指標對應的數字。

![鍵盤存取數字](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> 若要選取 **檢閱** 指標，請按住 **Alt**，同時使用左移鍵和右移鍵來巡覽。

## <a name="q--a"></a>問答集

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>問：如何? 關閉或開啟 CodeLens，或選擇要查看哪些指標？

**答：**  除了參考指標之外，您可以關閉或開啟各個指標。 移至 **工具**  >  **選項**  >  **文字編輯器**  >  **所有語言**  >  **CodeLens**。

開啟指標之後，您也可以從指標開啟 CodeLens 選項。

![CodeLens - 開啟或關閉指標](../ide/media/codelensturnoffonindicatorsfromcode.png)

請使用 [編輯器] 視窗底部的＞形箭號圖示，開啟和關閉 CodeLens 檔案層級指標。

![開啟及關閉檔案層級指標](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>問：CodeLens 在哪裡？

**答：** CodeLens 顯示在方法、類別、索引子和屬性層級的 C# 和 Visual Basic 程式碼中。 CodeLens 會顯示在所有其他類型檔案的檔案層級。

- 請確定 CodeLens 已開啟。 移至 **工具**  >  **選項**  >  **文字編輯器**  >  **所有語言**  >  **CodeLens**。

- 如果您的程式碼儲存在 TFS 中，請務必使用 [CodeIndex 命令](../ide/codeindex-command.md) 與 [TFS 組態命令](/azure/devops/server/command-line/tfsconfig-cmd)，確定程式碼索引已開啟。

- 唯有當工作項目連結到程式碼，且您擁有開啟工作項目連結的權限時，才會出現與 DevOps 相關的指標。 確認您擁有 [小組成員許可權](/azure/devops/organizations/security/view-permissions?view=vsts&preserve-view=true)。

- 應用程式程式碼沒有單元測試時，不會出現測試狀態指標。 測試狀態指標會自動出現在測試專案中。 如果您知道您的應用程式程式碼有單元測試，但未出現測試指標，請嘗試建立解決方案 (**Ctrl** + **Shift** + **B**) 。

::: moniker range=">=vs-2019"

> [!TIP]
> CodeLens 可在 Visual Studio Community 版本中使用，但在此版本中無法使用 *原始檔控制* 指標。

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> 在 Visual Studio Community 版中無法使用 CodeLens。

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>問：為什麼看不到認可的工作項目詳細資料？

**答：** 發生這種情況的原因可能是 CodeLens 在 Azure Boards 或 TFS 中找不到工作項目。 請確認您已連線到具有那些工作項目的專案，而且您具有查看那些工作項目的權限。 如果認可描述具有 Azure Boards 或 TFS 中工作項目 ID 的錯誤資訊，工作項目詳細資料也可能不會顯示。

### <a name="q-why-dont-i-see-the-skype-indicators"></a>問：為何看不到 Skype 指標？

**答：** 如果您未登入商務用 Skype、未安裝該產品，或沒有支援的組態，則不會出現 Skype 指標。 不過，您仍然可以傳送郵件：

![CodeLens - 透過郵件連絡變更集擁有人](../ide/media/codelenscodesendmailchangesetnolync1.png)

**支援哪些 Skype 和 Lync 設定？**

- 商務用 Skype (32 位元或 64 位元)

- Lync 2010 或更新版本搭配 (32 位元或 64 位元)，但不是 Lync Basic 2013 的 Windows 8.1

CodeLens 不支援安裝不同版本的 Lync 或 Skype。 它們可能尚未對所有 Visual Studio 當地語系化版本完成當地語系化。

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>問：如何變更 CodeLens 的字型和色彩？

**答：** 移至 [工具] > [選項] > [環境] > [字型和色彩]。

![CodeLens - 變更字型和色彩設定](../ide/media/codelensoptionsfontscolorssettings.png)

使用鍵盤：

1. 按 **Alt** + **T** + **O** 以開啟 [**選項**] 對話方塊。

2. 按 **向上鍵** 或 **向下鍵** 移至 [ **環境** ] 節點，然後按 **向左鍵** 展開節點。

3. 按 **向下鍵** 移至 [ **字型和色彩**]。

4. 按 **Tab** 鍵移至 [顯示設定:] 清單，然後按 **向下鍵** 選取 [CodeLens]。

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>問：我可以移動 CodeLens 平視顯示窗嗎？

**答：** 可以，選擇![固定圖示](../ide/media/codelensdockwindow.png)可將 CodeLens 固定為視窗。

![CodeLens 指標視窗中的 [固定] 按鈕](../ide/media/codelensselectdockwindow.png)

![固定的 CodeLens 參考視窗](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>問：如何重新整理指標？

**答：** 這取決於指標：

- **參考**：程式碼變更時，此指標會自動更新。 如果 **參考** 指標固定為個別的視窗，請選取 [重新整理] 來重新整理指標：

   ![CodeLens 參考中的 [重新整理] 按鈕](../ide/media/codelensviewreferencesdocked.png)

- **小組**：從右鍵功能表選取 [重新整理 CodeLens 小組指標]，以重新整理這些指標：

   ![[重新整理 CodeLens 小組指標] 功能表項目](../ide/media/codelensrefreshindicatorsfromcode.png)

- **測試**：[尋找您程式碼的單元測試](#associated-unit-tests)，以重新整理 **測試** 指標。

### <a name="q-whats-local-version"></a>問：什麼是「本機版本」？

**答：**[本機版本] 箭頭指向這個檔案的本機版本的最新變更集。 當伺服器有更新的變更集時，它們會顯示在 [ **本機版本** ] 箭頭上方或下方 (根據變更集的排列順序而定)。

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>問：我是否可以管理 CodeLens 處理程式碼的方式，以顯示記錄和連結項目？

**答：** 是。 如果您的程式碼位於 TFS，請使用 [CodeIndex 命令](../ide/codeindex-command.md) 與 [TFS 組態命令](/azure/devops/server/command-line/tfsconfig-cmd)。

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>問：當我初次開啟解決方案時，我的 CodeLens 測試指標不再顯示在檔案中。 該如何加以載入？

**答：** 重建您的專案，讓 CodeLens 測試指標在您的檔案中載入。 為了提升效能，Visual Studio 不再於程式碼檔案載入時，為測試指標擷取來源資訊。 測試指標會在 **測試清單編輯器** 中，在建置後或在您按兩下以瀏覽到測試時載入。

## <a name="see-also"></a>另請參閱

- [程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md)
