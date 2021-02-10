---
title: R 工作區
description: 如何在 Visual Studio 中使用工作區來控制 R 程式碼執行所在的位置。
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 3627a8944941fc77bb9b19fe3dd0a1549f41892a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961582"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>控制 R 程式碼以工作區執行的位置

Visual Studio R 工具 (RTVS) 的工作區可讓您設定 R 工作階段的執行位置，此位置可能位於本機和遠端電腦。 目標是讓您以可比較性的使用者體驗在任一電腦上運作，讓您能夠充分利用可能更強大的雲端型電腦。

若要開啟 [工作區] 視窗，請使用 [R 工具] > [Windows] > [工作區] 命令，或按 **Ctrl**+**9**。

![Visual Studio R 工具的工作區視窗 (VS2017)](media/workspaces-window.png)

在此視窗中，綠色的核取記號表示 RTVS 繫結所在的使用中工作區。 選取藍色箭頭可設定使用中的工作區。 每個工作區右邊的設定 (齒輪) 圖示可讓您變更其名稱、位置和命令列引數。 紅色 X 會移除以手動方式新增的工作區。

## <a name="save-and-reset-a-workspace"></a>儲存並重設工作區

根據預設，當您關閉並重新開啟專案時，RTVS 不會儲存工作區狀態。 但是您可以透過[工作區選項](options-for-r-tools-in-visual-studio.md#workspace)變更此行為。

[ **R 工具**  >  **會話**  >  **重設**] 命令和互動式視窗中的 [重設] 工具列按鈕，也會隨時重設工作區狀態。 使用遠端工作區，重設會刪除第一次連線到遠端伺服器時所建立的使用者設定檔，這其實會刪除此處累積的任何檔案。

## <a name="local-workspaces"></a>本機工作區

[本機工作區] 清單會顯示您電腦上安裝的所有 R 解譯器。

當 Visual Studio 啟動時，它會嘗試透過查看 **HKEY_LOCAL_MACHINE\Software\R-Core\\** 登錄機碼，自動偵測您已安裝的所有 R 版本。 因為這項檢查只會在啟動時完成，所以如果您安裝新的 R 解譯器，就需要重新啟動 Visual Studio。

RTVS 可能偵測不到非以標準方式安裝的 R 解譯器 (例如，僅將檔案複製到資料夾而不是執行安裝程式)。 如果是這種情況，請以手動方式建立新的本機 R 工作區，如下所示︰

1. 選取 [工作區] 視窗中的 [新增] 按鈕。
1. 輸入新工作區的名稱。
1. 輸入 R 根資料夾的路徑，亦即包含 *bin* 資料夾及解譯器的路徑，以及 RTVS 啟動時傳遞至解譯器的任何選用命令列引數。
1. 完成時，請選取 [儲存]  。

![新增新的工作區](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>遠端工作區

遠端工作區可讓您連線到遠端電腦的 R 工作階段。 (如需如何設定此用途的電腦，請參閱[設定遠端工作區](setting-up-remote-r-workspaces.md)。)

Visual Studio 不會自動偵測遠端工作區，因此您必須使用 [工作區] 視窗中的 [新增] 按鈕手動新增它們，如上節所述。 在此情況下，請輸入遠端電腦的 URI，而不是輸入本機路徑。

> [!Important]
> 遠端工作區是由「必須使用 HTTPS 通訊協定」的 URI 所識別，以確保與遠端電腦通訊的隱私權和完整性。 Visual Studio 無法連線到不支援 HTTPS 的遠端電腦。

> [!Note]
> 遠端工作區預覽有效。 我們正在努力改善未來版本的檔案同步實作問題，歡迎您提供想法和意見反應。

## <a name="remote-workspace-logon"></a>遠端工作區登入

您必須輸入使用者名稱和密碼來登入遠端工作區。

### <a name="logon-to-windows-workspace"></a>登入 Windows 工作區

如果您的遠端電腦是設定為使用網域帳戶，您即可使用網域登入來存取遠端工作區。 如果不是，您就必須使用 `machine-name\username` 格式，藉由遠端電腦上的電腦帳戶來登入。

### <a name="logon-to-linux-workspace"></a>登入 Linux 工作區

若要登入 Linux 帳戶，請使用 `<<unix>>\username` 格式。 例如，如果您擁有的帳戶名稱為 `ruser`，則您應該鍵入下列使用者名稱：`<<unix>>\ruser`。

## <a name="switch-between-workspaces"></a>切換工作區

RTVS 一次只會繫結至一個工作區。 繫結工作區是以 [工作區] 視窗中的小型綠色勾選記號表示。 根據預設，RTVS 會繫結至上一個工作階段中最後開啟的本機工作區。

若要變更使用中的工作區，請選取所需工作區旁的藍色箭號。 如此一來，系統會提示您儲存工作階段、終止目前的工作區，然後切換到新的工作區。

> [!Tip]
> 若要停用儲存提示，請選取 [ **R 工具**  >  **選項**] 命令，並在 [**切換工作區] 選項之前，先設定 [顯示確認] 對話方塊** `No` 。 請參閱[工作區選項](options-for-r-tools-in-visual-studio.md#workspace)。

如果您嘗試切換至已解除安裝的本機工作區或無法使用的遠端工作區，則 RTVS 可能未繫結至任何工作區。 因此，當您在互動視窗中輸入程式碼時，或另行嘗試執行程式碼時，可能會看到錯誤：

![沒有任何工作區繫結至 RTVS 時發生錯誤](media/workspaces-disconnected-interactive-window.png)

若要修正此問題，請切換到 [工作區] 視窗中的另一個工作區。 如果沒有任何可用的工作區，您必須安裝 R 解譯器。 如果您在 Visual Studio 執行時已安裝解譯器，則也可以嘗試重新啟動 Visual Studio。

### <a name="switch-to-a-remote-workspace"></a>切換至遠端工作區

RTVS 會在您第一次連線到遠端工作區時提示您輸入認證，然後 (使用安全的 Windows 認證保險箱) 快取這些認證供後續工作階段使用。 然後透過 HTTPS 安全地與遠端伺服器完成通訊 (這是必要的)。

根據伺服器的組態，您可能會在連線時看到憑證警告：「遠端 R 服務所提供的安全性憑證無法讓我們證明您確實正在連線到電腦 (名稱)」。

![連線到遠端工作區時出現自我簽署憑證警告](media/workspaces-remote-self-signed-certificate-warning.png)

憑證是您嘗試連線的電腦向 RTVS 呈現的文件。 憑證包含的欄位可識別該電腦的 URI。 當 RTVS 偵測到憑證中的 URI 與連連線電腦所用的 URI 不符時，就會發出警告，指出伺服器的安全性可能已遭入侵。

不過，如果遠端電腦使用「自我簽署憑證」來啟用 HTTPS，而不是使用信任提供者的憑證，也會出現這項警告。 如需詳細資訊，請參閱[設定遠端工作區](setting-up-remote-r-workspaces.md)。

## <a name="directories-on-local-and-remote-computers"></a>本機和遠端電腦上的目錄

根據預設，當您在本機工作區中啟動新的 R 解譯器時，目前的工作目錄會是 *%userprofile%\Documents*。 您可以使用 [ **R 工具**  >  **工作目錄**] 命令隨時變更目錄，或以滑鼠右鍵按一下 Visual Studio 方案總管中的專案，然後選取 [在 **這裡設定工作目錄**] 之類的命令。

當您第一次連線到遠端電腦時，RTVS 會根據您的認證自動建立使用者設定檔，這樣會將工作目錄設定為該設定檔下的 *Documents* 資料夾。 此資料夾用於所有使用相同認證的後續遠端工作階段。

如此一來，程式碼實際執行的位置在本機和遠端工作區就不同。 在您的程式碼，則請一律使用資料檔案的相對路徑，讓您的程式碼可移植到不同的工作區。

亦請注意，在遠端工作區中，各個工作階段工作目錄中的所有檔案仍都保留在相同使用者設定檔原位。 如先前所述，您可以在使用遠端工作區時，使用 [ **R 工具**  >  **會話**  >  **重設**] 命令 (或互動式視窗) 中的 [重設] 按鈕來刪除這些檔案。 此命令會再次刪除伺服器中的使用者設定檔，這在您重新連線時會重新建立。

## <a name="copy-project-files-to-remote-workspaces"></a>將專案檔案複製到遠端工作區

在 Visual Studio 中使用 R 專案時，即使您使用遠端工作區，本機電腦還是一律會有最新的專案檔。 亦即當您在 Visual Studio 中開啟專案時 (通常表示開啟包含該專案的方案)，RTVS 會假設專案的內容完全位於本機電腦上。 遠端工作區其實只是專案檔案和任何程式碼輸出的暫存主機。 這表示，例如，在互動式視窗中使用 `source` 載入檔案時，該檔案必須已在您提供的遠端電腦路徑中，或者必須在遠端 R 解譯器目前的工作目錄中 (以 `setwd()` 函式設定)。

檔案會複製到遠端伺服器，如下所示︰

- 若要透過互動視窗從遠端使用檔案，您必須先在 [方案總管] 中以滑鼠右鍵按一下這些檔案 (或專案)，然後選取 [Source Selected]\(選取的來源) 來手動複製這些檔案。 個別檔案會複製至伺服器的工作目錄。複製專案時，RTVS 會建立專案的資料夾。

- 您也可以在方案總管中選取檔案，然後選取 [所選來源檔案] 來複製檔案。 此動作會將它們載入至互動式視窗，並在此執行。 如果工作階段連線到遠端電腦，檔案會先複製至該處。

- 如果 RTVS 繫結至遠端工作區而您按 **F5**、選取 [偵錯] > [開始偵錯] 或另行開始執行您的程式碼，RTVS 預設會自動將專案檔案複製到遠端工作區 (如需控制此行為的方法，請參閱下文)。

- 會覆寫已經存在於伺服器上的任何檔案。

> [!Note]
> 因為 RTVS 無法可靠地攔截所有 R 函式呼叫，所以在互動式視窗內呼叫 `source()` 或 `runApp()` 這類函式 (適用於 Shiny 應用程式)「不會」將檔案複製至遠端工作區。

[專案屬性](r-projects-in-visual-studio.md#project-properties)可控制 RTVS 在執行專案時是否複製檔案，且實際複製的檔案為何。 若要開啟此頁面，請選取 **專案**  >  **(名稱) [屬性**] 功能表命令，或以滑鼠右鍵按一下方案總管中的專案，然後選取 [**屬性**]。

![專案屬性執行索引標籤與檔案傳輸設定](media/workspaces-remote-file-transfer-filter-settings.png)

在此，[Transfer files on run] (執行時傳輸檔案) 屬性會判斷 RTVS 是否自動複製專案檔。 接著 [Files to transfer] (要傳輸的檔案) 值會確實篩選要傳送哪些檔案。 預設值為僅複製 *.R*、*.Rmd*、*.sql*、*.md* 和 *.cpp* 檔案。 此行為是為了避免每次執行時不小心將大型的資料檔案複製至伺服器。

## <a name="copy-files-from-a-remote-workspace"></a>從遠端工作區複製檔案

如果您的 R 指令碼會在伺服器上產生檔案，您可以使用 `rtvs::fetch_file` 函式將這些檔案複製回用戶端。 此函式至少會接受您想要複製到電腦的檔案遠端路徑，並且選擇性接受您電腦上的目標路徑。 如果您未指定路徑，就會將檔案複製至您的 *%userprofile%\Downloads* 資料夾。
