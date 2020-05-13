---
title: 如何:重新簽名應用程式和部署清單 |微軟文件
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
ms.openlocfilehash: fc69ce1f79644d7f4b35fbb1c1e3a41691761390
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649192"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>如何：重新簽署應用程式和部署資訊清單
更改 Windows 窗體應用程式、Windows 演示文稿基礎應用程式 (xbap) 或 Office 解決方案的應用程式清單中的部署屬性後,必須使用證書重新簽名應用程式和部署清單。 這項程序有助於確保不會在終端使用者電腦上安裝遭到竄改的檔案。

 另一種可能重新簽名清單的情況是,您的客戶希望使用自己的證書對應用程式和部署清單進行簽名。

## <a name="re-sign-the-application-and-deployment-manifests"></a>重新簽署應用程式和部署資訊清單
 此過程假定您已經對應用程式清單檔 *(.manifest)* 進行了更改。 有關詳細資訊,請參閱[如何:更改部署屬性](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472)。

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>使用 Mage.exe 重新簽署應用程式和部署清單

1. 開啟**視覺化工作室指令提示視窗**。

2. 將目錄更改為包含要簽名的清單檔的資料夾。

3. 鍵入以下命令對應用程式清單檔進行簽名。 將*清單檔名稱*替換為清單檔的名稱以及副檔名。 將*憑證*替換為憑證檔的相對或完全限定路徑,並將*密碼*替換為證書的密碼。

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     例如,您可以運行以下命令來為外接程式、Windows 窗體應用程式或 Windows 演示文稿基礎瀏覽器應用程式簽名應用程式清單。 不建議將 Visual Studio 創建的臨時證書部署到生產環境中。

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. 鍵入以下命令以更新和簽名部署清單檔,替換占位符名稱,如上一步驟中所述。

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     例如,您可以運行以下命令來更新和簽署 Excel 外接程式、Windows 窗體應用程式或 Windows 演示文稿基礎瀏覽器應用程式的部署清單。

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. 或者,將主部署清單(*發佈\\\<應用程式名稱>.應用程式*)複製到版本部署目錄(*發佈\應用程式\\\<檔 應用程式名稱\<>_ 版本>*)。

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>更新並重新簽署應用程式和部署清單
 此過程假定您已經對應用程式清單檔 *(.manifest)* 進行了更改,但還有其他檔已更新。 更新檔時,還必須更新表示檔的哈希值。

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>使用 Mage.exe 更新並重新簽署應用程式和部署清單

1. 開啟**視覺化工作室指令提示視窗**。

2. 將目錄更改為包含要簽名的清單檔的資料夾。

3. 從發佈輸出資料夾中的檔案中刪除 *.deploy*檔案副檔名。

4. 鍵入以下命令以使用更新檔的新哈希更新應用程式清單,並簽署應用程式清單檔。 將*清單檔名稱*替換為清單檔的名稱以及副檔名。 將*憑證*替換為憑證檔的相對或完全限定路徑,並將*密碼*替換為證書的密碼。

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     例如,您可以運行以下命令來為外接程式、Windows 窗體應用程式或 Windows 演示文稿基礎瀏覽器應用程式簽名應用程式清單。 不建議將 Visual Studio 創建的臨時證書部署到生產環境中。

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. 鍵入以下命令以更新和簽名部署清單檔,替換占位符名稱,如上一步驟中所述。

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     例如,您可以運行以下命令來更新和簽署 Excel 外接程式、Windows 窗體應用程式或 Windows 演示文稿基礎瀏覽器應用程式的部署清單。

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. 將 *.deploy*檔案副檔名添加回檔案,應用程式和部署清單檔除外。

7. 或者,將主部署清單(*發佈\\\<應用程式名稱>.應用程式*)複製到版本部署目錄(*發佈\應用程式\\\<檔 應用程式名稱\<>_ 版本>*)。

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
- [How to: Configure the ClickOnce trust prompt behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md) (如何：設定 ClickOnce 信任提示行為)