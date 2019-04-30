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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f0d1a9e24c965af9513b3c2645bcee35f916f436
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565729"
---
# <a name="troubleshoot-service-references"></a>針對服務參考進行疑難排解

本主題列出當您使用 Windows Communication Foundation (WCF) 或 Visual Studio 中的 WCF 資料服務參考時可能發生的常見問題。

## <a name="error-returning-data-from-a-service"></a>從服務傳回資料時發生錯誤

當您恢復`DataSet`或`DataTable`從服務中，您可能會收到 「 內送訊息的大小上限配額已超過 」 的例外狀況。 根據預設，`MaxReceivedMessageSize`某些繫結的屬性設為相對較小的值來限制暴露於阻絕服務攻擊。 您可以增加此值，以避免這個例外狀況。 如需詳細資訊，請參閱<xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>。

修正這個錯誤：

1. 在 [**方案總管] 中**，按兩下*app.config*檔案將它開啟。

2. 找出`MaxReceivedMessageSize`屬性並將它變更為較大的值。

## <a name="cannot-find-a-service-in-my-solution"></a>找不到我的解決方案中的服務

當您按一下 [ **Discover**按鈕**加入服務參考**] 對話方塊中，方案中的一或多個 WCF 服務程式庫專案不會出現在 [服務] 清單中。 如果服務程式庫已新增至方案，但尚未編譯，也可能會發生。

修正這個錯誤：

- 在 **方案總管**，以滑鼠右鍵按一下 WCF 服務程式庫專案，然後按一下**建置**。

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>透過遠端桌面存取的服務時發生錯誤

當使用者存取 Web 裝載的 WCF 服務，透過遠端桌面連線和使用者沒有系統管理權限，會使用 NTLM 驗證。 如果使用者沒有系統管理權限，使用者可能會收到下列錯誤訊息：「 HTTP 要求是未經授權的用戶端驗證配置 'Anonymous'。 從伺服器收到的驗證標頭是 'NTLM'。 」

修正這個錯誤：

1. 在網站專案中，開啟**屬性**頁面。

2. 在 **啟動選項**索引標籤上，清除**NTLM 驗證**核取方塊。

    > [!NOTE]
    > 您應該關閉 NTLM 驗證，只針對只包含 WCF 服務的網站。 WCF 服務的安全性透過在組態管理*web.config*檔案。 這可讓 NTLM 驗證的非必要。

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>產生的類別設定的存取層級沒有任何作用

設定**存取產生的類別層級**選項**設定服務參考**對話方塊，即可**內部**或是**Friend**未必可行。 即使在對話方塊中設定，會出現的選項，產生的支援類別產生的存取層級的`Public`。

這是特定類型，例如使用序列化的已知的限制<xref:System.Xml.Serialization.XmlSerializer>。

## <a name="error-debugging-service-code"></a>錯誤偵錯服務程式碼

當您從用戶端程式碼逐步執行 WCF 服務的程式碼時，您可能會收到與符號遺失相關的錯誤。 服務方案的一部分，已被移動，或從解決方案移除時，可能發生這項目。

當您第一次新增屬於目前方案的 WCF 服務的參考時，之間服務專案和服務用戶端專案加入明確組建相依性。 這樣可保證，用戶端一律會存取最新的服務二進位檔，這是特別重要案例，例如從用戶端程式碼逐步執行服務程式碼進行偵錯。

如果從方案移除服務專案，此明確組建相依性將會失效。 Visual Studio 無法再保證，服務就會重建專案為必要。

若要修正這個錯誤，您必須以手動方式重新建置服務專案：

1. 在 [ **工具** ] 功能表上按一下 [ **選項**]。

2. 在 **選項**對話方塊方塊中，展開**專案和方案**，然後選取**一般**。

3. 請確定**顯示進階組建組態** 核取方塊已選取，然後再按一下**確定**。

4. 載入 WCF 服務專案。

5. 在 [ **Configuration Manager** ] 對話方塊中，將**現用方案組態**來**偵錯**。 如需詳細資訊，請參閱[如何：建立及編輯組態](../ide/how-to-create-and-edit-configurations.md)。

6. 在 **方案總管 中**，選取 WCF 服務專案。

7. 在 [**建置**] 功能表中，按一下**重建**重建 WCF 服務專案。

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF 資料服務不會顯示在瀏覽器

它會嘗試將檢視中資料的 XML 表示法[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]，Internet Explorer 可能會錯誤解譯為 RSS 摘要的資料。 請確定顯示 RSS 摘要的選項已停用。

若要修正這個錯誤，請停用 RSS 摘要：

1. 在 Internet Explorer 的 [工具] 功能表中，按一下 [網際網路選項]。

2. 在 **內容**索引標籤中，於**摘要**區段中，按一下**設定**。

3. 在 **摘要的設定**對話方塊中，清除**開啟摘要讀取檢視**核取方塊，然後按一下**確定**。

4. 按一下 [確定] 以關閉 [網際網路選項] 對話方塊。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)