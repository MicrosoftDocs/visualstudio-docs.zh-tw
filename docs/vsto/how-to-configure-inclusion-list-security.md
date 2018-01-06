---
title: "如何： 設定內含清單的安全性 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 09ea283b17a980ff9be1fae54ecc8b24912b70ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-inclusion-list-security"></a>如何：設定內含清單的安全性
  如果您有系統管理員權限，您可以設定[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示來控制使用者是否可以儲存至內含清單信任決策，藉以安裝 Office 方案的選項。 關於內含清單的資訊，請參閱[使用內含清單信任 Office 方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 如需每五個區域中的解決方案，您可以設定下列選項：  
  
-   啟用[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示的索引鍵和內含清單。 您可以讓使用者授與信任給 Office 方案的任何憑證進行簽署。  
  
-   限制[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示的索引鍵和內含清單。 您可以允許使用者安裝已簽署的 Office 方案使用可識別發行者上，但已經不受信任的憑證。  
  
-   停用[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信任提示的索引鍵和內含清單。 您可以防止使用者安裝未簽署的任何 Office 方案使用明確受信任的憑證。  
  
## <a name="enabling-the-inclusion-list"></a>啟用內含清單  
 當您想讓使用者安裝及執行任何來自該區域的 Office 方案的選項會呈現，請啟用區域的內含清單。  
  
#### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>若要使用登錄編輯程式中啟用內含清單  
  
1.  開啟登錄編輯程式：  
  
    1.  按一下**啟動**，然後按一下 **執行**。  
  
    2.  在**開啟**方塊中，輸入**regedt32.exe**，然後按一下 **確定**。  
  
2.  尋找下列登錄機碼：  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\。NETFramework\Security\TrustManager\PromptingLevel  
  
     如果索引鍵不存在，建立它。  
  
3.  新增下列子機碼為**字串值**，如果它們尚不存在，與相關的值。  
  
    |字串值的子機碼|值|  
    |-------------------------|-----------|  
    |**網際網路**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**已停用**|  
    |**MyComputer**|**已啟用**|  
    |**LocalIntranet**|**已啟用**|  
    |**TrustedSites**|**已啟用**|  
  
     根據預設，**網際網路**值**AuthenticodeRequired**和**UntrustedSites**值**已停用**。  
  
#### <a name="to-enable-the-inclusion-list-programmatically"></a>若要以程式設計方式啟用內含清單  
  
1.  建立 Visual Basic 或 Visual C# 主控台應用程式。  
  
2.  開啟 Program.vb 或 Program.cs 檔案進行編輯並加入下列程式碼。  
  
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
  
3.  建置並執行應用程式。  
  
## <a name="restricting-the-inclusion-list"></a>限制內含清單  
 限制包含清單，讓解決方案必須以提示使用者信任決策之前有已知識別的 Authenticode 憑證簽署。  
  
#### <a name="to-restrict-the-inclusion-list"></a>若要限制內含清單  
  
1.  開啟登錄編輯程式：  
  
    1.  按一下**啟動**，然後按一下 **執行**。  
  
    2.  在**開啟**方塊中，輸入**regedt32.exe**，然後按一下 **確定**。  
  
2.  尋找下列登錄機碼：  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\。NETFramework\Security\TrustManager\PromptingLevel  
  
     如果索引鍵不存在，建立它。  
  
3.  新增下列子機碼為**字串值**，如果它們尚不存在，與相關的值。  
  
    |字串值的子機碼|值|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**已停用**|  
    |**網際網路**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     根據預設，**網際網路**值**AuthenticodeRequired**和**UntrustedSites**值**已停用**。  
  
#### <a name="to-restrict-the-inclusion-list-programmatically"></a>若要以程式設計的方式限制內含清單  
  
1.  建立 Visual Basic 或 Visual C# 主控台應用程式。  
  
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
  
## <a name="disabling-the-inclusion-list"></a>停用內含清單  
 您可以停用內含清單，讓使用者只能安裝具有已知信任憑證的已簽署的解決方案。  
  
#### <a name="to-disable-the-inclusion-list"></a>若要停用內含清單  
  
1.  開啟登錄編輯程式：  
  
    1.  按一下**啟動**，然後按一下 **執行**。  
  
    2.  在**開啟**方塊中，輸入**regedt32.exe**，然後按一下 **確定**。  
  
2.  如果這並不存在，請建立下列登錄機碼：  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\。NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  新增下列子機碼為**字串值**，如果它們尚不存在，與相關的值。  
  
    |字串值的子機碼|值|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**已停用**|  
    |**網際網路**|**已停用**|  
    |**MyComputer**|**已停用**|  
    |**LocalIntranet**|**已停用**|  
    |**TrustedSites**|**已停用**|  
  
#### <a name="to-disable-the-inclusion-list-programmatically"></a>若要以程式設計的方式停用內含清單  
  
1.  建立 Visual Basic 或 Visual C# 主控台應用程式。  
  
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
  
## <a name="see-also"></a>請參閱  
 [使用內含清單信任 Office 方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)  
  
  