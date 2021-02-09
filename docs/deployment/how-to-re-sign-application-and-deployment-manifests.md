---
title: 重新簽署應用程式和部署資訊清單 |Microsoft Docs
description: 瞭解如何在對部署屬性進行變更之後，使用憑證重新簽署應用程式和部署資訊清單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b4e4efee02ca1571f40ae33f9d69d8fbec0a1d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900439"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>如何：重新簽署應用程式和部署資訊清單
在 Windows Forms 應用程式的應用程式資訊清單中變更部署屬性之後，Windows Presentation Foundation 應用程式 (xbap) 或 Office 方案中，您必須使用憑證重新簽署應用程式和部署資訊清單。 這項程序有助於確保不會在終端使用者電腦上安裝遭到竄改的檔案。

 當您的客戶想要使用自己的憑證來簽署應用程式和部署資訊清單時，您可能會重新簽署資訊清單的另一種情況。

## <a name="re-sign-the-application-and-deployment-manifests"></a>重新簽署應用程式和部署資訊清單
 此程式假設您已經對應用程式資訊清單檔進行變更 (*指令* 清單) 。 如需詳細資訊，請參閱 [如何：變更部署屬性](/previous-versions/cc442869(v=vs.110))。

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>使用 Mage.exe 重新簽署應用程式和部署資訊清單

1. 開啟 **Visual Studio 的命令提示** 字元視窗。

2. 將目錄變更為包含您要簽署之資訊清單檔的資料夾。

3. 輸入下列命令以簽署應用程式資訊清單檔。 將 *ManifestFileName* 取代為您的資訊清單檔名稱加上副檔名。 將 *憑證* 取代為憑證檔案的相對或完整路徑，並將 *密碼* 取代為憑證的密碼。

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     例如，您可以執行下列命令來簽署增益集、Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的應用程式資訊清單。 不建議在生產環境中部署 Visual Studio 所建立的暫時憑證。

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. 輸入下列命令來更新和簽署部署資訊清單檔，並取代上一個步驟中的預留位置名稱。

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     例如，您可以執行下列命令來更新和簽署 Excel 增益集、Windows Forms 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的部署資訊清單。

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. （選擇性）將主要部署資訊清單 (*發佈 \\ \<appname> 。應用程式*) 到您的版本部署目錄 (*publish\Application 檔 \\ \<appname> _ \<version>*) 。

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>更新並重新簽署應用程式和部署資訊清單
 此程式假設您已經對應用程式資訊清單 *檔 ()* 進行變更，但仍有其他已更新的檔案。 更新檔案時，也必須更新代表檔案的雜湊。

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>使用 Mage.exe 更新並重新簽署應用程式和部署資訊清單

1. 開啟 **Visual Studio 的命令提示** 字元視窗。

2. 將目錄變更為包含您要簽署之資訊清單檔的資料夾。

3. 從 [發行輸出] 資料夾中的檔案移除 *.deploy 副檔名。*

4. 輸入下列命令以更新應用程式資訊清單，並針對更新的檔案使用新的雜湊，並簽署應用程式資訊清單檔。 將 *ManifestFileName* 取代為您的資訊清單檔名稱加上副檔名。 將 *憑證* 取代為憑證檔案的相對或完整路徑，並將 *密碼* 取代為憑證的密碼。

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     例如，您可以執行下列命令來簽署增益集、Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的應用程式資訊清單。 不建議在生產環境中部署 Visual Studio 所建立的暫時憑證。

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. 輸入下列命令來更新和簽署部署資訊清單檔，並取代上一個步驟中的預留位置名稱。

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     例如，您可以執行下列命令來更新和簽署 Excel 增益集、Windows Forms 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的部署資訊清單。

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. 將 *.deploy* 副檔名新增回檔案，但應用程式和部署資訊清單檔案除外。

7. （選擇性）將主要部署資訊清單 (*發佈 \\ \<appname> 。應用程式*) 到您的版本部署目錄 (*publish\Application 檔 \\ \<appname> _ \<version>*) 。

## <a name="see-also"></a>另請參閱
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)
- [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)
- [信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)
- [How to: Enable ClickOnce security settings (如何：啟用 ClickOnce 安全性設定)](../deployment/how-to-enable-clickonce-security-settings.md)
- [如何：設定 ClickOnce 應用程式的安全性區域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [How to: Set custom permissions for a ClickOnce application (如何：設定 ClickOnce 應用程式的自訂權限)](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [如何：使用受限制的許可權對 ClickOnce 應用程式進行 Debug 錯](securing-clickonce-applications.md)
- [如何：將新增信任的發行者新增至 ClickOnce 應用程式的用戶端電腦](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [How to: Configure the ClickOnce trust prompt behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md) (如何：設定 ClickOnce 信任提示行為)