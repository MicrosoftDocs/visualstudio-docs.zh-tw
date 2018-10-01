---
title: Visual Studio 中的 IntelliTrace 資料
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 30a6cb4f2d39e16a9ff5334bc0676707e4c65dce
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44321147"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>如何：收集 IntelliTrace 資料以協助偵錯困難的問題

您可以在 Visual Studio 中設定診斷資料配接器，讓 IntelliTrace 收集特定診斷追蹤資訊。 測試可以使用此配接器，如此測試就可以收集應用程式的重大診斷事件，讓開發人員之後使用這些事件追蹤整個程式碼，找出 Bug 的原因。 IntelliTrace 的診斷資料配接器可以用於手動或自動化測試。

> [!NOTE]
> IntelliTrace 只會在使用 Managed 程式碼所撰寫的應用程式上運作。 如果您要測試使用瀏覽器做為用戶端的 Web 應用程式，就不應該在測試設定中針對該用戶端啟用 IntelliTrace，因為沒有任何 Managed 程式碼可進行追蹤。 在此情況下，您可能會想要設定環境並且在 Web 伺服器上遠端收集 IntelliTrace 資料。

IntelliTrace 資料儲存在副檔名為 *.iTrace* 的檔案中。 在您執行測試時，若測試步驟失敗，您可以建立 Bug。 包含診斷資訊的 IntelliTrace 檔案會自動附加至此 Bug 中。

> [!NOTE]
> 測試成功時，IntelliTrace does 的診斷資料配接器不會建立 IntelliTrace 檔。 它只會在測試案例失敗或您送出 Bug 時儲存檔案。

 IntelliTrace 檔中收集的資料可縮短重現及診斷程式碼錯誤所需的時間，進而提高偵錯的效能。 此外，因為您可以與其他人共用 IntelliTrace 檔，而且這些人可在其電腦上複製您的本機工作階段，所以這會降低不可重現 Bug 的可能性。

> [!NOTE]
> 如果您在測試設定中啟用 IntelliTrace，則無法收集程式碼涵蓋範圍資料。

> [!WARNING]
> IntelliTrace 的診斷資料配接器會透過檢測 Managed 處理序來運作，該檢測作業必須在載入測試回合的測試之後執行。 如果您要監視的處理序已啟動，則不會收集任何 IntelliTrace 檔，因為處理序已在執行中。 若要避免此情況，請確定處理序在載入測試之前已停止。 然後，請在載入測試或啟動第一項測試之後，啟動處理序。

 下列程序說明如何設定您想要收集的 IntelliTrace 資料。 這些步驟同時適用於 Microsoft Test Manager 中的組態編輯器和 Visual Studio 中的 [測試設定] 對話方塊。

> [!NOTE]
> 就用以收集 IntelliTrace 資料的測試代理程式而言，其使用者帳戶必須是 Administrators 群組的成員。 如需詳細資訊，請參閱[安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>設定利用 IntelliTrace 診斷資料配接器收集的資料

執行這個程序中的步驟之前，您必須先從 Microsoft Test Manager 或 Visual Studio 開啟測試設定，然後選取 [資料和診斷] 頁面。

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>設定利用 IntelliTrace 診斷資料配接器收集的資料

1.  選取要用來收集 IntelliTrace 資料的角色。

2.  選取 [IntelliTrace]。

3.  如果您要針對 Web 用戶端角色或 ASP.NET Web 應用程式新增 IntelliTrace，那麼也必須選取 [用於 IntelliTrace 及測試影響的 ASP.NET 用戶端 Proxy]。

     此 Proxy 可讓您針對「IntelliTrace 和測試影響」診斷資料配接器，收集從用戶端到 Web 伺服器之 HTTP 呼叫的相關資訊。

    > [!WARNING]
    > 如果您決定要針對用於想要收集 Intellitrace 資料之 Internet Information Server (IIS) 上的應用程式集區識別使用自訂帳戶，就必須在 IIS 電腦上，針對所使用的自訂帳戶建立本機使用者設定檔。 您可以透過登入 IIS 電腦本機一次或使用自訂帳戶認證來執行下列命令列，藉以建立自訂帳戶的本機設定檔：
    >
    > **runas /user:domain\name /profile cmd.exe**

4.  選擇 [IntelliTrace] 的 [設定]，修改預設 IntelliTrace 設定。

     設定將要收集之資料的對話方塊隨即顯示。

    > [!WARNING]
    > 如果您啟用收集 IntelliTrace 資料，則無法收集程式碼涵蓋範圍資料。

5.  選擇 [一般] 索引標籤。選取 [僅 IntelliTrace 事件] 記錄重大診斷事件，同時對測試期間的效能造成最小影響。

     -或-

     選取 [IntelliTrace 事件和呼叫資訊] 記錄診斷事件和顯示呼叫資訊的方法層級追蹤。 此追蹤層級可能會在您執行測試時對效能造成影響。

6.  若要從網際網路資訊服務上執行的 ASP.NET 應用程式收集資料，請選取 [收集執行於網際網路資訊服務之 ASP.NET 應用程式中的資料]。 在 Web 伺服器角色上安裝及設定您的測試代理程式。 請參閱[安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。

7.  選擇 [模組] 索引標籤。選取 [從所有模組收集資料，但下列模組例外]，然後使用 [新增] 以新增至模組清單，並使用 [移除] 以移除模組。 此選項可讓您納入系統上執行的所有模組，但您指定的模組例外。

     -或-

     選取 [只從下列模組收集資料]，然後使用 [新增] 以新增至模組清單，並使用 [移除] 以移除模組。 此選項可讓您確切地指定想要的模組。

    > [!NOTE]
    > 請盡可能選取您想要監視的特定處理序。 這是最佳效能的建議事項。

8.  選擇 [處理序] 索引標籤。選取 [從所有處理序收集資料，但下列處理序例外]，然後使用 [新增] 以新增至處理序清單，並使用 [移除] 以移除處理序。 此選項可讓您納入系統上執行的所有處理序，但您指定的處理序例外。

     -或-

     選取 [只從指定的處理序收集資料]，然後使用 [新增] 以新增至處理序清單，並使用 [移除] 以移除處理序。 此選項可讓您確切地指定想要的處理序。

9. (選擇性) 選擇 [IntelliTrace 事件] 索引標籤。選取或清除收集診斷事件時想要納入或排除的每個 IntelliTrace 事件分類。

10. (選擇性) 展開每個 IntelliTrace 事件分類，並選取或清除您想要在 IntelliTrace 事件中納入或排除的每個特定事件。

11. (選擇性) 選擇 [進階] 索引標籤。接著，選擇 [用於記錄的最大磁碟空間] 旁邊的箭號，並選取要讓 IntelliTrace 檔案使用的大小上限。

    > [!NOTE]
    > 如果您增加了記錄的大小，當您將這項記錄與測試結果儲存在一起時，可能會發生逾時問題。 如需如何針對診斷資料配接器增加逾時值的詳細資訊，請參閱[如何：防止診斷資料配接器逾時](../test/how-to-prevent-time-outs-for-diagnostic-data-adapters.md)。

12. 如果您要使用 Microsoft Test Manager，請選擇 [儲存]。 如果您要使用 Visual Studio，請選擇 [確定]。 針對測試設定，現在已經設定和儲存 IntelliTrace 設定。

    > [!NOTE]
    > 若要重設此診斷資料配接器的組態，在 Visual Studio 中請選擇 [重設為預設組態]****，在 Microsoft Test Manager 中則選擇 [重設為預設值]****。

## <a name="see-also"></a>另請參閱

- [在測試時收集診斷資料 (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [在手動測試中收集診斷資料 (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)
- [收集 IntelliTrace 資料](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)