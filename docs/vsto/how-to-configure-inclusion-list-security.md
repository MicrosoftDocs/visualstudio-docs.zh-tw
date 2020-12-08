---
title: 如何：設定包含清單安全性
description: 設定 ClickOnce 信任提示，以控制終端使用者是否可以透過將信任決策儲存至內含清單來選擇安裝 Office 方案。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1f9eca5150e019906805adf40e5c9b6af8a3c14e
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846723"
---
# <a name="how-to-configure-inclusion-list-security"></a>如何：設定包含清單安全性
  如果您有系統管理員許可權，您可以設定 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示，以控制終端使用者是否可透過將信任決策儲存至內含清單，來控制使用者是否可以選擇安裝 Office 方案。 如需包含清單的詳細資訊，請參閱 [使用包含清單來信任 Office 方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 針對每五個區域中的解決方案，您可以設定下列選項：

- 啟用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示金鑰和包含清單。 您可以允許終端使用者將信任授與以任何憑證簽署的 Office 方案。

- 限制 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示金鑰和包含清單。 您可以讓終端使用者安裝使用識別發行者的憑證簽署的 Office 方案，但是該憑證尚未受信任。

- 停用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示金鑰和包含清單。 您可以防止終端使用者安裝未以明確信任的憑證簽署的任何 Office 解決方案。

## <a name="enable-the-inclusion-list"></a>啟用包含清單
 當您想要讓使用者看到安裝和執行來自該區域之任何 Office 方案的選項時，請啟用區域的包含清單。

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>使用登錄編輯程式啟用包含清單

1. 開啟 [登錄編輯程式]：

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 [ **開啟** ] 方塊中，輸入 **regedt32.exe**，然後按一下 **[確定]**。

2. 尋找下列登錄機碼：

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     如果機碼不存在，請加以建立。

3. 將下列子機碼新增為 **字串值**（如果不存在的話），以及相關聯的值。

    |字串值子機碼|值|
    |-------------------------|-----------|
    |**網際網路**|**AuthenticodeRequired**|
    |**UntrustedSites**|**停用**|
    |**MyComputer**|**啟用**|
    |**LocalIntranet**|**啟用**|
    |**TrustedSites**|**啟用**|

     根據預設， **網際網路** 的值為 **AuthenticodeRequired** ，而 **UntrustedSites** 的值為 **Disabled**。

### <a name="to-enable-the-inclusion-list-programmatically"></a>以程式設計方式啟用包含清單

1. 建立 Visual Basic 或 Visual c # 主控台應用程式。

2. 開啟要編輯的 *Program.cs* 檔案，然後加入下列 *程式* 代碼。

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
 限制包含清單，讓解決方案必須以具有已知身分識別的 Authenticode 憑證簽署，使用者才會提示使用者進行信任決策。

### <a name="to-restrict-the-inclusion-list"></a>限制包含清單

1. 開啟 [登錄編輯程式]：

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 [ **開啟** ] 方塊中，輸入 **regedt32.exe**，然後按一下 **[確定]**。

2. 尋找下列登錄機碼：

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     如果機碼不存在，請加以建立。

3. 將下列子機碼新增為 **字串值**（如果不存在的話），以及相關聯的值。

    |字串值子機碼|值|
    |-------------------------|-----------|
    |**UntrustedSites**|**停用**|
    |**網際網路**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     根據預設， **網際網路** 的值為 **AuthenticodeRequired** ，而 **UntrustedSites** 的值為 **Disabled**。

### <a name="to-restrict-the-inclusion-list-programmatically"></a>以程式設計方式限制包含清單

1. 建立 Visual Basic 或 Visual c # 主控台應用程式。

2. 開啟要編輯的 *Program.cs* 檔案，然後加入下列 *程式* 代碼。

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
 您可以停用包含清單，讓使用者只能安裝以受信任且已知的憑證簽署的方案。

### <a name="to-disable-the-inclusion-list"></a>停用包含清單

1. 開啟 [登錄編輯程式]：

    1. 按一下 **[開始]** ，然後按一下 **[執行]** 。

    2. 在 [ **開啟** ] 方塊中，輸入 **regedt32.exe**，然後按一下 **[確定]**。

2. 如果此登錄機碼不存在，請建立下列登錄機碼：

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

3. 將下列子機碼新增為 **字串值**（如果不存在的話），以及相關聯的值。

    |字串值子機碼|值|
    |-------------------------|-----------|
    |**UntrustedSites**|**停用**|
    |**網際網路**|**停用**|
    |**MyComputer**|**停用**|
    |**LocalIntranet**|**停用**|
    |**TrustedSites**|**停用**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>以程式設計方式停用包含清單

1. 建立 Visual Basic 或 Visual c # 主控台應用程式。

2. 開啟要編輯的 *Program.cs* 檔案，然後加入下列 *程式* 代碼。

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
- [使用包含清單來信任 Office 方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [保護 Office 方案](../vsto/securing-office-solutions.md)
