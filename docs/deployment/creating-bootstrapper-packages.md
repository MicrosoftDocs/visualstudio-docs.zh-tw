---
title: "建立啟動載入器套件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 5f269369084df3d81d323e75730fad27713831ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-bootstrapper-packages"></a>建立啟動載入器套件
安裝程式 (Setup Program) 是一般安裝程式 (Installer)，可設定來偵測及安裝可轉散發元件，例如 Windows Installer (.msi) 檔案和可執行程式。 安裝程式也稱為啟動載入器。 其程式設計方式是透過一組 XML 資訊清單，指定用於管理元件安裝的中繼資料。  
  
 啟動載入器會先偵測是否已安裝所有必要條件。 如果未安裝必要條件，啟動載入器會先顯示授權合約。 接著，在使用者接受授權合約之後，就會開始安裝必要條件。 不過，如果啟動載入器偵測到所有必要條件，就會直接啟動應用程式安裝程式。  
  
## <a name="creating-custom-packages"></a>建立自訂套件  
 您可以使用 Visual Studio 中的 XML 編輯器產生資訊清單。 如需詳細資訊，請參閱 [How to: Create a Package Manifest](../deployment/how-to-create-a-package-manifest.md) 與 [How to: Create a Product Manifest](../deployment/how-to-create-a-product-manifest.md)。 如需查看建立啟動載入器套件的範例，請參閱 [逐步解說：建立自訂啟動載入器以顯示隱私權提示](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)。  
  
 若要建立啟動載入器套件，您必須將可轉散發套件以 EXE 或 MSI 檔案形式提供給啟動載入器資訊清單產生器。 啟動載入器資訊清單產生器接著會建立下列檔案：  
  
-   產品資訊清單 (product.xml)，包含套件的所有語言中性中繼資料。 此清單包含所有當地語系化版本之可轉散發元件通用的中繼資料。  
  
-   套件資訊清單 (package.xml)，包含特定語言中繼資料。此清單通常包含當地語系化的錯誤訊息。 元件的每個當地語系化版本至少必須各有一份套件資訊清單。  
  
 建立這些檔案之後，請將產品資訊清單檔案放入以自訂啟動載入器命名的資料夾中， 並將套件資訊清單檔案放入以地區設定命名的資料夾中。 例如，如果是英文版可轉散發套件的套件資訊清單檔案，請將檔案放入稱為 en 的資料夾中。 針對每個地區設定重複這個程序，例如以 ja 代表日文，以 de 代表德文。 最終的自訂啟動載入器套件可能會有下列資料夾結構。  
  
 `CustomBootstrapperPackage`  
  
 `product.xml`  
  
 `CustomBootstrapper.msi`  
  
 `de`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 `en`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 `ja`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 最後，將可轉散發檔案複製到啟動載入器資料夾位置中。 如需詳細資訊，請參閱 [How to: Create a Localized Bootstrapper Package](../deployment/how-to-create-a-localized-bootstrapper-package.md)。  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 或  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 您也可以從下列登錄機碼中的 [路徑]  值，決定啟動載入器資料夾位置：  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 在 64 位元系統上，使用下列登錄機碼：  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 每個可轉散發元件會出現在套件目錄下各自的子資料夾中。 產品資訊清單和可轉散發檔案會放入這個子資料夾中。 元件和套件資訊清單的當地語系化版本會放入依文化特性名稱命名的子資料夾中。  
  
 當這些檔案複製到啟動載入器資料夾之後，啟動載入器套件就會自動出現在 Visual Studio 的 [必要條件] 對話方塊中。 如果您的自訂啟動載入器套件沒有出現在其中，請關閉再重新開啟 [必要條件] 對話方塊。 如需詳細資訊，請參閱 [Prerequisites Dialog Box](../ide/reference/prerequisites-dialog-box.md)。  
  
 下表顯示啟動載入器會自動填入的屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|ApplicationName|應用程式的名稱。|  
|ProcessorArchitecture|可執行檔之目標平台的處理器和每個字組的位元。 包括下列值：<br /><br /> -Intel<br />-IA64<br />-AMD64|  
|[Version9x](https://msdn.microsoft.com/en-us/library/aa372490\(v=vs.140\).aspx)|Microsoft Windows 95、Windows 98 或 Windows ME 作業系統的版本號碼。 版本的語法是 Major.Minor.ServicePack。|  
|[VersionNT](https://msdn.microsoft.com/en-us/library/aa372495\(v=vs.140\).xaspx)|Windows NT、Windows 2000、Windows XP、Windows Vista、Windows Server 2008 或 Windows 7 作業系統的版本號碼。 版本的語法是 Major.Minor.ServicePack。|  
|[VersionMSI](https://msdn.microsoft.com/en-us/library/aa372493\(v=vs.140\).aspx)|在安裝期間執行的 Windows Installer 組件 (msi.dll) 版本。|  
|[AdminUser](https://msdn.microsoft.com/en-us/library/aa367545\(v=vs.140\).aspx)|如果使用者具有系統管理員權限，則會設定這個屬性。 值為 true 或 false。|  
|InstallMode|安裝模式指出需要從中安裝元件的位置。 包括下列值：<br /><br /> 從廠商的網站安裝-HomeSite-必要條件。<br />從您選取的位置安裝-SpecificSite-必要條件。<br />從應用程式的相同位置安裝-SameSite-必要條件。|  
  
## <a name="separating-redistributables-from-application-installations"></a>將可轉散發套件與應用程式安裝分開放置  
 您可以防止可轉散發檔案部署在安裝專案中。 若要達成這項目的，請在 .NET Framework 目錄的 RedistList 資料夾中建立可轉散發清單：  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 可轉散發清單是 XML 檔案，應該使用下列格式命名： *公司名稱*.*元件名稱*.RedistList.xml。 例如，如果 Acme 建立稱為 Datawidgets 的元件，請使用 Acme.DataWidgets.RedistList.xml。 可轉散發清單的內容範例可能如下所示：  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>請參閱  
 [如何：使用 ClickOnce 應用程式安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [必要條件對話方塊](../ide/reference/prerequisites-dialog-box.md)   
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)   
 [使用 Visual Studio 2005 啟動載入器開始進行安裝](http://go.microsoft.com/fwlink/?LinkId=107537)