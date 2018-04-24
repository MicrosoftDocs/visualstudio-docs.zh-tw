---
title: 如何： 重新簽署應用程式和部署資訊清單 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba634ffb30d6459c940811f0ea080f8b71a37f34
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>如何：重新簽署應用程式和部署資訊清單
您對 Windows Forms 應用程式、 Windows Presentation Foundation 應用程式 (xbap) 或 Office 方案的應用程式資訊清單中的部署屬性變更之後，您必須重新簽署應用程式和部署資訊清單與憑證。 此程序有助於確保終端使用者電腦上沒有安裝的檔案遭竄改。  
  
 另一種情況可能會重新簽署資訊清單時，您的客戶想要簽署應用程式和部署資訊清單與自己的憑證。  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>重新簽署應用程式和部署資訊清單  
 此程序假設您已經有進行變更您的應用程式資訊清單檔案 (.manifest)。 如需詳細資訊，請參閱[如何： 變更部署屬性](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472)。  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>若要重新簽署應用程式和部署資訊清單使用 Mage.exe  
  
1.  開啟**Visual Studio 命令提示字元**視窗。  
  
2.  將目錄變更至包含您要簽署資訊清單檔案的資料夾。  
  
3.  輸入下列命令來簽署應用程式資訊清單檔案。 ManifestFileName 取代為您的資訊清單檔案，再加上副檔名的名稱。 憑證檔案的相對或完整路徑來取代憑證和密碼取代憑證的密碼。  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以執行下列命令，以登入的增益集、 Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的應用程式資訊清單。 部署到生產環境不建議使用 Visual Studio 所建立的暫時憑證。  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  輸入下列命令以更新並簽署部署資訊清單檔案，取代預留位置名稱，如同前一個步驟。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以執行下列命令以更新並簽署部署資訊清單的 Excel 增益集、 Windows Forms 應用程式或 Windows Presentation Foundation 瀏覽器應用程式。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  選擇性地複製主要部署資訊清單 (發行\\*appname*.application) 您版本的部署目錄 (publish\Application 檔案\\*appname*_*版本*)。  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>更新和重新簽署應用程式和部署資訊清單  
 此程序假設您已經完成變更您的應用程式資訊清單檔案 (.manifest)，但有其他已更新的檔案。 當更新檔案時，也必須更新代表檔案的雜湊。  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>若要更新並重新簽署應用程式和部署資訊清單使用 Mage.exe  
  
1.  開啟**Visual Studio 命令提示字元**視窗。  
  
2.  將目錄變更至包含您要簽署資訊清單檔案的資料夾。  
  
3.  從發行輸出資料夾中的檔案移除.deploy 副檔名。  
  
4.  輸入下列命令以使用新的更新檔案的雜湊更新應用程式資訊清單，並簽署應用程式資訊清單檔案。 ManifestFileName 取代為您的資訊清單檔案，再加上副檔名的名稱。 憑證檔案的相對或完整路徑來取代憑證和密碼取代憑證的密碼。  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以執行下列命令，以登入的增益集、 Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的應用程式資訊清單。 部署到生產環境不建議使用 Visual Studio 所建立的暫時憑證。  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  輸入下列命令以更新並簽署部署資訊清單檔案，取代預留位置名稱，如同前一個步驟。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以執行下列命令以更新並簽署部署資訊清單的 Excel 增益集、 Windows Forms 應用程式或 Windows Presentation Foundation 瀏覽器應用程式。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  將.deploy 副檔名加回檔案中，除了應用程式和部署資訊清單檔案。  
  
7.  選擇性地複製主要部署資訊清單 (發行\\*appname*.application) 您版本的部署目錄 (publish\Application 檔案\\*appname*_*版本*)。  
  
## <a name="see-also"></a>另請參閱  
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)   
 [如何：啟用 ClickOnce 安全性設定](../deployment/how-to-enable-clickonce-security-settings.md)   
 [如何：設定 ClickOnce 應用程式的安全性區域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [如何：設定 ClickOnce 應用程式的自訂使用權限](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [如何：以限制權限偵錯 ClickOnce 應用程式](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [如何： 新增 ClickOnce 應用程式的用戶端電腦信任的發行者](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [如何：設定 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)