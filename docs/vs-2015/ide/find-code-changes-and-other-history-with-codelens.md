---
title: 尋找 CodeLens 的程式碼變更和其他記錄 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f697d7b4-704e-4cac-b13a-bc57d2ff8318
caps.latest.revision: 134
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8876a0a3c2b978443ee4bc74097dbc9fdd410b8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656008"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>尋找 CodeLens 的程式碼變更和其他記錄
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您了解程式碼發生什麼事時，也能保持專注在工作上，且無須離開編輯器。 尋找程式碼參考、程式碼的變更、已連結的 Bug、工作項目、程式碼檢閱和單元測試。

> [!NOTE]
> CodeLens 僅適用於 Visual Studio Enterprise 與 Visual Studio Professional 版。 其不適用於 Visual Studio Community 版。

 請參閱在解決方案中的何處使用程式碼的各個部分，及使用方式：

 ![[程式碼編輯器] 中的 CodeLens 指標](../ide/media/codelensoverview.png "CodeLensOverview")

 連絡您的小組有關程式碼的變更，而無須離開編輯器：

 ![CodeLens &#45; 與您的小組聯繫](../ide/media/codelensovervew2.png "CodeLensOvervew2")

 若要選擇欲查看或開啟/關閉 CodeLens 的指標，請移至 [工具] ****、[選項] ****、[文字編輯器] ****、[所有語言] ****、[CodeLens] ****。

## <a name="find-references-to-your-code"></a><a name="FindReferences"></a> 尋找您程式碼的參考
 您將需要：

- Visual Studio Enterprise 或 Visual Studio Professional

- Visual C# .NET 或 Visual Basic .NET 程式碼

  請選擇 [參考] **** 指標 (**[Alt+2]**)。 如果您看到 [0 個參考] ****，代表您沒有來自 Visual C# 或 Visual Basic 程式碼的參考。 這不包含來自其他項目的參考，例如 XAML 和 ASPX 檔案。

  ![CodeLens &#45; 選擇參考指標](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")

  若要檢視參考程式碼，請將滑鼠移至該參考上方。

  ![CodeLens &#45; 查看參考](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")

  若要開啟包含參考的檔案，請按兩下參考。

  若要查看此程式碼與其參考之間的關聯性，請[建立 Code Map](../modeling/map-dependencies-across-your-solutions.md)，並選擇 Code Map 捷徑功能表的 [顯示所有參考]**** 。

  ![CodeLens &#45; code map 上的參考](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")

## <a name="find-your-codes-history-and-linked-items"></a><a name="FindCodeHistory"></a> 尋找您程式碼的記錄和連結的項目
 檢閱您的程式碼記錄，以了解程式碼發生了什麼事。 或者，請先檢閱變更內容，再將其合併到您的程式碼中，如此可更了解其他分支中的變更可能會如何影響您的程式碼。

 您將需要：

- Visual Studio Enterprise 或 Visual Studio Professional

- Team Foundation Server 2013 或更新版本、Visual Studio Team Services 或 Git

- [Lync 2010 或更新版本或是商務用 Skype](https://technet.microsoft.com/lync)，以從程式碼編輯器連絡您的小組

  針對 Team Foundation 版本控制 (TFVC) 或 Git 儲存的 Visual C# .NET 或 Visual Basic .NET，您將在類別與方法層級取得 CodeLens 詳細資訊 (*程式碼項目層級* 指標)。 如果您的 Git 儲存機制裝載在 TfGit 中，您也會取得 TFS 工作項目的連結。

  ![程式碼元素&#45;層級指標](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")

  對於可以在 Visual Studio 編輯器中開啟的所有其他類型的檔案，將可於視窗的下方取得整個檔案的 CodeLens 詳細資料 (*檔案層級* 指標)。

  ![檔&#45;層級 CodeLens 指示器](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")

  若要使用鍵盤來選取指標，請按住 **ALT** 鍵以顯示相關數位鍵。

  ![按下 ALT 鍵以查看鍵盤存取號碼](../ide/media/codelensaltkeyindicators.png ">codelensaltkeyindicators")

### <a name="find-changes-in-your-code"></a>尋找您程式碼中的變更
 在程式碼項目層級指標中，找出誰變更了您的 C# 或 Visual Basic 程式碼，以及他們做的變更。 當您使用 Team Foundation Server 或 Visual Studio Team Services 中的 Team Foundation 版本控制 (TFVC) 時，這就是您所看到的樣子。

 ![CodeLens：取得 TFVC 中的程式碼變更記錄](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")

 預設的時間週期為 12 個月。 如果程式碼儲存在 Team Foundation Server 中，您就可以執行 [TFSConfig 命令](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62) 與 [CodeIndex 命令](../ide/codeindex-command.md) 和 **/indexHistoryPeriod** 旗標，變更這項限制。

 若要查看所有變更的詳細記錄，包括一年多前的記錄，請選擇 [顯示所有檔案變更] ****。

 ![顯示所有程式碼變更](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")

 這會開啟變更集的 [記錄] 視窗。

 ![所有程式碼變更的歷程記錄視窗](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")

 當您的檔案放在 Git 儲存機制中，而您選擇程式碼項目層級變更指標時，這就是您所看到的。

 ![CodeLens：取得 Git 中的程式碼變更記錄](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")

 在視窗下方的檔案層級指標中，尋找整個檔案 (除了 C# 和 Visual Basic 檔案) 的變更。

 ![CodeLens：取得程式碼檔案詳細資料](../ide/media/codelensfilelevel.png "CodeLensFileLevel")

 若要取得變更的更多詳細資料，請在該項目上按一下滑鼠右鍵。 視您使用的 TFVC 或 Git 之不同，您會取得一系列的選項以比較檔案的版本、檢視詳細資料及追蹤變更集，取得檔案所選的版本，並以對作者發送電子郵件表示出現該變更。 部分詳細資料會出現在 Team Explorer 中。

 您也可以看到在這段時間裡是誰變更了您的程式碼。 這可協助您找出小組變更的模式，並評估其影響。

 ![CodeLens：以圖形方式檢視程式碼變更記錄](../ide/media/codelens.png "CodeLens")

#### <a name="find-changes-in-your-current-branch"></a>尋找您目前分支中的變更
 假設您的小組有多個分支 (主要分支和子系開發) 可減少中斷穩定程式碼的風險：

 ![CodeLens：了解您的程式碼於何時分支](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")

 找出在主要分支中，有多少人對您的程式碼進行了多少變更 (**Alt + 6**)：

 ![CodeLens：了解您的分支中有多少變更](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")

#### <a name="find-when-your-code-was-branched"></a>尋找何時將您的程式碼進行分支處理
 在子分支中移至您的程式碼 (例如，這裡的 Dev 分支)。 選擇變更指標 (**Alt + 6**)：

 ![CodeLens：了解您的程式碼於何時分支](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")

#### <a name="find-incoming-changes-from-other-branches"></a>尋找其他分支傳入的變更
 ![CodeLens：尋找其他分支的程式碼變更](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")

 …像此處 Dev 分支中的這個 Bug 修正：

 ![CodeLens：移入其他分支中的變更](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")

 您可以檢閱這項變更，而不離開目前分支 (Main)：

 ![CodeLens：查看從其他分支連入的變更](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")

#### <a name="find-when-changes-got-merged"></a>尋找何時合併變更
 因此，您可以看到您分支中所含的變更：

 ![CodeLens &#45; 在分支之間合併變更](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")

 例如，您在 Main 分支中的程式碼現在具有來自 Dev 分支的 Bug 修正：

 ![CodeLens &#45; 在分支之間合併的變更](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")

#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>比較傳入變更與您的本機版本 (Shift + F10)
 ![CodeLens：比較連入變更與本機變更](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")

 您也可以連按兩下變更集。

#### <a name="what-do-the-icons-mean"></a>圖示的意義為何？

|**圖示**|**變更的出處為何？**|
|--------------|-----------------------------------------|
|![CodeLens - 從目前分支變更圖示](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|目前分支|
|![CodeLens &#45; 從父分支變更圖示](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|父分支|
|![CodeLens - 從子分支變更圖示](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|子分支|
|![CodeLens &#45; 從對等分支變更圖示](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|對等分支|
|![CodeLens &#45; 從分支進一步變更圖示](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|比父分支、子分支或對等分支更遠的分支|
|![CodeLens - 從父分支合併圖示](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|從父分支到子分支的合併|
|![CodeLens - 從子分支合併圖示](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|從子分支到父分支的合併|
|![CodeLens - 從非相關的分支合併圖示](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|從不相關分支的合併 (無基礎的合併)|

### <a name="find-linked-work-items"></a>尋找已連結的工作項目
 ![CodeLens &#45; 尋找特定程式碼的工作專案](../ide/media/codelensworkitems.png "CodeLensWorkItems")

### <a name="find-linked-code-reviews"></a>尋找已連結的程式碼檢閱
 ![CodeLens &#45; 查看程式碼審核要求](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")

### <a name="find-linked-bugs"></a>尋找已連結的錯誤 (bug)
 ![CodeLens &#45; 尋找連結至變更集的 bug](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")

### <a name="contact-the-owner-of-an-item"></a>連絡項目擁有者
 ![連絡項目擁有者](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")

 開啟項目的捷徑功能表，查看連絡人選項。 如果您安裝了 Lync 或商務用 Skype，您會看到下列選項：

 ![項目的連絡選項](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")

## <a name="find-unit-tests-for-your-code"></a><a name="FindRunUnitTests"></a> 尋找您程式碼的單元測試
 深入了解因您的程式碼而存在的單元測試，而不需要開啟 [測試總管]。 您將需要：

- Visual Studio Enterprise 或 Visual Studio Professional

- Visual C# .NET 或 Visual Basic .NET 程式碼

- [單元測試專案](../test/unit-test-your-code.md) ，其中具有應用程式程式碼的單元測試

1. 移至包含單元測試的應用程式程式碼。

2. 檢閱該程式碼的測試 (**Alt + 3**)。

     ![CodeLens &#45; 選擇程式碼編輯器中的測試狀態](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")

3. 如果您看到警告圖示 ![CodeLens &#45; 單元測試尚未執行警告](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon")，請執行測試。

     ![CodeLens &#45; 查看尚未執行的單元測試](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")

4. 若要檢閱測試的定義，請按兩下 CodeLens 指示器視窗中的測試項目，在編輯器中開啟程式碼檔案。

     ![CodeLens &#45; 移至單元測試定義](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")

5. 檢閱測試結果。 選擇測試狀態指標 (![CodeLens &#45; 單元測試失敗圖示](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") 或 ![codelens &#45; 單元測試已通過圖示](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")) ，或按 **Alt + 1**。

     ![CodeLens &#45; 請參閱單元測試結果](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")

6. 若要查看變更過此測試的人數、變更過此測試的人士，或是此測試經變更的次數，請 [尋找您程式碼的記錄和連結的項目](#FindCodeHistory)。

## <a name="q--a"></a><a name="QA"></a> 問 & A

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a><a name="ChangeOrTurnOff"></a> 問：如何關閉或開啟 CodeLens？ 又如何選擇要查看的指標？
 **答：**  除了參考指標之外，您可以關閉或開啟各個指標。 請依序移至 [工具] ****、[選項] ****、[文字編輯器] ****、[所有語言] **** 和 [CodeLens] ****。

 開啟指標之後，您也可以從指標開啟 CodeLens 選項。

 ![CodeLens &#45; 關閉或開啟指示器](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")

 請使用 [編輯器] 視窗底部的＞形箭號圖示，開啟和關閉 CodeLens 檔案層級指標。

 ![開啟和關閉檔案&#45;層級指示器](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")

### <a name="q-where-is-codelens"></a><a name="NoIndicators"></a> 問：CodeLens 在哪裡？
 **答：** CodeLens 顯示在方法、類別、索引子和屬性層級的 Visual C# .NET 和 Visual Basic .NET 程式碼中。 CodeLens 會顯示在所有其他類型檔案的檔案層級。

- 請確定 CodeLens 已開啟。 請依序移至 [工具] ****、[選項] ****、[文字編輯器] ****、[所有語言] **** 和 [CodeLens] ****。

- 如果您的程式碼儲存在 TFS 中，請務必使用 [CodeIndex 命令](../ide/codeindex-command.md) 與 [TFS 組態命令](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62)，確定程式碼索引已開啟。

- 唯有當工作項目連結程式碼，且您擁有開啟連結工作項目的權限時，才會出現與 TFS 相關的指標。 [確認您擁有小組成員權限。](/azure/devops/organizations/security/view-permissions)

- 應用程式程式碼沒有單元測試時，不會出現測試狀態指標。 測試狀態指標會自動出現在測試專案中。 如果您知道應用程式程式碼有單元測試，但是並未出現測試指標，請嘗試建置方案 ([**Ctrl + Shift + B**])。

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>問：為什麼看不到認可的工作項目詳細資料？
 **答：** 因為 CodeLens 在 TFS 中找不到工作項目，所以可能會發生這種情況。 請確認您已連接至具有那些工作項目的 Team 專案，以及您具有查看那些工作項目的權限。 如果認可描述具有 TFS 中工作項目 ID 的不正確資訊，則也可能會發生這種情況。

### <a name="q-why-dont-i-see-the-lync-or-skype-indicators"></a><a name="NoLync"></a> 問：為什麼看不到 Lync 或 Skype 指標？
 **答：** 如果您未登入 Lync 或商務用 Skype、未安裝其中之一，或沒有支援的組態，則不會出現 Lync 或 Skype 指標。 不過您仍然可以傳送郵件：

 ![CodeLens &#45; Contact mail 的變更集擁有者](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")

 **支援哪些 Lync 和 Skype 組態？**

- 商務用 Skype (32 位元或 64 位元)

- Lync 2010 或更新版本搭配 (32 位元或 64 位元)，但不是 Lync Basic 2013 的 Windows 8.1

  CodeLens 不支援安裝不同版本的 Lync 或 Skype。 它們可能尚未對所有 Visual Studio 當地語系化版本完成當地語系化。

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>問：如何變更 CodeLens 的字型和色彩？
 **答：** 移至 [ **工具**]、[ **選項**]、[ **環境**]、[ **字型和色彩**]。

 ![CodeLens &#45; 變更字型和色彩設定](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")

 使用鍵盤：

1. 按 **Alt + T + O** 開啟 [ **選項** ] 方塊。

2. 按 **向上鍵** 或 **向下鍵** 移至 [ **環境** ] 節點，然後按 **向左鍵** 展開節點。

3. 按 **向下鍵** 移至 [ **字型和色彩**]。

4. 按 **tab** 鍵移至 [ **顯示設定** ] 清單，然後按 **向下鍵** 選取 [ **CodeLens**]。

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>問：我可以移動 CodeLens 平視顯示窗嗎？
 **答：** 是，請選擇 ![CodeLens &#45; dock 作為視窗](../ide/media/codelensdockwindow.png "CodeLensDockWindow") ，將 CodeLens 固定為視窗。

 ![停駐 CodeLens 指標視窗](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")

 ![停駐的 CodeLens 參考視窗](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")

### <a name="q-how-do-i-refresh-the-indicators"></a>問：如何重新整理指標？
 **答：** 這取決於指標：

- **參考**：程式碼變更時，此指標會自動更新。 如果您將此指標固定為獨立視窗，請在此處手動重新整理指標：

     ![CodeLens &#45; 停駐為視窗](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")

- **小組**：請在此處手動重新整理指標：

     ![CodeLens &#45; 重新整理指示器](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")

- **測試**：請 [尋找您程式碼的單元測試](#FindRunUnitTests) ，以重新整理此指標。

### <a name="q-whats-local-version"></a><a name="LocalVersion"></a> 問：什麼是「本機版本」？
 **答：** [ **本機版本** ] 箭頭指向這個檔案的本機版本的最新變更集。 當伺服器有更新的變更集時，它們會顯示在 [ **本機版本** ] 箭頭上方或下方 (根據變更集的排列順序而定)。

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>問：我是否可以管理 CodeLens 處理程式碼的方式，以顯示記錄和連結項目？
 **答：** 可以，如果您的程式碼儲存於 TFS，請使用 [CodeIndex 命令](../ide/codeindex-command.md) 與 [TFS 組態命令](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62)。
