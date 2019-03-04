---
title: 如何： 重新簽署應用程式和部署資訊清單 |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03606c1844ba058c5129affb5776cdc0a89849be
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610641"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>如何：重新簽署應用程式和部署資訊清單
您對 Windows Forms 應用程式、 Windows Presentation Foundation 應用程式 (xbap) 或 Office 方案的應用程式資訊清單中的部署屬性變更之後，您必須重新簽署應用程式和部署資訊清單與憑證。 這項程序有助於確保不會在終端使用者電腦上安裝遭到竄改的檔案。

 可能會重新簽署資訊清單的另一個案例是當您的客戶想要簽署應用程式和部署資訊清單與他們自己的憑證。

## <a name="re-sign-the-application-and-deployment-manifests"></a>重新簽署應用程式和部署資訊清單
 此程序假設您已經有進行變更您的應用程式資訊清單檔案 (*.manifest*)。 如需詳細資訊，請參閱 <<c0> [ 如何： 變更部署屬性](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472)。

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>若要重新簽署應用程式和部署資訊清單使用 Mage.exe

1.  開啟**Visual Studio 命令提示字元**視窗。

2.  將目錄變更至包含您想要登入的資訊清單檔案的資料夾。

3.  輸入下列命令來簽署應用程式資訊清單檔案。 取代*ManifestFileName*程式資訊清單檔案，再加上擴充功能的名稱。 取代*憑證*憑證檔案和取代的相對或完整路徑*密碼*與憑證的密碼。

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     例如，您可以執行下列命令來登入的增益集、 Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的應用程式資訊清單。 Visual Studio 所建立的暫時憑證不建議用於部署至生產環境。

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4.  輸入下列命令來更新並簽署部署資訊清單檔案，取代預留位置名稱，如同前一個步驟。

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     例如，您可以執行下列命令來更新並簽署部署資訊清單的 Excel 增益集、 Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式。

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5.  或者，複製 主要的部署資訊清單 (*發佈\\\<appname >.application*) 至您版本的部署目錄 (*publish\Application 檔案\\\<應用程式名稱 > _\<版本 >*)。

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>更新並重新簽署應用程式和部署資訊清單
 此程序假設您已經有進行變更您的應用程式資訊清單檔案 (*.manifest*)，但有其他已更新的檔案。 當更新檔案時，也必須更新代表檔案的雜湊。

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>若要更新和重新簽署應用程式和部署資訊清單使用 Mage.exe

1.  開啟**Visual Studio 命令提示字元**視窗。

2.  將目錄變更至包含您想要登入的資訊清單檔案的資料夾。

3.  移除 *.deploy*副檔名中發行的檔案從輸出資料夾。

4.  輸入下列命令，以使用新的雜湊，更新檔案更新應用程式資訊清單，並簽署應用程式資訊清單檔案。 取代*ManifestFileName*程式資訊清單檔案，再加上擴充功能的名稱。 取代*憑證*憑證檔案和取代的相對或完整路徑*密碼*與憑證的密碼。

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     例如，您可以執行下列命令來登入的增益集、 Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的應用程式資訊清單。 Visual Studio 所建立的暫時憑證不建議用於部署至生產環境。

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5.  輸入下列命令來更新並簽署部署資訊清單檔案，取代預留位置名稱，如同前一個步驟。

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     例如，您可以執行下列命令來更新並簽署部署資訊清單的 Excel 增益集、 Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式。

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6.  新增 *.deploy*回到檔案，檔案副檔名，但應用程式和部署資訊清單檔案。

7.  或者，複製 主要的部署資訊清單 (*發佈\\\<appname >.application*) 至您版本的部署目錄 (*publish\Application 檔案\\\<應用程式名稱 > _\<版本 >*)。

## <a name="see-also"></a>另請參閱
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)
- [Trusted application deployment overview](../deployment/trusted-application-deployment-overview.md) (信任的應用程式部署概觀)
- [How to: Enable ClickOnce security settings](../deployment/how-to-enable-clickonce-security-settings.md) (如何：啟用 ClickOnce 安全性設定)
- [How to: Set a security zone for a ClickOnce application](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md) (如何：設定 ClickOnce 應用程式的安全性區域)
- [How to: Set custom permissions for a ClickOnce application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md) (如何：設定 ClickOnce 應用程式的自訂權限)
- [How to: Debug a ClickOnce application with restricted permissions](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md) (如何：以限制的權限對 ClickOnce 應用程式進行偵錯)
- [How to: Add a trusted publisher to a client computer for ClickOnce applications](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md) (如何：將信任的發行者新增至 ClickOnce 應用程式的用戶端電腦)
- [How to: Configure the ClickOnce trust prompt behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md) (如何：設定 ClickOnce 信任提示行為)