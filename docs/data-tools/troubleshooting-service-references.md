---
title: "疑難排解服務參考 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: e46c8bf778ff18ea25096e524716bcb44916f460
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-service-references"></a>服務參考的疑難排解
本主題列出常見的問題，當您正在使用時，可能會發生[!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]或[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]參考[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="error-returning-data-from-a-service"></a>傳回從服務的資料時發生錯誤  
 當您傳回`DataSet`或`DataTable`從服務中，您可能會收到 「 已超過傳入訊息的大小上限配額 」 的例外狀況。 根據預設，`MaxReceivedMessageSize`某些繫結的屬性設定為相對較小的值來限制暴露於阻絕服務攻擊。 您可以增加此值，以避免這個例外狀況。 如需詳細資訊，請參閱<xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>。  
  
 若要修正這個錯誤：  
  
1.  在**方案總管 中**，按兩下 app.config 檔案，將它開啟。  
  
2.  找出`MaxReceivedMessageSize`屬性並將它變更為較大的值。  
  
## <a name="cannot-find-a-service-in-my-solution"></a>在 我的方案中找不到服務  
 當您按一下**探索**按鈕**加入服務參考**對話方塊中，方案中的一個或多個 WCF 服務程式庫專案不會出現在 [服務] 清單中。 如果服務程式庫已加入至方案，但尚未編譯，這可能會發生。  
  
 若要修正這個錯誤：  
  
-   在**方案總管 中**，以滑鼠右鍵按一下 WCF 服務程式庫專案，然後按一下**建置**。  
  
## <a name="error-accessing-a-service-over-a-remote-desktop"></a>透過遠端桌面存取服務時發生錯誤  
 當使用者存取的 Web 裝載的 WCF 服務，透過遠端桌面連線和使用者沒有系統管理權限，則使用 NTLM 驗證。 如果使用者沒有系統管理權限，使用者可能會收到下列錯誤訊息: 「 HTTP 要求是未經授權的用戶端驗證配置 'Anonymous'。 從伺服器收到的驗證標頭 'NTLM'。 」  
  
 若要修正這個錯誤：  
  
1.  在網站專案中，開啟**屬性**頁面。  
  
2.  在**起始選項**索引標籤上，清除**NTLM 驗證**核取方塊。  
  
    > [!NOTE]
    >  您應該關閉 NTLM 驗證只有針對只包含 WCF 服務的網站。 WCF 服務的安全性是透過 web.config 檔案中的組態管理。 這可讓 NTLM 驗證的非必要。  
  
## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>產生的類別存取層級設定沒有任何作用  
 設定**存取產生的類別層級**選項**設定服務參考**對話方塊**內部**或**Friend**未必可行。 即使與選項出現在對話方塊中設定，將會產生的支援類別產生的存取層級`Public`。  
  
 這是特定的類型，例如使用序列化的已知的限制<xref:System.Xml.Serialization.XmlSerializer>。  
  
## <a name="error-debugging-service-code"></a>偵錯服務錯誤碼  
 當您從用戶端程式碼逐步執行 WCF 服務的程式碼時，您可能會收到遺失符號相關的錯誤。 發生這個問題的服務方案的一部分已移動，或從方案中移除。  
  
 當您初次加入至目前方案的一部分的 WCF 服務的參考時，在服務專案和服務用戶端專案之間加上明確組建相依性。 這可確保用戶端一律會存取最新的服務二進位檔，這是特別重要的案例，例如從用戶端程式碼逐步執行服務的程式碼偵錯。  
  
 如果從方案移除的服務專案時，此明確的組建相依性會失效。 Visual Studio 無法再保證會重建服務專案，在必要時。  
  
 若要修正這個錯誤，您必須手動重建服務專案：  
  
1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2.  在**選項**對話方塊方塊中，展開 **專案和方案**，然後選取**一般**。  
  
3.  請確定**顯示進階組建組態**核取方塊已選取，然後按一下 **確定**。  
  
4.  載入 WCF 服務專案。  
  
5.  在**Configuration Manager**  對話方塊中，將**現用方案組態**至**偵錯**。 如需詳細資訊，請參閱[如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)。  
  
6.  在**方案總管] 中**，選取 [WCF 服務專案。  
  
7.  在**建置**功能表上，按一下 **重建**重建 WCF 服務專案。  
  
## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF 資料服務不會顯示在瀏覽器  
 當它嘗試檢視中資料的 XML 表示法[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]，Internet Explorer 可能會錯誤解譯為 RSS 摘要的資料。 您必須確定顯示 RSS 摘要的選項已停用。  
  
 若要修正這個錯誤，請停用 RSS 摘要：  
  
1.  在 Internet Explorer 上**工具**功能表上，按一下 **網際網路選項**。  
  
2.  在**內容**索引標籤的**摘要**區段中，按一下**設定**。  
  
3.  在**摘要設定**對話方塊中，清除**開啟摘要讀取檢視**核取方塊，然後**確定**。  
  
4.  按一下**確定**關閉**網際網路選項** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)