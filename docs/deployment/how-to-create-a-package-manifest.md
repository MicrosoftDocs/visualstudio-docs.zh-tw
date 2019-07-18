---
title: HOW TO：建立封裝資訊清單 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8083ca9a8d3025b1760edde96279a0cd557f722
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899736"
---
# <a name="how-to-create-a-package-manifest"></a>HOW TO：建立套件資訊清單
若要部署您的應用程式的必要條件，您可以使用啟動載入器套件。 啟動載入器套件會包含單一產品資訊清單檔案的套件資訊清單但每個地區設定。 在不同的當地語系化版本之間共用的功能應該移入產品資訊清單。

 如需有關產品資訊清單的詳細資訊，請參閱[How to:建立產品資訊清單](../deployment/how-to-create-a-product-manifest.md)。

## <a name="create-the-package-manifest"></a>建立封裝資訊清單

#### <a name="to-create-the-package-manifest"></a>若要建立封裝資訊清單

1. 建立啟動載入器套件目錄。 這個範例會使用*C:\package*。

2. 建立一個子目錄的地區設定，名稱，例如*en*英文。

3. 在 Visual Studio 中，建立名為 XML 檔案*package.xml*，並將它儲存*C:\package\en*資料夾。

4. 加入至清單的啟動載入器套件名稱、 此當地語系化的封裝資訊清單中和選擇性的授權合約的文化特性的 XML。 下列 XML 程式碼會使用變數`DisplayName`和`Culture`，更新版本的項目中定義。

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. 加入 XML 以列出的地區設定特定目錄中的所有檔案。 下列 XML 程式碼會使用檔案，稱為*eula.txt*這是適用於**en**地區設定。

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. 加入 XML 以定義可當地語系化啟動載入器套件的字串。 下列 XML 會將錯誤字串，如**en**地區設定。

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

7. 複製*C:\package*到 Visual Studio 啟動載入器目錄的資料夾。 若為 Visual Studio 2010，則 *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*目錄。

## <a name="example"></a>範例
 封裝資訊清單包含地區設定特有的資訊，例如錯誤訊息、 軟體授權條款，以及語言套件。

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
- [產品和套件結構描述參考](../deployment/product-and-package-schema-reference.md)