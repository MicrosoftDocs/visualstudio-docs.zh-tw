---
title: "如何： 建立套件資訊清單 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 463286eb8360b728b3b7e3ce9396c9f4b7e11305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-package-manifest"></a>如何：建立封裝資訊清單
若要部署您的應用程式的必要條件，您可以使用啟動載入器套件。 啟動載入器套件包含單一產品資訊清單檔案，但卻封裝資訊清單的每個地區設定。 產品資訊清單都應在不同的當地語系化版本的共用的功能。  
  
 如需封裝資訊清單的詳細資訊，請參閱[How to： 建立產品資訊清單](../deployment/how-to-create-a-product-manifest.md)。  
  
## <a name="creating-the-package-manifest"></a>建立封裝資訊清單  
  
#### <a name="to-create-the-package-manifest"></a>若要建立封裝資訊清單  
  
1.  建立啟動載入器套件的目錄。 這個範例會使用 C:\package。  
  
2.  建立一個子目錄的地區設定，例如 en-us 代表英文名稱。  
  
3.  在 Visual Studio 中，建立名為 XML 檔案`package.xml`，並將它儲存到 C:\package\en 資料夾。  
  
4.  加入 XML 以列出的啟動載入器套件名稱、 這個當地語系化的封裝資訊清單，以及選擇性的授權合約的文化特性。 下列 XML 會使用變數`DisplayName`和`Culture`，其中定義更新的項目中。  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  加入 XML 以列出所有地區設定特定的目錄中的檔案。 下列 XML 會使用名為適用於的 eula.txt 檔案**en**地區設定。  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  加入 XML 以定義啟動載入器套件可當地語系化的字串。 下列 XML 會將錯誤字串以 en-us 地區設定。  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  C:\package 資料夾複製到 Visual Studio 啟動載入器目錄。 Visual Studio 2010 中，這是 \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages 目錄。  
  
## <a name="example"></a>範例  
 封裝資訊清單包含地區設定特定的資訊，例如錯誤訊息、 軟體授權條款，以及語言套件。  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)