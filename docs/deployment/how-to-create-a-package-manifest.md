---
title: 建立套件資訊清單 |Microsoft Docs
description: 瞭解如何使用啟動載入器套件來部署 ClickOnce 應用程式的必要條件，其中包含每個地區設定的套件資訊清單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cef6cd23a1e5ff1e00e2d4d93313ee1e9355ece2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927557"
---
# <a name="how-to-create-a-package-manifest"></a>How to: Create a package manifest (如何：建立封裝資訊清單)
若要部署應用程式的必要條件，您可以使用啟動載入器套件。 啟動載入器套件包含單一產品資訊清單檔案，但每個地區設定都有套件資訊清單。 不同當地語系化版本之間的共用功能應該進入產品資訊清單。

 如需產品資訊清單的詳細資訊，請參閱 [如何：建立產品資訊清單](../deployment/how-to-create-a-product-manifest.md)。

## <a name="create-the-package-manifest"></a>建立套件資訊清單

#### <a name="to-create-the-package-manifest"></a>若要建立封裝資訊清單

1. 建立啟動載入器套件的目錄。 此範例使用 *C:\package*。

2. 使用地區設定的名稱來建立子目錄，例如英文的 *en* 。

3. 在 Visual Studio 中，建立名為 *package.xml* 的 XML 檔案，並將它儲存至 *C:\package\en* 資料夾。

4. 加入 XML 以列出啟動載入器套件的名稱、此當地語系化套件資訊清單的文化特性，以及選用的授權合約。 下列 XML 會使用變數 `DisplayName` 和 `Culture` ，在稍後的元素中定義。

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. 加入 XML 以列出地區設定特定目錄中的所有檔案。 下列 XML 會使用名為 *eula.txt* 且適用于 **en** 地區設定的檔案。

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. 加入 XML 以定義啟動載入器套件的可當地語系化字串。 下列 XML 會新增 **en** 地區設定的錯誤字串。

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. 將 *C:\package* 資料夾複製到 Visual Studio 啟動載入器目錄。 針對 Visual Studio 2010，這是 *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* 目錄。

## <a name="example"></a>範例
 封裝資訊清單包含地區設定特定的資訊，例如錯誤訊息、軟體授權條款和語言套件。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Package
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  Name="DisplayName"
  Culture="Culture"
  LicenseAgreement="eula.txt">

  <PackageFiles>
    <PackageFile Name="eula.txt"/>
  </PackageFiles>

  <Strings>
    <String Name="DisplayName">Custom Bootstrapper Package</String>
    <String Name="Culture">en</String>
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>
    <String Name="GeneralFailure">A general error has occurred while
installing this package.</String>
  </Strings>
</Package>
```

## <a name="see-also"></a>另請參閱
- [產品和套件架構參考](../deployment/product-and-package-schema-reference.md)