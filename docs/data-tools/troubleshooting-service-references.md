---
title: 服務參考的疑難排解
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 28ff14f10cd6ad5612551bb65b7b17f0280358f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639594"
---
# <a name="troubleshoot-service-references"></a>針對服務參考進行疑難排解

本主題列出當您使用 Windows Communication Foundation （WCF）或 Visual Studio 中 WCF Data Services 參考時可能發生的常見問題。

## <a name="error-returning-data-from-a-service"></a>從服務傳回資料時發生錯誤

當您從服務傳回 `DataSet` 或 `DataTable` 時，您可能會收到「已超過傳入訊息的大小上限」例外狀況。 根據預設，某些系結的 `MaxReceivedMessageSize` 屬性會設定為相對較小的值，以限制暴露于拒絕服務的攻擊。 您可以增加這個值，以防止發生例外狀況。 如需詳細資訊，請參閱<xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>。

修正這個錯誤：

1. 在**方案總管**中，按兩下*app.config*檔案以開啟它。

2. 找出 [`MaxReceivedMessageSize`] 屬性，並將它變更為較大的值。

## <a name="cannot-find-a-service-in-my-solution"></a>在我的方案中找不到服務

當您按一下 [**加入服務參考**] 對話方塊中的 [**探索**] 按鈕時，解決方案中的一個或多個 WCF 服務程式庫專案不會出現在 [服務] 清單中。 如果已將服務程式庫加入至方案，但尚未進行編譯，就會發生這種情況。

修正這個錯誤：

- 在**方案總管**中，以滑鼠右鍵按一下 [WCF 服務程式庫] 專案，然後按一下 [**建立**]。

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>透過遠端桌面存取服務時發生錯誤

當使用者透過遠端桌面連線存取 Web 裝載的 WCF 服務，而使用者沒有系統管理許可權時，就會使用 NTLM 驗證。 如果使用者沒有系統管理許可權，則使用者可能會收到下列錯誤訊息：「HTTP 要求未經授權使用用戶端驗證配置 ' Anonymous '。 從伺服器收到的驗證標頭為「NTLM」。」

修正這個錯誤：

1. 在網站專案中，開啟 [**屬性**] 頁面。

2. 在 [**開始選項**] 索引標籤上，清除 [ **NTLM 驗證**] 核取方塊。

    > [!NOTE]
    > 您應該只針對獨佔包含 WCF 服務的網站關閉 NTLM 驗證。 WCF 服務的安全性是*透過 web.config 檔案*中的設定來管理。 這會使 NTLM 驗證不必要。

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>[產生的類別] 設定的存取層級無效

將 [**設定服務參考**] 對話方塊中的 [**產生的類別的存取層級**] 選項設定為 [**內部**] 或 [ **Friend** ]，可能不一定會有效。 雖然此選項會在對話方塊中顯示，但產生的支援類別是以 `Public` 的存取層級來產生。

這是已知的特定類型限制，例如使用 <xref:System.Xml.Serialization.XmlSerializer> 進行序列化的。

## <a name="error-debugging-service-code"></a>偵錯工具服務程式代碼時發生錯誤

當您從用戶端程式代碼逐步執行 WCF 服務的程式碼時，可能會收到與遺漏符號相關的錯誤。 當方案中的服務已移動或從解決方案移除時，就可能發生這種情況。

當您第一次加入屬於目前方案一部分之 WCF 服務的參考時，服務專案與服務用戶端專案之間會加入明確的組建相依性。 這可確保用戶端一律會存取最新的服務二進位檔，這對於將從用戶端程式代碼逐步執行至服務程式代碼的案例而言特別重要。

如果服務專案已從方案中移除，此明確組建相依性將會失效。 Visual Studio 無法再保證服務專案會視需要重建。

若要修正此錯誤，您必須手動重建服務專案：

1. 在 [ **工具** ] 功能表上按一下 [ **選項**]。

2. 在 [**選項**] 對話方塊中，展開 [**專案和方案**]，然後選取 **[一般**]。

3. 請確定已選取 [**顯示先進的組建**設定] 核取方塊，然後按一下 **[確定]** 。

4. 載入 WCF 服務專案。

5. 在 [ **Configuration Manager** ] 對話方塊中，將 [使用中的**方案**設定] 設為 [ **Debug**]。 如需詳細資訊，請參閱[如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)。

6. 在 **方案總管**中，選取 WCF 服務 專案。

7. 在 [**建立**] 功能表上，按一下 [**重建**] 以重建 WCF 服務專案。

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services 不會顯示在瀏覽器中

當它嘗試在 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] 中查看資料的 XML 表示時，Internet Explorer 可能會將資料錯誤解譯為 RSS 摘要。 請確定 [顯示 RSS 摘要] 的選項已停用。

若要修正此錯誤，請停用 RSS 摘要：

1. 在 Internet Explorer 的 [工具] 功能表中，按一下 [網際網路選項]。

2. 在 [**內容**] 索引標籤的 [摘要 **] 區段中**，按一下 [**設定**]。

3. 在 [摘要**設定**] 對話方塊中，清除 [**開啟摘要閱讀檢視**] 核取方塊，然後按一下 **[確定]** 。

4. 按一下 [確定] 以關閉 [網際網路選項] 對話方塊。

## <a name="see-also"></a>請參閱

- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)