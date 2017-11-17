---
title: "如何： 設定 ClickOnce 信任提示行為 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 24a229c7c96221c0b7f04a91d5f71fa566e71e81
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>如何：設定 ClickOnce 信任提示行為
您可以設定 ClickOnce 信任提示，來控制，是否可以選擇安裝 ClickOnce 應用程式，例如 Windows Forms 應用程式、 Windows Presentation Foundation 應用程式、 主控台應用程式、 WPF 瀏覽器的使用者。應用程式和 Office 方案。 您可以設定每位使用者的電腦上的登錄機碼設定信任提示。  
  
 下表顯示可以套用到每一個這五個區域 （網際網路、 UntrustedSites、 MyComputer、 近端內部網路和 TrustedSites） 的組態選項。  
  
|選項|登錄設定值|描述|  
|------------|----------------------------|-----------------|  
|啟用信任提示。|`Enabled`|ClickOnce 信任提示會顯示，讓使用者可以授與信任給 ClickOnce 應用程式。|  
|限制信任提示。|`AuthenticodeRequired`|只有使用的憑證來識別 「 發行者 」 經過簽署的 ClickOnce 應用程式時，才會顯示 ClickOnce 信任提示。|  
|停用信任提示。|`Disabled`|任何未使用明確受信任的憑證簽署的 ClickOnce 應用程式不會顯示 ClickOnce 信任提示。|  
  
 下表顯示每個區域的預設行為。 應用程式的資料行是指 Windows Forms 應用程式、 Windows Presentation Foundation 應用程式、 WPF 瀏覽器應用程式和主控台應用程式。  
  
|區域|應用程式|Office 方案|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 您可以啟用、 限制，或停用 ClickOnce 信任提示來覆寫這些設定。  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>啟用 ClickOnce 信任提示  
 當您想讓使用者安裝及執行任何來自該區域的 ClickOnce 應用程式的選項會呈現時，請啟用信任提示區域。  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>若要使用登錄編輯程式中啟用 ClickOnce 信任提示  
  
1.  開啟登錄編輯程式：  
  
    1.  按一下**啟動**，然後按一下 **執行**。  
  
    2.  在**開啟**方塊中，輸入`regedit32`，然後按一下 **確定**。  
  
2.  尋找下列登錄機碼：  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\。NETFramework\Security\TrustManager\PromptingLevel  
  
     如果索引鍵不存在，建立它。  
  
3.  新增下列子機碼為**字串值**，如果它們尚不存在，使用下表所示的關聯值。  
  
    |字串值的子機碼|值|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Office 方案的`Internet`預設值`AuthenticodeRequired`和`UntrustedSites`值`Disabled`。 對於所有其他人，`Internet`預設值`Enabled`。  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>若要以程式設計方式啟用 ClickOnce 信任提示  
  
1.  Visual Studio 中建立 Visual Basic 或 Visual C# 主控台應用程式。  
  
2.  開啟 Program.vb 或 Program.cs 檔案進行編輯並加入下列程式碼。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## <a name="restricting-the-clickonce-trust-prompt"></a>限制 ClickOnce 信任提示  
 限制信任提示，讓解決方案必須以提示使用者信任決策之前有已知識別的 Authenticode 憑證簽署。  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>若要限制 ClickOnce 信任提示，使用登錄編輯程式  
  
1.  開啟登錄編輯程式：  
  
    1.  按一下**啟動**，然後按一下 **執行**。  
  
    2.  在**開啟**方塊中，輸入`regedit`，然後按一下 **確定**。  
  
2.  尋找下列登錄機碼：  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\。NETFramework\Security\TrustManager\PromptingLevel  
  
     如果索引鍵不存在，建立它。  
  
3.  新增下列子機碼為**字串值**，如果它們尚不存在，使用下表所示的關聯值。  
  
    |字串值的子機碼|值|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>若要以程式設計的方式限制 ClickOnce 信任提示  
  
1.  Visual Studio 中建立 Visual Basic 或 Visual C# 主控台應用程式。  
  
2.  開啟 Program.vb 或 Program.cs 檔案進行編輯並加入下列程式碼。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## <a name="disabling-the-clickonce-trust-prompt"></a>停用 ClickOnce 信任提示  
 您可以停用信任提示，讓一般使用者系統不會提供安裝已經不信任其安全性原則中的解決方案的選項。  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>使用登錄編輯程式停用 ClickOnce 信任提示  
  
1.  開啟登錄編輯程式：  
  
    1.  按一下**啟動**，然後按一下 **執行**。  
  
    2.  在**開啟**方塊中，輸入`regedit`，然後按一下 **確定**。  
  
2.  尋找下列登錄機碼：  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\。NETFramework\Security\TrustManager\PromptingLevel  
  
     如果索引鍵不存在，建立它。  
  
3.  新增下列子機碼為**字串值**，如果它們尚不存在，使用下表所示的關聯值。  
  
    |字串值的子機碼|值|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>若要以程式設計的方式停用 ClickOnce 信任提示  
  
1.  Visual Studio 中建立 Visual Basic 或 Visual C# 主控台應用程式。  
  
2.  開啟 Program.vb 或 Program.cs 檔案進行編輯並加入下列程式碼。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## <a name="see-also"></a>另請參閱  
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)   
 [如何： 啟用 ClickOnce 安全性設定](../deployment/how-to-enable-clickonce-security-settings.md)   
 [如何： 設定 ClickOnce 應用程式的安全性區域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [如何： 偵錯 ClickOnce 應用程式，以限制權限](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [如何： 新增 ClickOnce 應用程式的用戶端電腦信任的發行者](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)