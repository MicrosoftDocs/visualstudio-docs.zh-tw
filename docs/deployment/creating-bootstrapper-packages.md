---
title: 建立啟動載入器套件
ms.date: 05/02/2018
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f84f91ebedd47df8c0804adee35dcbec18d8551
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301990"
---
# <a name="create-bootstrapper-packages"></a>建立啟動載入器套件
安裝程式是通用安裝程式，可配置為檢測和安裝可轉散布元件，如 Windows 安裝程式 *（.msi*） 檔和可執行程式。 安裝程式也稱為啟動載入器。 其程式設計方式是透過一組 XML 資訊清單，指定用於管理元件安裝的中繼資料。  **"ClickOnce"的先決條件**"對話方塊中顯示的每個可轉散布元件或先決條件都是引導套裝程式。 啟動載入器套件是一組目錄和檔案，內含描述必要條件安裝方式的資訊清單檔案。

啟動載入器會先偵測是否已安裝所有必要條件。 如果未安裝必要條件，啟動載入器會先顯示授權合約。 接著，在使用者接受授權合約之後，就會開始安裝必要條件。 不過，如果啟動載入器偵測到所有必要條件，就會直接啟動應用程式安裝程式。

## <a name="create-custom-bootstrapper-packages"></a>創建自訂引導套裝程式
您可以使用 Visual Studio 中的 XML 編輯器生成引導程式清單。 要查看創建引導套裝程式的示例，請參閱[演練：創建具有隱私提示的自訂引導器](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)。

要創建引導套裝程式，必須創建產品清單，並且對於元件的每個當地語系化版本，也創建一個包清單。

* 產品清單 *，product.xml*，包含包的任何語言中性中繼資料。 此清單包含所有當地語系化版本之可轉散發元件通用的中繼資料。  要創建此檔，請參閱[如何：創建產品清單](../deployment/how-to-create-a-product-manifest.md)。

* 包清單，*包.xml*，包含特定于語言的中繼資料;它通常包含當地語系化的錯誤訊息。 元件的每個當地語系化版本至少必須各有一份套件資訊清單。 要創建此檔，請參閱[如何：創建包清單](../deployment/how-to-create-a-package-manifest.md)。

建立這些檔案之後，請將產品資訊清單檔案放入以自訂啟動載入器命名的資料夾中， 並將套件資訊清單檔案放入以地區設定命名的資料夾中。 例如，如果是英文版可轉散發套件的套件資訊清單檔案，請將檔案放入稱為 en 的資料夾中。 針對每個地區設定重複這個程序，例如以 ja 代表日文，以 de 代表德文。 最終的自訂啟動載入器套件可能會有下列資料夾結構。

```
CustomBootstrapperPackage
  product.xml
  CustomBootstrapper.msi
  de
    eula.rtf
    package.xml
  en
    eula.rtf
    package.xml
  ja
    eula.rtf
    package.xml
```

接下來，將可轉散布的檔案複製到引導程式資料夾位置。 有關詳細資訊，請參閱[如何：創建當地語系化的引導套裝程式](../deployment/how-to-create-a-localized-bootstrapper-package.md)。

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

或，對於舊版本的視覺工作室

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

或

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

您還可以在以下註冊表鍵中從**Path**值中找到引導者資料夾位置：

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

在 64 位元系統上，使用下列登錄機碼：

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

每個可轉散發元件會出現在套件目錄下各自的子資料夾中。 產品清單和可轉散布的檔必須放入此子資料夾中。 元件和包清單的當地語系化版本必須放在根據區域性名稱命名的子資料夾中。

將這些檔案複製到引導程式資料夾中後，引導套裝程式將自動顯示在"視覺化工作室**先決條件"** 對話方塊中。 如果未顯示自訂引導套裝程式，請關閉然後重新打開 **"先決條件"** 對話方塊。 有關詳細資訊，請參閱[先決條件對話方塊](../ide/reference/prerequisites-dialog-box.md)。

下表顯示啟動載入器會自動填入的屬性。

|屬性|描述|
|--------------|-----------------|
|ApplicationName|應用程式的名稱。|
|ProcessorArchitecture|可執行檔之目標平台的處理器和每個字組的位元。 包括下列值：<br /><br /> -   Intel<br />-   IA64<br />-   AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Microsoft Windows 95、Windows 98 或 Windows ME 作業系統的版本號碼。 版本的語法是 Major.Minor.ServicePack。|
|[VersionNT](/windows/desktop/Msi/versionnt)|Windows NT、Windows 2000、Windows XP、Windows Vista、Windows Server 2008 或 Windows 7 作業系統的版本號碼。 版本的語法是 Major.Minor.ServicePack。|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|安裝期間要運行的 Windows 安裝程式程式集 （msi.dll） 的版本。|
|[管理員使用者](/windows/desktop/Msi/adminuser)|如果使用者具有系統管理員權限，則會設定這個屬性。 值為 true 或 false。|
|InstallMode|安裝模式指出需要從中安裝元件的位置。 包括下列值：<br /><br /> -   HomeSite - 從廠商的網站安裝必要條件。<br />-   SpecificSite - 從您選取的位置安裝必要條件。<br />-   SameSite - 從應用程式的相同位置安裝必要條件。|

## <a name="separate-redistributables-from-application-installations"></a>從應用程式安裝中分離出來可轉散布
您可以防止可轉散發檔案部署在安裝專案中。 若要達成這項目的，請在 .NET Framework 目錄的 RedistList 資料夾中建立可轉散發清單：

`%ProgramFiles%\Microsoft.NET\RedistList`

可轉散布清單是一個 XML 檔，您應該使用以下格式命名：*\<公司名稱>。\<元件名稱>。瑞瑞斯特清單.xml*. 因此，例如，如果元件稱為 Acme 製作的 DataWidgets，請使用*Acme.DataWidgets.Redistlist.xml*。 可轉散發清單的內容範例可能如下所示：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>另請參閱
- [How to: Install prerequisites with a ClickOnce application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) (如何：使用 ClickOnce 應用程式安裝必要元件)
- [先決條件對話方塊](../ide/reference/prerequisites-dialog-box.md)
- [產品和套件結構描述參考](../deployment/product-and-package-schema-reference.md)
- [使用 Visual Studio 2005 引導器啟動安裝](https://msdn.microsoft.com/magazine/cc163899.aspx)
