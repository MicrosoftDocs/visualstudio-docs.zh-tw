---
title: 如何：設定包含清單安全性
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 459cf3f33197939a916a5f11a94bbaf09e8142e3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541631"
---
# <a name="how-to-configure-inclusion-list-security"></a>如何：設定包含清單安全性
  如果您具有系統管理員許可權，您可以設定 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示，以控制使用者是否能透過將信任決策儲存至包含清單的方式來安裝 Office 方案。 如需包含清單的相關資訊，請參閱[使用內含清單信任 Office 方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 針對每五個區域中的解決方案，您可以設定下列選項：

- 啟用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示金鑰和包含清單。 您可以讓終端使用者將信任授與以任何憑證簽署的 Office 方案。

- 限制 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示金鑰和包含清單。 您可以讓使用者安裝使用可識別發行者但尚未受信任的憑證簽署的 Office 方案。

- 停用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示金鑰和包含清單。 您可以防止終端使用者安裝未使用明確信任的憑證簽署的任何 Office 方案。

## <a name="enable-the-inclusion-list"></a>啟用包含清單
 當您想要讓使用者看到安裝和執行來自該區域的任何 Office 解決方案的選項時，請啟用該區域的包含清單。

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>使用登錄編輯程式啟用包含清單

1. 開啟 [登錄編輯程式]：

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 [**開啟**] 方塊中，輸入**regedt32.exe**，然後按一下 **[確定]**。

2. 尋找下列登錄機碼：

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     如果機碼不存在，請加以建立。

3. 將下列子機碼新增為**字串值**（如果尚未存在的話）與相關聯的值。

    |字串值子機碼|值|
    |-------------------------|-----------|
    |**網際網路**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Disabled**|
    |**MyComputer**|**已啟用**|
    |**LocalIntranet**|**已啟用**|
    |**TrustedSites**|**已啟用**|

     根據預設， **Internet**的值為**AuthenticodeRequired** ，而**UntrustedSites**的值為**Disabled**。

### <a name="to-enable-the-inclusion-list-programmatically"></a>以程式設計方式啟用包含清單

1. 建立 Visual Basic 或 Visual c # 主控台應用程式。

2. 開啟*程式 .vb*或*Program.cs*檔案進行編輯，並加入下列程式碼。

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "AuthenticodeRequired")
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

## <a name="restrict-the-inclusion-list"></a>限制包含清單
 限制包含清單，以便在系統提示使用者提供信任決策之前，必須使用具有已知身分識別的 Authenticode 憑證來簽署解決方案。

### <a name="to-restrict-the-inclusion-list"></a>限制包含清單

1. 開啟 [登錄編輯程式]：

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 [**開啟**] 方塊中，輸入**regedt32.exe**，然後按一下 **[確定]**。

2. 尋找下列登錄機碼：

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     如果機碼不存在，請加以建立。

3. 將下列子機碼新增為**字串值**（如果尚未存在的話）與相關聯的值。

    |字串值子機碼|值|
    |-------------------------|-----------|
    |**UntrustedSites**|**Disabled**|
    |**網際網路**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     根據預設， **Internet**的值為**AuthenticodeRequired** ，而**UntrustedSites**的值為**Disabled**。

### <a name="to-restrict-the-inclusion-list-programmatically"></a>以程式設計方式限制包含清單

1. 建立 Visual Basic 或 Visual c # 主控台應用程式。

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

## <a name="disable-the-inclusion-list"></a>停用包含清單
 您可以停用包含清單，讓終端使用者只能安裝使用受信任的憑證和已知憑證簽署的解決方案。

### <a name="to-disable-the-inclusion-list"></a>停用包含清單

1. 開啟 [登錄編輯程式]：

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 [**開啟**] 方塊中，輸入**regedt32.exe**，然後按一下 **[確定]**。

2. 建立下列登錄機碼（如果尚未存在）：

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

3. 將下列子機碼新增為**字串值**（如果尚未存在的話）與相關聯的值。

    |字串值子機碼|值|
    |-------------------------|-----------|
    |**UntrustedSites**|**Disabled**|
    |**網際網路**|**Disabled**|
    |**MyComputer**|**Disabled**|
    |**LocalIntranet**|**Disabled**|
    |**TrustedSites**|**Disabled**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>以程式設計方式停用包含清單

1. 建立 Visual Basic 或 Visual c # 主控台應用程式。

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
- [使用包含清單信任 Office 方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [保護 Office 方案](../vsto/securing-office-solutions.md)
