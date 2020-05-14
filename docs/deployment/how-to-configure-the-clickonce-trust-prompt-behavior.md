---
title: 如何:配置點擊信任提示行為 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ec5f1cca49f1b799b39969849e0a73bf1e6e296d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649163"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>如何：設定 ClickOnce 信任提示行為
您可以設定 ClickOnce 信任提示,以控制是否允許最終使用者選擇安裝 ClickOnce 應用程式,例如 Windows 窗體應用程式、Windows 演示文稿基礎應用程式、控制台應用程式、WPF 瀏覽器應用程式和 Office 解決方案。 通過在每個最終用戶的計算機上設置註冊表項來配置信任提示。

 下表顯示了可應用於五個區域(Internet、不受信任的網站、MyComputer、本地 Intranet 和受信任的網站)中的每個區域的配置選項。

|選項|登錄表設定值|描述|
|------------|----------------------------|-----------------|
|啟用信任提示。|`Enabled`|將顯示「按一次信任」提示,以便最終使用者可以信任 ClickOnce 應用程式。|
|限制信任提示。|`AuthenticodeRequired`|僅當 ClickOnce 應用程式使用標識發佈者的證書進行簽名時,才會顯示 ClickOnce 信任提示。|
|禁用信任提示。|`Disabled`|對於未使用顯式受信任的證書簽名的任何 ClickOnce 應用程式,不會顯示 ClickOnce 信任提示。|

 下表顯示了每個區域的默認行為。 "應用程式"列是指 Windows 表單應用程式、Windows 演示文稿基礎應用程式、WPF 瀏覽器應用程式和控制台應用程式。

|區域|應用程式|Office 方案|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 您可以通過啟用、限制或禁用「按下」信任提示來覆蓋這些設定。

## <a name="enable-the-clickonce-trust-prompt"></a>開啟「按下次數」信任提示
 當您希望向最終使用者顯示安裝和運行來自該區域的任何 ClickOnce 應用程式的選項時,啟用區域的信任提示。

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>使用註冊表編輯器啟用 ClickOnce 信任提示

1. 開啟註冊表編輯器:

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 **"打開"** 框`regedit`中, 鍵入 ,然後按一下 **「 確定**」。

2. 尋找以下註冊表項:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     如果金鑰不存在,請創建它。

3. 如果子鍵不存在,則將以下子鍵添加為**字串值**,並顯示下表中的關聯值。

    |字串值子鍵|值|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     對於`Internet`Office 解決方案,具有`AuthenticodeRequired`預設`UntrustedSites`值,`Disabled`並且具有值 。 為所有其他,`Internet`具有預設`Enabled`值 。

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>以程式設計方式啟用「按下次數」信任提示

1. 在可視化工作室中創建視覺化基本或可視化C++控制台應用程式。

2. 開啟*程式.vb*或*Program.cs*檔案進行編輯並添加以下代碼。

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

## <a name="restrict-the-clickonce-trust-prompt"></a>限制按一下信任提示
 限制信任提示,以便在提示使用者做出信任決策之前,必須使用具有已知標識的身份驗證證書對解決方案進行簽名。

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>使用註冊表編輯器限制 ClickOnce 信任提示

1. 開啟註冊表編輯器:

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 **"打開"** 框`regedit`中, 鍵入 ,然後按一下 **「 確定**」。

2. 尋找以下註冊表項:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     如果金鑰不存在,請創建它。

3. 如果子鍵不存在,則將以下子鍵添加為**字串值**,並顯示下表中的關聯值。

    |字串值子鍵|值|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>以程式設計方式限制按一下信任提示

1. 在可視化工作室中創建視覺化基本或可視化C++控制台應用程式。

2. 開啟*程式.vb*或*Program.cs*檔案進行編輯並添加以下代碼。

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

## <a name="disable-the-clickonce-trust-prompt"></a>禁用「按一次信任提示」
 您可以關閉信任提示,以便最終使用者不會選擇安裝其安全原則中尚未信任的解決方案。

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>使用註冊表編輯器禁用 ClickOnce 信任提示

1. 開啟註冊表編輯器:

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 **"打開"** 框`regedit`中, 鍵入 ,然後按一下 **「 確定**」。

2. 尋找以下註冊表項:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     如果金鑰不存在,請創建它。

3. 如果子鍵不存在,則將以下子鍵添加為**字串值**,並顯示下表中的關聯值。

    |字串值子鍵|值|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>以程式設計方式關閉「按一下次數」信任提示

1. 在可視化工作室中創建視覺化基本或可視化C++控制台應用程式。

2. 開啟*程式.vb*或*Program.cs*檔案進行編輯並添加以下代碼。

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
- [如何:除錯具有受限權限的 ClickOnce 應用程式](securing-clickonce-applications.md)
- [如何：將新增信任的發行者新增至 ClickOnce 應用程式的用戶端電腦](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
