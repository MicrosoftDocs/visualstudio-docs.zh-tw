---
title: "如何：設定 ClickOnce 信任提示行為 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 應用程式, 不用提示直接安裝"
  - "ClickOnce 應用程式, 信任提示"
  - "ClickOnce 部署, 不用提示直接安裝"
  - "ClickOnce 部署, 信任提示"
  - "部署應用程式 [ClickOnce], 信任提示"
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：設定 ClickOnce 信任提示行為
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以設定 ClickOnce 信任提示以控制是否向使用者提供安裝 ClickOnce 應用程式的選項，例如 Windows Forms 應用程式、Windows Presentation Foundation 應用程式、主控台應用程式、WPF 瀏覽器應用程式和 Office 方案。  透過在每位使用者的電腦上設定登錄機碼來設定信任提示。  
  
 下表顯示可以套用至五個區域的組態選項 \(Internet、UntrustedSites、MyComputer、LocalIntranet 和 TrustedSites\)。  
  
|選項|登錄設定值|描述|  
|--------|-----------|--------|  
|啟用信任提示。|`Enabled`|顯示 ClickOnce 信任提示，以讓使用者將信任授與 ClickOnce 應用程式。|  
|限制信任提示。|`AuthenticodeRequired`|只有以識別發行者的憑證來簽署 ClickOnce 應用程式時，才會顯示 ClickOnce 信任提示。|  
|停用信任提示。|`Disabled`|對於未明確使用信任憑證簽署的任何 ClickOnce 應用程式，不會顯示 ClickOnce 信任提示。|  
  
 下表顯示每個區域的預設行為。  「應用程式」資料行是指 Windows Forms 應用程式、Windows Presentation Foundation 應用程式、WPF 瀏覽器應用程式和主控台應用程式。  
  
|區域|應用程式|Office 方案|  
|--------|----------|---------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`近端內部網路`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`網際網路`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 您可以透過啟用、限制或停用 ClickOnce 信任提示來覆寫這些設定。  
  
## 啟用 ClickOnce 信任提示  
 當您希望對使用者顯示安裝和執行來自某區域之任何 ClickOnce 應用程式的選項時，請啟用該區域的信任提示。  
  
#### 若要使用登錄編輯程式啟用 ClickOnce 信任提示  
  
1.  開啟登錄編輯器：  
  
    1.  按一下 \[**開始**\]，再按一下 \[**執行**\]。  
  
    2.  在 \[**開啟**\] 方塊中，輸入 `regedit32`，然後按下 \[**確定**\]。  
  
2.  尋找下列登錄機碼：  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     如果機碼不存在，請加以建立。  
  
3.  請加入下列子機碼做為 \[**字串值**\] \(如果沒有的話\)，並且加入下表中的關聯值。  
  
    |字串值子機碼|值|  
    |------------|-------|  
    |`網際網路`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`近端內部網路`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     對於 Office 方案來說，`Internet` 的預設值為 `AuthenticodeRequired`，而 `UntrustedSites` 的值為 `Disabled`。  對於所有其他方案來說，`Internet` 的預設值為 `Enabled`。  
  
#### 若要以程式設計的方式啟用 ClickOnce 信任提示  
  
1.  在 Visual Studio 中建立 Visual Basic 或 Visual C\# 主控台應用程式。  
  
2.  開啟 Program.vb 或 Program.cs 檔案以進行編輯，然後加入下列程式碼。  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  建置並執行應用程式。  
  
## 限制 ClickOnce 信任提示  
 限制信任提示，以在確認方案已用具有已知識別的 Authenticode 憑證來簽署之後，才提示使用者決定是否信任。  
  
#### 若要使用登錄編輯程式限制 ClickOnce 信任提示  
  
1.  開啟登錄編輯器：  
  
    1.  按一下 \[**開始**\]，再按一下 \[**執行**\]。  
  
    2.  在 \[**開啟**\] 方塊中，輸入 `regedit`，然後按下 \[**確定**\]。  
  
2.  尋找下列登錄機碼：  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     如果機碼不存在，請加以建立。  
  
3.  請加入下列子機碼做為 \[**字串值**\] \(如果沒有的話\)，並且加入下表中的關聯值。  
  
    |字串值子機碼|值|  
    |------------|-------|  
    |`UntrustedSites`|`Disabled`|  
    |`網際網路`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`近端內部網路`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### 若要以程式設計的方式限制 ClickOnce 信任提示  
  
1.  在 Visual Studio 中建立 Visual Basic 或 Visual C\# 主控台應用程式。  
  
2.  開啟 Program.vb 或 Program.cs 檔案以進行編輯，然後加入下列程式碼。  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  建置並執行應用程式。  
  
## 停用 ClickOnce 信任提示  
 您可以停用信任提示，以便不向使用者提供安裝尚未在安全性原則中受信任之方案的選項。  
  
#### 若要使用登錄編輯程式停用 ClickOnce 信任提示  
  
1.  開啟登錄編輯器：  
  
    1.  按一下 \[**開始**\]，再按一下 \[**執行**\]。  
  
    2.  在 \[**開啟**\] 方塊中，輸入 `regedit`，然後按下 \[**確定**\]。  
  
2.  尋找下列登錄機碼：  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     如果機碼不存在，請加以建立。  
  
3.  請加入下列子機碼做為 \[**字串值**\] \(如果沒有的話\)，並且加入下表中的關聯值。  
  
    |字串值子機碼|值|  
    |------------|-------|  
    |`UntrustedSites`|`Disabled`|  
    |`網際網路`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`近端內部網路`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### 若要以程式設計的方式停用 ClickOnce 信任提示  
  
1.  在 Visual Studio 中建立 Visual Basic 或 Visual C\# 主控台應用程式。  
  
2.  開啟 Program.vb 或 Program.cs 檔案以進行編輯，然後加入下列程式碼。  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  建置並執行應用程式。  
  
## 請參閱  
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)   
 [如何：啟用 ClickOnce 安全性設定](../deployment/how-to-enable-clickonce-security-settings.md)   
 [如何：設定 ClickOnce 應用程式的安全性區域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [如何：設定 ClickOnce 應用程式的自訂使用權限](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [如何：以限制使用權限偵錯 ClickOnce 應用程式](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [如何：新增信任發行者至 ClickOnce 應用程式的用戶端電腦](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)