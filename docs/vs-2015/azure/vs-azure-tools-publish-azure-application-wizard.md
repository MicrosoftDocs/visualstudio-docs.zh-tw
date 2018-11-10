---
title: 使用 Visual Studio 發佈 Azure 應用程式精靈 |Microsoft Docs
description: 了解如何設定 Visual Studio 發行 Azure 應用程式精靈中的各種設定
author: ghogen
manager: douge
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: c9c4104d4d07cab7486038a8787ed0c7759abd60
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002022"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>使用 Visual Studio 發佈 Azure 應用程式精靈

開發 Visual Studio 中的 web 應用程式之後，您可以使用發行 Azure 雲端服務應用程式**發佈 Azure 應用程式**精靈。

> [!Note]
> 這篇文章是關於部署到雲端服務，而不網站。 如需部署至網站的資訊，請參閱[如何部署 Azure 網站](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false)。

## <a name="accessing-the-publish-azure-application-wizard"></a>存取發佈 Azure 應用程式精靈

您可以存取發佈 Azure 應用程式精靈，有兩種，視您擁有的 Visual Studio 專案類型而定。

**如果您有 Azure 雲端服務專案：**

1. 建立或開啟 Visual Studio 中的 Azure 雲端服務專案。

1. 在 **方案總管**，以滑鼠右鍵按一下專案，並從操作功能表中，選取**發佈**。

**如果您有未啟用適用於 Azure web 應用程式專案：**

1. 建立或開啟 Visual Studio 中的 Azure 雲端服務專案。

1. 在 **方案總管**，以滑鼠右鍵按一下專案，並從操作功能表中，選取**轉換** > **轉換成 Azure 雲端服務專案**。 

1. 在 **方案總管**、 以滑鼠右鍵按一下新建立的 Azure 專案，並從操作功能表中，選取**發佈**。

## <a name="sign-in-page"></a>登入頁面

![登入頁面](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**帳戶**-選取帳戶，或選取**新增帳戶**帳戶下拉式清單中。

**選擇您的訂用帳戶**-選擇要用於您部署的訂用帳戶。

## <a name="settings-page---common-settings-tab"></a>設定頁面-一般設定 索引標籤

![一般設定](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**雲端服務**-使用下拉式清單中，選取現有的雲端服務，或選取**&lt;新建 >**，並建立雲端服務。 資料中心會顯示每個雲端服務的括號括住。 建議的資料中心的雲端服務的位置是相同的儲存體帳戶 （進階設定） 的資料中心位置。

**環境**-選取其中一個**生產**或是**預備**。 如果您想要部署您的應用程式，在測試環境，請選擇預備環境。 

**組建組態**-選取其中一個**偵錯**或是**發行**。

**服務組態**-選取其中一個**定域機組**或是**本機**。

**啟用所有角色的遠端桌面**-選取此選項，如果您想要能夠從遠端連線至服務。 此選項主要用於疑難排解。 如需詳細資訊，請參閱 <<c0> [ 使用 Visual Studio 的 Azure 雲端服務中的角色啟用遠端桌面連線](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)。

**啟用所有 web 角色的 Web Deploy** -選取此選項可啟用服務的 web 部署。 您也必須選取**啟用所有角色的遠端桌面**選項可使用這項功能。 如需詳細資訊，請參閱 <<c0> [ 發佈雲端服務，使用 Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)。

## <a name="settings-page---advanced-settings-tab"></a>設定頁面-進階設定 索引標籤

![進階設定](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**部署標籤**-接受預設名稱，或輸入您選擇的名稱。 若要將日期附加至部署標籤中，保留選取的核取方塊。 

**儲存體帳戶**-選取要用於此部署中，儲存體帳戶 * *&lt;新建 > 若要建立儲存體帳戶。 資料中心會顯示在括號內的每個儲存體帳戶。 建議的儲存體帳戶的資料中心位置是雲端服務 （一般設定） 的資料中心位置相同。

Azure 儲存體帳戶會儲存應用程式部署的封裝。 應用程式部署之後，封裝會移除從儲存體帳戶。

**刪除失敗的部署**-選取此選項可讓在發佈期間遇到任何錯誤時刪除部署。 如果您想要維護您的雲端服務的固定虛擬 IP 位址，則這應該是取消核取。

**部署更新**-如果您只想要部署已更新的元件，請選取此選項。 這種部署類型可以是更完整的部署。 如果您想要維護您的雲端服務的固定虛擬 IP 位址應檢查這。 

**部署更新-設定**-此對話方塊會用來進一步指定您希望更新角色的方式。 如果您選擇**累加式更新**，更新您的應用程式的每個執行個體是一個接一個，使應用程式一律可供使用。 如果您選擇**同時更新**，同時更新您的應用程式的所有執行個體。 同時更新較為快速，但您的服務可能無法在更新程序期間。

![部署設定](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**啟用 IntelliTrace** -指定您是否要啟用 IntelliTrace。 如果有 IntelliTrace，您可以在 Azure 中執行時記錄的角色執行個體的廣泛偵錯資訊。 如果您需要找出問題的原因，您可以使用 IntelliTrace 記錄檔，如同它已在 Azure 中執行，逐步執行程式碼從 Visual Studio。 如需使用 IntelliTrace 的詳細資訊，請參閱[已發佈 Azure 雲端服務，使用 Visual Studio 和 IntelliTrace 進行偵錯](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)。

**啟用程式碼剖析**-指定您是否要啟用效能分析。 Visual Studio 分析工具可讓您取得您的雲端服務的執行情況在計算方面的深入分析。 如需有關如何使用 Visual Studio 分析工具的詳細資訊，請參閱 <<c0> [ 測試 Azure 雲端服務的效能](./vs-azure-tools-performance-profiling-cloud-services.md)。

**啟用所有角色的遠端偵錯工具**-指定是否要啟用遠端偵錯。 如需有關偵錯使用 Visual Studio 的雲端服務的詳細資訊，請參閱 < [Azure 雲端服務或虛擬機器，在 Visual Studio 中偵錯](./vs-azure-tools-debug-cloud-services-virtual-machines.md)。

## <a name="diagnostics-settings-page"></a>診斷設定 頁面

![診斷設定](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

診斷可讓您針對 Azure 雲端服務 （或 Azure 虛擬機器） 進行疑難排解。 如需診斷資訊，請參閱 <<c0> [ 為 Azure 雲端服務和虛擬機器設定診斷](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)。 Application Insights 的相關資訊，請參閱[什麼是 Application Insights？](/azure/application-insights/app-insights-overview.md)。

## <a name="summary-page"></a>摘要頁面

![總結](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**目標設定檔**-您可以選擇從您所選擇的設定建立發行設定檔。 例如，您可以建立一個設定檔用於測試環境，另一個用於生產環境。 若要儲存此設定檔，請選擇**儲存**圖示。 此精靈會建立設定檔，並將它儲存在 Visual Studio 專案。 若要修改的設定檔名稱，開啟**目標設定檔**清單，然後再選擇**&lt;管理...&gt;**.

   > [!Note]
   > 發行設定檔會出現在 Visual Studio 中的 [方案總管] 中，設定檔設定寫入至副檔名為.azurePubxml 的檔案。 設定會儲存為 XML 標記的屬性。

## <a name="publishing-your-application"></a>發行您的應用程式

一旦您設定您的專案部署的所有設定，請選取**發佈**對話方塊的底部。 您可以監視中的程序狀態**輸出**Visual Studio 中的視窗。

## <a name="next-steps"></a>後續步驟

- [移轉並發佈至 Azure 雲端服務從 Visual Studio 將 Web 應用程式](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [了解如何使用 Visual Studio 發佈 Azure 雲端服務](./vs-azure-tools-publishing-a-cloud-service.md)

- [已發佈 Azure 雲端服務，使用 Visual Studio 和 IntelliTrace 進行偵錯](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [測試 Azure 雲端服務的效能](./vs-azure-tools-performance-profiling-cloud-services.md)

- [適用於 Azure 雲端服務和虛擬機器設定診斷](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)。

- [什麼是 Application Insights？](/azure/application-insights/app-insights-overview.md)