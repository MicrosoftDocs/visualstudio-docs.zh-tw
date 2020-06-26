---
title: 如何-建立產品資訊清單 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0f4302756b089376eca8926453399768faaf58f
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382506"
---
# <a name="how-to-create-a-product-manifest"></a>How to: Create a product manifest (如何：建立產品資訊清單)
若要部署應用程式的必要條件，您可以建立啟動載入器套件。 啟動載入器套件包含單一產品資訊清單檔案，但每個地區設定都有套件資訊清單。 封裝資訊清單包含封裝的當地語系化特定層面。 這包括字串、使用者授權合約及語言套件。

 如需封裝資訊清單的詳細資訊，請參閱[如何：建立封裝資訊清單](../deployment/how-to-create-a-package-manifest.md)。

## <a name="create-the-product-manifest"></a>建立產品資訊清單

#### <a name="to-create-the-product-manifest"></a>建立產品資訊清單

1. 建立啟動載入器套件的目錄。 這個範例會使用 C:\package。

2. 在 Visual Studio 中，建立名為*product.xml*的新 XML 檔案，並將它儲存至*C:\package*資料夾。

3. 新增下列 XML 來描述封裝的 XML 命名空間和產品程式碼。 將產品程式碼取代為封裝的唯一識別碼。

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. 加入 XML 以指定封裝具有相依性。 此範例會使用 Microsoft Windows Installer 3.1 的相依性。

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. 加入 XML 以列出啟動載入器套件中的所有檔案。 這個範例會使用封裝檔案名*CorePackage.msi*。

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. 複製*CorePackage.msi*檔案，或將其移至*C:\package*資料夾。

7. 新增 XML 以使用啟動載入器命令來安裝封裝。 啟動載入器會自動將 **/qn**旗標新增至 *.msi*檔案，而該檔案將會以無訊息模式安裝。 如果檔案是 *.exe*，啟動載入器會使用 shell 來執行 *.exe*檔案。 下列 XML 不會顯示*CorePackage.msi*的引數，但您可以將命令列引數放入 `Arguments` 屬性中。

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. 新增下列 XML，以檢查是否已安裝此啟動載入器套件。 將產品程式碼取代為可轉散發元件的 GUID。

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. 加入 XML 以根據是否已安裝啟動載入器元件來變更啟動載入器行為。 如果已安裝元件，啟動載入器套件就不會執行。 下列 XML 會檢查目前的使用者是否為系統管理員，因為此元件需要管理許可權。

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

10. 新增 XML 以設定結束代碼（如果安裝成功），以及是否需要重新開機。 下列 XML 示範 Fail 和 FailReboot 結束代碼，這表示啟動載入器將不會繼續安裝封裝。

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. 新增下列 XML 以結束啟動載入器命令的區段。

    ```xml
        </Command>
    </Commands>
    ```

12. 將 [ *C:\package* ] 資料夾移至 Visual Studio 啟動載入器目錄。 針對 Visual Studio 2010，這是*\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*目錄。

## <a name="example"></a>範例
 產品資訊清單包含自訂必要條件的安裝指示。

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
- [產品和套件架構參考](../deployment/product-and-package-schema-reference.md)