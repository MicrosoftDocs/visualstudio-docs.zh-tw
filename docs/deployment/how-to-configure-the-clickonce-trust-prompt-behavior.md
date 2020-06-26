---
title: 如何-設定 ClickOnce 信任提示行為 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7417f9cdce21dc09aeaf306b55834ad7d3a125a6
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382545"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>如何：設定 ClickOnce 信任提示行為
您可以設定 ClickOnce 信任提示，以控制是否提供使用者安裝 ClickOnce 應用程式的選項，例如 Windows Forms 應用程式、Windows Presentation Foundation 應用程式、主控台應用程式、WPF 瀏覽器應用程式和 Office 方案。 您可以藉由在每個使用者的電腦上設定登錄機碼，來設定信任提示。

 下表顯示可套用至五個區域（Internet、UntrustedSites、MyComputer、LocalIntranet 和 TrustedSites）的設定選項。

|選項|登錄設定值|描述|
|------------|----------------------------|-----------------|
|啟用信任提示。|`Enabled`|隨即顯示 ClickOnce 信任提示，讓終端使用者可以將信任授與 ClickOnce 應用程式。|
|限制信任提示。|`AuthenticodeRequired`|只有在使用可識別發行者的憑證簽署 ClickOnce 應用程式時，才會顯示 ClickOnce 信任提示。|
|停用信任提示。|`Disabled`|不是以明確信任的憑證簽署的任何 ClickOnce 應用程式，都不會顯示 ClickOnce 信任提示。|

 下表顯示每個區域的預設行為。 [應用程式] 資料行指的是 Windows Forms 應用程式、Windows Presentation Foundation 應用程式、WPF 瀏覽器應用程式和主控台應用程式。

|區域|應用程式|Office 方案|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 您可以藉由啟用、限制或停用 ClickOnce 信任提示來覆寫這些設定。

## <a name="enable-the-clickonce-trust-prompt"></a>啟用 ClickOnce 信任提示
 當您想要讓使用者看到安裝和執行來自該區域之任何 ClickOnce 應用程式的選項時，請啟用該區域的信任提示。

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>使用登錄編輯程式啟用 ClickOnce 信任提示

1. 開啟 [登錄編輯程式]：

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 [**開啟**] 方塊中，輸入 `regedit` ，然後按一下 **[確定]**。

2. 尋找下列登錄機碼：

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     如果機碼不存在，請加以建立。

3. 將下列子機碼新增為**字串值**（如果尚未存在），其相關聯的值如下表所示。

    |字串值子機碼|值|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     針對 Office 方案， `Internet` 具有預設值 `AuthenticodeRequired` ，而且 `UntrustedSites` 具有值 `Disabled` 。 對於所有其他專案， `Internet` 則具有預設值 `Enabled` 。

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>以程式設計方式啟用 ClickOnce 信任提示

1. 在 Visual Studio 中建立 Visual Basic 或 Visual c # 主控台應用程式。

2. 開啟*程式 .vb*或*Program.cs*檔案進行編輯，並加入下列程式碼。

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

3. 建置並執行應用程式。

## <a name="restrict-the-clickonce-trust-prompt"></a>限制 ClickOnce 信任提示
 限制信任提示，以便在系統提示使用者提供信任決策之前，必須以具有已知身分識別的 Authenticode 憑證簽署解決方案。

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>使用登錄編輯程式來限制 ClickOnce 信任提示

1. 開啟 [登錄編輯程式]：

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 [**開啟**] 方塊中，輸入 `regedit` ，然後按一下 **[確定]**。

2. 尋找下列登錄機碼：

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     如果機碼不存在，請加以建立。

3. 將下列子機碼新增為**字串值**（如果尚未存在），其相關聯的值如下表所示。

    |字串值子機碼|值|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>以程式設計方式限制 ClickOnce 信任提示

1. 在 Visual Studio 中建立 Visual Basic 或 Visual c # 主控台應用程式。

2. 開啟*程式 .vb*或*Program.cs*檔案進行編輯，並加入下列程式碼。

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

3. 建置並執行應用程式。

## <a name="disable-the-clickonce-trust-prompt"></a>停用 ClickOnce 信任提示
 您可以停用信任提示，讓終端使用者無法選擇安裝其安全性原則中尚未信任的解決方案。

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>使用登錄編輯程式停用 ClickOnce 信任提示

1. 開啟 [登錄編輯程式]：

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 [**開啟**] 方塊中，輸入 `regedit` ，然後按一下 **[確定]**。

2. 尋找下列登錄機碼：

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     如果機碼不存在，請加以建立。

3. 將下列子機碼新增為**字串值**（如果尚未存在），其相關聯的值如下表所示。

    |字串值子機碼|值|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>以程式設計方式停用 ClickOnce 信任提示

1. 在 Visual Studio 中建立 Visual Basic 或 Visual c # 主控台應用程式。

2. 開啟*程式 .vb*或*Program.cs*檔案進行編輯，並加入下列程式碼。

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

3. 建置並執行應用程式。

## <a name="see-also"></a>另請參閱
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)
- [信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)
- [How to: Enable ClickOnce security settings (如何：啟用 ClickOnce 安全性設定)](../deployment/how-to-enable-clickonce-security-settings.md)
- [如何：設定 ClickOnce 應用程式的安全性區域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [How to: Set custom permissions for a ClickOnce application (如何：設定 ClickOnce 應用程式的自訂權限)](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [如何：以限制的許可權對 ClickOnce 應用程式進行 Debug](securing-clickonce-applications.md)
- [如何：將新增信任的發行者新增至 ClickOnce 應用程式的用戶端電腦](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
