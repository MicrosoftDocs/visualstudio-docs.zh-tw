---
title: "Troubleshooting Service References | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther"
  - "msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo"
  - "msvse_wcf.Err.ErrorOnOK"
  - "msvse_wcf.cfg.ConfigurationErrorsException"
helpviewer_keywords: 
  - "service references [Visual Studio], troubleshooting"
  - "WCF services, troubleshooting"
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Troubleshooting Service References
本主題列出在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] 或 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 參考時可能發生的常見問題。  
  
## 從服務傳回資料時發生錯誤  
 當您從服務傳回 `DataSet` 或 `DataTable` 時，可能會收到「超出傳入訊息的訊息大小配額上限」例外狀況。  根據預設，某些繫結的 `MaxReceivedMessageSize` 屬性會設定為相對而言較小的值，以降低阻絕服務攻擊的危險。  您可以增加此值以避免出現例外狀況。  如需詳細資訊，請參閱 <xref:System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize%2A>。  
  
 若要更正這個錯誤：  
  
1.  在 \[**方案總管**\] 中，按兩下以開啟 app.config 檔。  
  
2.  找出 `MaxReceivedMessageSize` 屬性，並將它變更為較大的值。  
  
## 在我的方案中找不到服務  
 當您按一下 \[**加入服務參考**\] 對話方塊中的 \[**探索**\] 按鈕時，方案中的一個或多個 WCF 服務庫專案沒有顯示在服務清單中。  如果服務庫已加入至方案，但尚未編譯，就會發生此錯誤。  
  
 若要更正這個錯誤：  
  
-   在 \[**方案總管**\] 中，以滑鼠右鍵按一下該 WCF 服務庫專案，然後按一下 \[**建置**\]。  
  
## 透過遠端桌面存取服務時發生錯誤  
 當使用者透過遠端桌面連線存取 Web 裝載的 WCF 服務，而且使用者沒有系統管理權限時，則會使用 NTLM 驗證。  如果使用者沒有系統管理權限，就會收到下列錯誤訊息：「HTTP 要求未經用戶端驗證配置 'Anonymous' 的授權。  接收自伺服器的驗證標頭為 'NTLM'」。  
  
 若要更正這個錯誤：  
  
1.  在網站專案中，開啟 \[**屬性**\] 頁面。  
  
2.  清除 \[**起始選項**\] 索引標籤中的 \[**NTLM 驗證**\] 核取方塊。  
  
    > [!NOTE]
    >  針對只包含 WCF 服務的網站，才應關閉 NTLM 驗證。  WCF 服務的安全性是透過 web.config 檔案中的組態來管理。  因此，不需要 NTLM 驗證。  
  
 如需詳細資訊，請參閱[疑難排解例外狀況：System.ServiceModel.Security.MessageSecurityException](../misc/troubleshooting-exceptions-system-servicemodel-security-messagesecurityexception.md)。  
  
## 產生之類別設定的存取層級沒有作用  
 將 \[**設定服務參考**\] 對話方塊中的 \[**產生的類別的存取層級**\] 選項設定為 \[**內部**\] 或 \[**Friend**\] 不一定都有作用。  即使在對話方塊中已設定選項，產生的支援類別仍會具有 `Public` 存取層級。  
  
 這是特定型別的已知限制，例如使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化的型別。  
  
## 偵錯服務程式碼時發生錯誤  
 當您從用戶端程式碼逐步執行 WCF 服務的程式碼時，可能會接到與遺失符號相關的錯誤。  當屬於方案一部分的服務移至他處或從方案移除時，便可能會發生這個錯誤。  
  
 當您一開始加入屬於目前方案一部分之 WCF 服務的參考時，會在服務專案和服務用戶端專案之間加入明確的組建相依性。  這可確保用戶端永遠存取最新的服務二進位檔，這對於像是從用戶端程式碼逐步執行服務程式碼之類的偵錯案例而言特別重要。  
  
 如果服務專案已從方案移除，此明確組建相依性就會變成無效。  Visual Studio 無法再保證服務專案會依所需重建。  
  
 若要修正此錯誤，您必須手動重建服務專案：  
  
1.  在 \[**工具**\] 功能表上按一下 \[**選項**\]。  
  
2.  在 \[**選項**\] 對話方塊中，展開 \[**專案和方案**\]，然後選取 \[**一般**\]。  
  
3.  確定已經選取 \[**顯示進階組建組態**\] 核取方塊，然後按一下 \[**確定**\]。  
  
4.  載入 WCF 服務專案。  如需詳細資訊，請參閱 [如何：建立多專案的方案](http://msdn.microsoft.com/zh-tw/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)。  
  
5.  在 \[**組態管理員**\] 對話方塊中，將 \[**使用中的方案組態**\] 設定為 \[**偵錯**\]。  如需詳細資訊，請參閱 [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)。  
  
6.  在 \[**方案總管**\] 中，選取 WCF 服務專案。  
  
7.  在 \[**建置**\] 功能表上，按一下 \[**重建**\] 來重建 WCF 服務專案。  
  
## 瀏覽器中未顯示 WCF 資料服務  
 當它嘗試在 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]中檢視資料的 XML 表示時，Internet Explorer 可能會將資料錯誤解譯為 RSS 摘要。  您必須確定顯示 RSS 饋送的選項已停用。  
  
 若要修正此錯誤，請停用 RSS 饋送：  
  
1.  在 Internet Explorer 的 \[**工具**\] 功能表上，按一下 \[**網際網路選項**\]。  
  
2.  在 \[**內容**\] 索引標籤的 \[**摘要**\] 區段中，按一下 \[**設定**\]。  
  
3.  在 \[**摘要設定**\] 對話方塊中，清除 \[**啟動摘要讀取檢視**\] 核取方塊，然後按一下 \[**確定**\]。  
  
4.  按一下 \[**確定**\]，關閉 \[**網際網路選項**\] 對話方塊。  
  
## 請參閱  
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Consuming ASMX and WCF Services Sample](http://msdn.microsoft.com/zh-tw/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)