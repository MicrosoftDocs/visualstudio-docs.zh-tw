---
title: '支援 (Preview 的 Visual Studio 功能) '
description: 瞭解使用 GitHub Codespaces 時可用的 Visual Studio IDE 功能。
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 68fbdef0e86b125971480ae1bd6a7ba6d3108cd8
ms.sourcegitcommit: 74b67f102d243e3b74a93563e834f49df298e4b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97696534"
---
# <a name="supported-visual-studio-features-preview"></a>支援 (Preview 的 Visual Studio 功能) 

Visual Studio 在連接至 codespace 時，提供豐富的開發體驗。 您可以取得您熟悉的 Visual Studio 內部迴圈工具，以編輯、偵測、測試和版本您的原始程式碼，以及諸如專案範本、豐富程式碼流覽和 IntelliSense 等生產力功能。

在目前的 GitHub Codespaces [公用 Beta 版](https://github.com/features/codespaces)中，某些 Visual Studio 功能可能不會有完整支援或一開始可能遺失。 下列各節概述 Visual Studio 和 GitHub Codespaces Beta 的預期內容，以及未來的未來可供您參考的內容。 

這 **不是一份詳盡的清單**，但為了說明 Visual Studio 連接到 codespace 時的一般功能。

> [!NOTE]
> 如果您在使用 codespaces 搭配 Visual Studio 時遺漏了功能，請在 [Visual Studio 開發人員社群](https://aka.ms/feedback/suggest?space=8)上開啟問題讓我們知道。 這可協助我們排列最需要的功能。

> [!NOTE]
> 以下所述的功能適用于 Visual Studio，而不是其他兩個 GitHub Codespaces 用戶端;Visual Studio Code 和瀏覽器內編輯器。

## <a name="edit-and-navigation"></a>編輯和流覽

當您取得智慧型語言功能（例如 IntelliSense、程式碼導覽、診斷和建議）時，您應該會注意到 codespace 中的編輯原始碼差異很小。

* 智慧
* 程式碼流覽 *
* 使用格式檔案格式化程式碼
* 語法醒目提示
* 快速資訊 *
* HTML、CSS、Razor 編輯器 *-部分支援。
* JavaScript 和 TypeScript 編輯器 *-部分支援。

尚未提供：

* IntelliSense *-某些自動完成/成員清單篩選器無法使用。 在 [監看式] 視窗中的未匯入類型和 IntelliSense 的完成尚未提供。
* 程式碼流覽 *-支援的大部分命令。 尚不支援移至基底，並在檔案中尋找路徑規格。
* 快速資訊 *-不支援快速諮詢中的顏色標示。
* HTML、CSS、Razor 編輯器 *-診斷、IntelliSense 完成、快速資訊、智慧縮排。 目前不支援語義顏色標示、流覽命令等等。
* JavaScript 和 TypeScript 編輯器 *-腳本區塊 (例如，HTML 和 CSHTML 檔案中的 JavaScript 內容) 和語義醒目提示尚未受到支援。 燈泡功能和 linting 的已知問題。
* CMake 目標視圖
* CMake 專案設定編輯器
* Ctrl + F7 (編譯檔) 
* CodeLens
* 程式碼片段
* IntelliCode

## <a name="application-types-and-configuration"></a>應用程式類型和設定

大部分的應用程式類型和專案設定都受到支援，但您必須直接編輯專案程式碼，而不需要視覺化設計工具的協助。 如需更多設定指引，請參閱 [如何自訂 codespace](customize-codespaces.md)。

* 專案範本與項目範本
* .NET Core 和 ASP.NET Core 專案
* C + + 主控台應用程式-支援 CMake 和 .vcxproj
* 以 Linux 為目標的 c + + 應用程式，大多支援非 GUI。 能夠安裝和布建 WSL、平臺特定的 IntelliSense 和組建。
* 專案檔案編輯-大多支援。 遺漏一些完成、語法反白顯示和先進的編輯功能。
* GitHub 帳戶-可以用來建立和連線至 Codespaces，並存取 GitHub 上的帳戶可用的資源。
* Azure CLI-不會共用已登入的 Visual Studio 身分識別或 keychain 帳戶。 不支援以瀏覽器為基礎的登入，但您可以使用下列程式在整合式終端機中進行驗證： `az login --use-device-code` 。

尚未提供：

* UI 設計工具-WinForms、WPF 和資源設計工具
* Visual Basic 和 F # 專案
* .NET Framework 目標專案
* Docker Compose 專案
* 專案屬性頁
* ASP.NET Core 範本中的驗證選項
* 需要 GUI 才能安裝的應用程式-支援可與終端機一起安裝的任何應用程式 (包括 chocolatey 安裝程式) ，但實際的 GUI 將無法立即使用。 啟用全螢幕 Live Share 存取 Gui 是目前的因應措施。 無法存取管理主控台。 不支援需要重新開機才能安裝的應用程式。
* Visual Studio 中適用于 Azure 資源的受控識別
* 內部網路資源 (私人網路) -目前，codespaces 將無法連線到任何需要 VPN 的資源。
* 擴充功能-搭配 Visual Studio 使用 Codespaces 時，不支援延伸模組。

## <a name="debugging"></a>偵錯

支援必要的內部迴圈偵錯工具，包括設定中斷點、基本逐步執行程式碼、檢查變數，以及本機、自動變數和監看式視窗。 不支援某些其他的視窗、自訂和視覺化檢視。

* 中斷
* 基本逐步執行
* 區域變數、自動變數、監看式視窗 *-部分支援。
* 符號伺服器、來源伺服器，以及匯入/匯出資料提示都有部分支援。

尚未提供：

* 在 [反組解碼] 視窗中，中斷點 *-中斷點標籤、資料中斷點和設定中斷點正在進行中。 部分支援匯入和匯出中斷點。
* [區域變數]、[自動變數]、[監看式] 視窗 *-一些功能，例如搜尋方塊中的語句完成和搜尋方塊導覽。
* UI 自訂-不支援可釘選屬性和隱藏範本參數。
* 視覺化檢視：部分支援 c + + natvis。 不支援 [反組解碼] 視窗、XAML 視覺效果診斷、自訂 .NET 視覺化程式和資料集視覺化檢視。
* 其他偵錯工具視窗-部分支援的 windows 進程。 不支援 [平行堆疊] 視窗-[工作視圖]、[診斷中樞] 和 [尋找來源/符號] 對話方塊。
* 某些偵錯工具工作流程-附加至進程，及時 (JIT) 偵錯工具，不支援傾印偵錯工具、分析和 IntelliTrace。 部分支援 c + + Just My Code 逐步執行。
* 編輯後繼續-managed 和機器碼都不支援。
* 執行緒功能-不支援凍結/解除凍結執行緒、重新命名執行緒，以及顯示來源中的執行緒。
* 其他逐步執行功能-不支援在屬性和運算子 ( .NET Core) 和逐步執行特定的自動步驟。 

## <a name="features"></a>功能

使用連接至 codespace 的 Visual Studio 時，您會取得與在本機工作時相同的協助工具功能。

* 原始檔控制-透過新的整合式 [git 體驗](../git-with-visual-studio.md)的完整 Git 支援。
* 協助工具-有一個已知的輔助技術問題，無法存取已進行偵錯工具的 appcasting。 除了這項限制，我們不認為本機 Visual Studio 體驗中還沒有任何其他相容性問題。 如果您在 [開發人員群體](https://aka.ms/feedback/report?space=8)上提出問題，請讓我們知道您是否偵測到 bug。
* 支援透過 GitHub Actions 發佈到 Azure。
* 已連線的服務-已部分支援 App Insights、KeyVault、儲存體、SQL、Redis、Cosmos、openAPI 和 gRPC。
* 測試瀏覽器 *-主要支援。

尚未提供：

* Test Explorer *-部分功能，例如預設架構選取、平行執行測試、播放清單等。偵測單元測試、執行設定和一些其他企業功能的已知問題。 不支援分析單元測試。
* NuGet 封裝管理員 UI-支援 NuGet 命令列。
* 企業測試功能-不支援 Live Unit Testing、Microsoft Fakes、程式碼涵蓋範圍和 IntelliTest。
* Advanced 發行案例-選擇性發佈、FTP 發佈、預覽變更、快速發佈工具列等。

## <a name="see-also"></a>請參閱

* [什麼是 GitHub Codespaces？](codespaces-overview.md)
* [如何搭配 codespace 使用 Visual Studio](use-visual-studio-with-codespaces.md)
* [如何自訂 codespace](customize-codespaces.md)
