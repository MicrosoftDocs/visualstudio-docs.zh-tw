---
title: 建立啟動載入器套件
description: 深入瞭解安裝程式，以及如何使用指定中繼資料的 XML 資訊清單來管理 ClickOnce 元件的安裝。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04cbb0db729d39295ee9c608a19302a109980f10
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912211"
---
# <a name="create-bootstrapper-packages"></a>建立啟動載入器套件
安裝程式是一般安裝程式，可設定來偵測及安裝可轉散發元件，例如 Windows Installer (*.msi*) 檔案和可執行程式。 安裝程式也稱為啟動載入器。 其程式設計方式是透過一組 XML 資訊清單，指定用於管理元件安裝的中繼資料。  ClickOnce 的必要條件對話方塊中顯示的每個可轉散發元件（或 **必要條件** ）都是啟動載入器套件。 啟動載入器套件是一組目錄和檔案，內含描述必要條件安裝方式的資訊清單檔案。

啟動載入器會先偵測是否已安裝所有必要條件。 如果未安裝必要條件，啟動載入器會先顯示授權合約。 接著，在使用者接受授權合約之後，就會開始安裝必要條件。 不過，如果啟動載入器偵測到所有必要條件，就會直接啟動應用程式安裝程式。

## <a name="create-custom-bootstrapper-packages"></a>建立自訂啟動載入器套件
您可以使用 Visual Studio 中的 XML 編輯器來產生啟動載入器資訊清單。 若要查看建立啟動載入器套件的範例，請參閱 [逐步解說：建立具有隱私權提示的自訂](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)啟動載入器。

若要建立啟動載入器套件，您必須建立產品資訊清單，並針對元件的每個當地語系化版本，也建立封裝資訊清單。

* 產品資訊清單（ *product.xml*）包含套件的任何非語言相關中繼資料。 此清單包含所有當地語系化版本之可轉散發元件通用的中繼資料。  若要建立這個檔案，請參閱 [如何：建立產品資訊清單](../deployment/how-to-create-a-product-manifest.md)。

* 封裝資訊清單（ *package.xml*）包含特定語言的中繼資料;它通常包含當地語系化的錯誤訊息。 元件的每個當地語系化版本至少必須各有一份套件資訊清單。 若要建立這個檔案，請參閱 [如何：建立封裝資訊清單](../deployment/how-to-create-a-package-manifest.md)。

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

接下來，將可轉散發檔案複製到啟動載入器資料夾位置。 如需詳細資訊，請參閱 [如何：建立當地語系化的](../deployment/how-to-create-a-localized-bootstrapper-package.md)啟動載入器套件。

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

或者，針對較舊版本的 Visual Studio

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

或

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

您也可以從下列登錄機碼中的 [ **路徑** ] 值尋找啟動載入器資料夾位置：

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

在 64 位元系統上，使用下列登錄機碼：

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

每個可轉散發元件會出現在套件目錄下各自的子資料夾中。 產品資訊清單和可轉散發檔案必須放在這個子資料夾中。 元件的當地語系化版本和套件資訊清單必須放在根據文化特性名稱命名的子資料夾中。

將這些檔案複製到啟動載入器資料夾之後，啟動載入器套件就會自動出現在 [Visual Studio **必要條件** ] 對話方塊中。 如果您的自訂啟動載入器套件未出現，請關閉然後再重新開啟 [ **必要條件** ] 對話方塊。 如需詳細資訊，請參閱 [必要條件對話方塊](../ide/reference/prerequisites-dialog-box.md)。

下表顯示啟動載入器會自動填入的屬性。

|屬性|描述|
|--------------|-----------------|
|ApplicationName|應用程式的名稱。|
|ProcessorArchitecture|可執行檔之目標平台的處理器和每個字組的位元。 包括下列值：<br /><br /> -   Intel<br />-   IA64<br />-   AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Microsoft Windows 95、Windows 98 或 Windows ME 作業系統的版本號碼。 版本的語法是 Major.Minor.ServicePack。|
|[VersionNT](/windows/desktop/Msi/versionnt)|Windows NT、Windows 2000、Windows XP、Windows Vista、Windows Server 2008 或 Windows 7 作業系統的版本號碼。 版本的語法是 Major.Minor.ServicePack。|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|要在安裝期間執行的 Windows Installer 元件 ( # A0) 版本。|
|[AdminUser](/windows/desktop/Msi/adminuser)|如果使用者具有系統管理員權限，則會設定這個屬性。 值為 true 或 false。|
|InstallMode|安裝模式指出需要從中安裝元件的位置。 包括下列值：<br /><br /> -   HomeSite - 從廠商的網站安裝必要條件。<br />-   SpecificSite - 從您選取的位置安裝必要條件。<br />-   SameSite - 從應用程式的相同位置安裝必要條件。|

## <a name="separate-redistributables-from-application-installations"></a>從應用程式安裝分隔可轉散發套件
您可以防止可轉散發檔案部署在安裝專案中。 若要達成這項目的，請在 .NET Framework 目錄的 RedistList 資料夾中建立可轉散發清單：

`%ProgramFiles%\Microsoft.NET\RedistList`

可轉散發清單是 XML 檔案，您應該使用下列格式來命名： *\<Company Name> . \<Component Name>.RedistList.xml*。 比方說，如果是由 DataWidgets 所建立的元件，請使用 *Acme.DataWidgets.RedistList.xml*。 可轉散發清單的內容範例可能如下所示：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>另請參閱
- [How to: Install prerequisites with a ClickOnce application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) (如何：使用 ClickOnce 應用程式安裝必要元件)
- [必要條件對話方塊](../ide/reference/prerequisites-dialog-box.md)
- [產品和套件架構參考](../deployment/product-and-package-schema-reference.md)
- [使用 Visual Studio 2005 啟動載入器開始安裝](/archive/msdn-magazine/2004/october/visual-studio-2005-bootstrapper-start-kick-your-installation)
