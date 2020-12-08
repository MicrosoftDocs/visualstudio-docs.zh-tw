---
title: Debug Office 專案
description: 瞭解如何使用您用於其他 Visual Studio 專案的相同 Microsoft Visual Studio 工具來將 Office 專案進行 debug。
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ea4874effcba4ee948f921ae9bf91f145b661f4f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845631"
---
# <a name="debug-office-projects"></a>Debug Office 專案
  您可以使用與偵錯其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 專案時所使用的相同 Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 工具，來偵錯 Office 專案。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 偵錯工具功能（例如在 [ **區域變數** ] 視窗中插入中斷點和 view 變數的功能），也可以在您進行 Office 專案的偵錯工具時使用。 如需偵錯工具的詳細資訊 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，請參閱 [Visual Studio 中的 Debug](../debugger/debugger-feature-tour.md)。

> [!TIP]
> 為了簡化偵錯，請關閉任何開啟的 Office 應用程式執行個體，再進行建置和偵錯。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="start-and-stop-the-debugger"></a>啟動和停止偵錯工具
 您可以開始對 Office 專案進行偵錯工具，就像開始調試其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 專案一樣，例如，您可以按 **F5** 鍵。 當您開始進行 VSTO 增益集專案的偵錯工具時，會啟動目標 Office 應用程式的新進程，並載入 VSTO 增益集。

 當您開始偵錯文件層級專案時，會在新的 Word 或 Excel 處理序中開啟文件或活頁簿。

 當您停止偵錯工具時，偵錯工具會突然終止應用程式處理序；如果您將偵錯工具設定為中斷連結，則會中斷連結處理序。 在終止的 Office 應用程式處理序中開啟的所有其他文件也會關閉，而不會發出警告，並且任何未儲存的變更都將會遺失。 這可能包括偵錯工具執行時所開啟的所有文件或活頁簿。

 一般而言，在您停止偵錯工具之前，最好先中斷連結處理序，以便可以正常結束 Office 應用程式。 如果您在停止偵錯工具之後，還想繼續使用開啟的文件或工作表，也可以先中斷連結處理序。

 如果您想要偵錯 Word 的文件層級自訂，不斷重複停止偵錯工具並使 Word 突然關閉，可能會導致 Normal 範本損毀。 如果發生這種情況，您可以刪除損毀的 Normal 範本；下次開啟 Word 時，將會自動重新建立這個範本。 不過，儲存在 Normal 範本中的任何巨集都不會重新建立。

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>使用 Office 2013 或 Office 2016 偵錯 Office 2013 VSTO 增益集
 如果您使用 Visual Studio 2015，並同時安裝了兩個版本的 Office，Visual Studio 會啟動 Office 2016。 如果您是使用 Visual Studio 2013，Visual Studio 會啟動 Office 2013。

 如果您想要使用不同的 Office 版本 (2013 或 2016) 偵錯 VSTO 增益集，請開啟 [專案設計工具] ，並在 [偵錯]  索引標籤中，選擇 [啟動外部程式]  選項按鈕。 然後，瀏覽至適當 Office 應用程式可執行檔的位置。

## <a name="f10-and-f11-behavior"></a>F10 和 F11 的行為
 當您開始進行 Office 專案的偵錯工具時， **F10** 和 **F11** 的行為與您開始錯其他 Visual Basic 或 c # 專案的行為不同。 在 Visual Basic 或 C# 專案中，偵錯工具會在 main 函式上停止；在 Office 專案中，Visual Studio 並不能控制 Office 應用程式的 main 函式。 不過，在調試過程中， **F10** 和 **F11** 的功能與 Visual Basic 和 c # 專案中的函式相同。

## <a name="display-exceptions"></a>顯示例外狀況
 由於 Managed 程式碼與 Unmanaged 程式碼的互動方式，Visual Studio 不會顯示 Microsoft Office 應用程式所擲回的錯誤。 例如，如果在 Visual Studio 中使用 Office 開發工具所建立的 VSTO 增益集擲回例外狀況，Microsoft Office 應用程式會繼續執行，而不會顯示錯誤。 若要查看這些錯誤，請設定偵錯工具在發生 Common Language Runtime 例外狀況時中斷。 如需詳細資訊，請參閱 [使用偵錯工具管理例外](../debugger/managing-exceptions-with-the-debugger.md)狀況。

 如果您設定偵錯工具在發生 Common Language Runtime 例外狀況時中斷，所有例外狀況現在會中斷偵錯工具，包括您已處理的例外狀況，以及一些來自執行階段本身之前幾個可能發生的例外狀況，這些例外狀況可能與專案無關。 每個專案中都會出現歸因於找不到 msosec 的錯誤，不過您可以放心地加以忽略。 這些 msosec 例外狀況不會影響您的方案。

 您也可以在方法前後使用 **Try...Catch** 陳述式，以便攔截例外狀況。

 根據預設，Visual Studio 亦不顯示 Office 專案的 Just-In-Time 偵錯錯誤，但是您可以啟用這項功能，以便查看所引發的錯誤。 如需詳細資訊，請參閱 Visual Studio 中的 [即時調試](../debugger/just-in-time-debugging-in-visual-studio.md)程式。

## <a name="command-line-arguments"></a>命令列引數
 如果 [**調試** 程式] 屬性頁上的 [**起始動作**] 設定為 [**起始專案**]，則即使您已指定命令列引數做為起始選項，Visual Studio 也不會在對專案進行偵錯工具時使用命令列引數。 如果您想要在啟動偵錯工具時使用命令列引數，您必須選取 [**起始專案**] 以外的 [**起始動作**]。

## <a name="source-control"></a>原始檔控制
 偵錯屬性不是在原始檔控制中由多位使用者共用。 Visual Basic 和 C# 專案將偵錯屬性儲存在使用者專屬檔案中 (*專案名稱*.vbproj.user 或 *專案名稱*.csproj.user)，而這個檔案不在原始檔控制中。 如果有多人同時進行偵錯，每個人都必須手動輸入偵錯屬性。

## <a name="debug-cached-datasets-in-a-document-level-project"></a>在檔層級專案中，將快取的資料集進行 Debug 錯
 每次建置專案時，資料集會先清空再重新建立。 如果您想要偵錯快取資料集，您必須在 Visual Studio 外部開啟文件，然後再附加偵錯工具。

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>根據 Word 97-2003 檔 ( * .doc) 格式來對 Word 檔專案進行 Debug 錯
 */* 您必須將專案資料夾加入至 [信任的資料夾] 清單，才能根據 word 97-2003 檔 (.doc * ) 格式來對 Word 檔專案進行 debug 錯。 如需如何進行此作業的詳細資訊，請參閱 [授與信任給檔](../vsto/granting-trust-to-documents.md)。

## <a name="debug-disabled-add-ins"></a>停用已停用的增益集
 Microsoft Office 應用程式可以停用無法如預期般運作的 VSTO 增益集。 Microsoft Office 應用程式會停用 VSTO 增益集，以防止在每次應用程式啟動時載入有問題的程式碼。 不過，在進行一般偵錯時，也很容易會導致未預期的行為。 如需如何重新啟用 VSTO 增益集的詳細資訊，請參閱 [如何：重新啟用已停用的 Vsto 增益集](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)。

 Microsoft Office 應用程式有兩種停用 VSTO 增益集的方式：強制停用和非強制停用。

### <a name="hard-disabling"></a>強制停用
 當 VSTO 增益集導致應用程式意外關閉時，可能會發生強制停用。 在開發電腦上，如果您在 VSTO 增益集中的 <xref:Microsoft.Office.Tools.AddIn.Startup> 事件處理常式正在執行時停止偵錯工具，也可能發生這種情形。 當 VSTO 增益集遭到停用時，它會出現在應用程式的 [ **停用的專案** ] 清單中。

 如果 Office 應用程式硬性停用在 Visual Studio 中使用 Office 開發工具建立的 VSTO 增益集，應用程式只會停用造成失敗的 VSTO 增益集。 其他使用 Visual Studio 中之 Office 程式開發工具建立的 VSTO 增益集仍會繼續載入。

### <a name="soft-disabling"></a>軟停用
 當 VSTO 增益集產生的錯誤不會導致應用程式意外關閉時，可能會發生非強制停用。 例如，如果在 <xref:Microsoft.Office.Tools.AddIn.Startup> 事件處理常式正在執行時擲回未處理的例外狀況，應用程式可能會非強制停用 VSTO 增益集。 當 VSTO 增益集已虛停用時，它會出現在應用程式的 [非使用中 **應用程式增益集** ] 清單中，而應用程式會變更 VSTO 增益集的 **LoadBehavior** 登錄專案值，表示它已卸載。 如需 **LoadBehavior** 登錄專案的詳細資訊，請參閱 [VSTO 增益集的登錄專案](../vsto/registry-entries-for-vsto-add-ins.md)。

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>使用事件檢視器針對安裝錯誤進行疑難排解
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會將您安裝或解除安裝 Office 方案時擲回的所有例外狀況訊息，寫入 Windows 事件檢視器。 您可以使用這些訊息，來解決安裝和部署問題。

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>使用記錄檔和錯誤訊息針對啟動錯誤進行疑難排解
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可將啟動期間發生的所有錯誤寫入記錄檔，或以訊息方塊顯示每個錯誤。 根據預設，這些選項為關閉狀態。 您可以藉由建立環境變數來開啟選項。

 若要以訊息方塊顯示每個錯誤，請建立名為 `VSTO_SUPPRESSDISPLAYALERTS` 的環境變數，並將其設定為 0 (零)。 您可以刪除環境變數或將其設定為 1 (一)，來隱藏訊息。

 若要將錯誤寫入記錄檔，請建立名為 `VSTO_LOGALERTS` 的環境變數，並將其設定為 1 (一)。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會在包含 VSTO 增益集之部署資訊清單的資料夾中，或在包含與自訂關聯之文件或活頁簿的資料夾中，建立記錄檔。 如果失敗，則會 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 在本機 *% TEMP%* 資料夾中建立記錄檔。 若是應用程式層級 VSTO 增益集，預設名稱為 *增益集名稱*.vsto.log。 若是文件層級專案，記錄檔的名稱為 *文件名稱*.*副檔名*.log，例如 ExcelWorkbook1.xlsx.log。 若要停止記錄錯誤，請刪除環境變數或將其設定為 0 (零)。

## <a name="see-also"></a>另請參閱

- [建立 Office 方案](../vsto/building-office-solutions.md)
- [如何：重新啟用已停用的 VSTO 增益集](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)