---
title: 如何： 建立產品資訊清單 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdb95f417cadac04a04e30b1e965392f2492d864
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815765"
---
# <a name="how-to-create-a-product-manifest"></a>如何：建立產品資訊清單
若要部署您的應用程式的必要條件，您可以建立啟動載入器套件。 啟動載入器套件包含單一產品資訊清單檔案，但卻封裝資訊清單的每個地區設定。 封裝資訊清單包含您的封裝當地語系化特定層面。 這包括字串、 使用者授權合約，以及語言套件。  
  
 如需產品資訊清單的詳細資訊，請參閱[How to： 建立封裝資訊清單](../deployment/how-to-create-a-package-manifest.md)。  
  
## <a name="creating-the-product-manifest"></a>建立產品資訊清單  
  
#### <a name="to-create-the-product-manifest"></a>若要建立產品資訊清單  
  
1.  建立啟動載入器套件的目錄。 這個範例會使用 C:\package。  
  
2.  在 Visual Studio 中，建立新的 XML 檔案，稱為`product.xml`，並將它儲存到 C:\package 資料夾。  
  
3.  加入下列 XML 來描述封裝的 XML 命名空間與產品程式碼。 產品程式碼取代封裝的唯一識別碼。  
  
    ```xml  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  加入 XML 來指定封裝有相依性。 這個範例會使用相依性，在 Microsoft Windows Installer 3.1。  
  
    ```xml  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  加入 XML 以列出啟動載入器套件中的所有檔案。 這個範例會使用封裝檔案名稱 CorePackage.msi。  
  
    ```xml  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  複製或移動到 C:\package 資料夾 CorePackage.msi 檔案。  
  
7.  加入 XML 以使用啟動載入器命令安裝封裝。 啟動載入器會自動加入 **/qn** .msi 檔案中，將會以無訊息模式安裝的旗標。 如果是.exe 檔案，啟動載入器會使用殼層執行.exe 檔案。 下列 XML 顯示 CorePackage.msi，沒有引數，但您可以將命令列引數放入引數屬性。  
  
    ```xml  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  加入下列的 XML，以檢查是否已安裝此啟動載入器套件。 產品程式碼取代為可轉散發元件的 GUID。  
  
    ```xml  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. 加入 XML 以變更取決於啟動載入器行為，如果已安裝啟動載入器元件。 如果已安裝的元件，啟動載入器套件不會執行。 下列 XML 會檢查目前的使用者是否是系統管理員，因為此元件需要系統管理權限。  
  
    ```xml  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. 加入 XML 以設定結束代碼，如果已成功安裝，而且必須重新開機。 下列 XML 程式碼示範失敗，且 FailReboot 結束代碼，指出啟動載入器將會繼續安裝封裝。  
  
    ```xml  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. 加入下列 XML 結束啟動載入器命令 」 一節。  
  
    ```xml  
        </Command>  
    </Commands>  
    ```  
  
12. C:\package 將資料夾移到 Visual Studio 啟動載入器目錄。 Visual Studio 2010 中，這是 \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages 目錄。  
  
## <a name="example"></a>範例  
 產品資訊清單包含自訂的必要條件的安裝指示。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>另請參閱  
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)