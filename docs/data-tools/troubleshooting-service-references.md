---
title: 服務參考的疑難排解
description: 檢查當您使用 Windows Communication Foundation (WCF) 或 Visual Studio 中 WCF Data Services 參考時可能發生的常見問題。
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 909291e3f9762593a58df93a9ccc7fe2e82b7952
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866355"
---
# <a name="troubleshoot-service-references"></a>針對服務參考進行疑難排解

本主題列出當您使用 Windows Communication Foundation (WCF) 或 Visual Studio 中 WCF Data Services 參考時可能會發生的常見問題。

## <a name="error-returning-data-from-a-service"></a>從服務傳回資料時發生錯誤

當您 `DataSet` 從服務傳回或時 `DataTable` ，您可能會收到「超過傳入訊息的大小上限」例外狀況。 根據預設，某些系結的 `MaxReceivedMessageSize` 屬性會設定為相對較小的值，以限制遭受拒絕服務的攻擊。 您可以增加此值以防止例外狀況。 如需詳細資訊，請參閱<xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>。

若要修正此錯誤：

1. 在 **方案總管** 中，按兩下 *app.config* 檔案將其開啟。

2. 找出 `MaxReceivedMessageSize` 屬性，並將其變更為較大的值。

## <a name="cannot-find-a-service-in-my-solution"></a>在我的解決方案中找不到服務

當您按一下 [**新增服務參考**] 對話方塊中的 [**探索**] 按鈕時，解決方案中的一或多個 WCF 服務程式庫專案不會出現在 [服務] 清單中。 如果已將服務程式庫新增至解決方案，但尚未進行編譯，就會發生這種情況。

若要修正此錯誤：

- 在 **方案總管** 中，以滑鼠右鍵按一下 [WCF 服務程式庫] 專案，然後按一下 [ **建立**]。

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>透過遠端桌面存取服務時發生錯誤

當使用者透過遠端桌面連線存取 Web 主控的 WCF 服務，而且使用者沒有系統管理許可權時，就會使用 NTLM 驗證。 如果使用者沒有系統管理許可權，則使用者可能會收到下列錯誤訊息：「HTTP 要求未經授權使用用戶端驗證配置 ' Anonymous '。 從伺服器收到的驗證標頭為「NTLM」。」

若要修正此錯誤：

1. 在網站專案中，開啟 [ **屬性** ] 頁面。

2. 在 [ **開始選項** ] 索引標籤上，清除 [ **NTLM 驗證** ] 核取方塊。

    > [!NOTE]
    > 您應該只針對僅包含 WCF 服務的網站關閉 NTLM 驗證。 WCF 服務的安全性是透過 *web.config* 檔案中的設定來管理。 這樣就不需要 NTLM 驗證。

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>產生之類別的存取層級設定沒有任何作用

將 [設定 **服務參考**] 對話方塊中的 [**產生類別的存取層級**] 選項設定為 [**內部**] 或 [ **Friend** ]，可能不一定會有效。 即使此選項顯示在對話方塊中，但產生的支援類別是以的存取層級來產生的 `Public` 。

這是特定類型的已知限制，例如使用進行序列化的特定類型 <xref:System.Xml.Serialization.XmlSerializer> 。

## <a name="error-debugging-service-code"></a>偵測服務程式代碼時發生錯誤

當您從用戶端程式代碼逐步執行 WCF 服務的程式碼時，可能會收到與遺失符號相關的錯誤。 當您解決方案中的服務已從方案中移動或移除時，就會發生這種情況。

當您第一次將參考加入至目前方案中的 WCF 服務時，會在服務專案與服務用戶端專案之間加入明確的組建相依性。 這可保證用戶端一律會存取最新的服務二進位檔，這對於在將用戶端程式代碼逐步執行至服務程式代碼的情況下特別重要。

如果從方案中移除服務專案，這個明確的組建相依性就會失效。 Visual Studio 無法再保證服務專案會在必要時重建。

若要修正這個錯誤，您必須手動重建服務專案：

1. 在 **[工具]** 功能表上，按一下 **[選項]** 。

2. 在 [ **選項** ] 對話方塊中，展開 [ **專案和方案**]，然後選取 **[一般**]。

3. 確定已選取 [ **顯示 advanced build** 設定] 核取方塊，然後按一下 **[確定]**。

4. 載入 WCF 服務專案。

5. 在 [ **設定管理員** ] 對話方塊中，將 [使用中的 **方案** 設定] 設定為 [ **Debug**]。 如需詳細資訊，請參閱 [如何：建立和編輯](../ide/how-to-create-and-edit-configurations.md)設定。

6. 在 **方案總管** 中，選取 [WCF 服務] 專案。

7. 在 [ **組建** ] 功能表上，按一下 [ **重建** ] 以重建 WCF 服務專案。

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services 不會顯示在瀏覽器中

當它嘗試在中查看資料的 XML 標記法時 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] ，Internet Explorer 可能會將資料誤譯為 rss 摘要。 請確定顯示 RSS 摘要的選項已停用。

若要修正這個錯誤，請停用 RSS 摘要：

1. 在 Internet Explorer 的 [工具] 功能表，按一下 [網際網路選項]。

2. 在 [ **內容** ] 索引標籤 **的 [摘要] 區段中** ，按一下 [ **設定**]。

3. 在 [摘要 **設定** ] 對話方塊中，清除 [ **開啟摘要閱讀檢視** ] 核取方塊，然後按一下 **[確定]**。

4. 按一下 **[確定** ]，以關閉 [ **網際網路選項** ] 對話方塊。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
