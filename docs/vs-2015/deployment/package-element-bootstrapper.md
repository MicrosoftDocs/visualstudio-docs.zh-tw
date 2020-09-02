---
title: '&lt;啟動載入器 &gt;)  (套件元素 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <package> element [bootstrapper]
ms.assetid: ecd06658-ad02-4440-bccd-88437b7fb816
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 62c19953d1c4d82c0040e728fc2c2645c68589c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157690"
---
# <a name="ltpackagegt-element-bootstrapper"></a>&lt;啟動載入器 &gt;)  (套件元素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Package`元素是封裝檔案內的最上層 XML 元素。  
  
## <a name="syntax"></a>語法  
  
```  
<Package  
    Culture  
    Name  
    LicenseAgreement  
>  
    <InstallChecks>  
        <AssemblyCheck   
            Property  
            Name  
            PublicKeyToken  
            Version  
            Language  
            ProcessorArchitecture  
        />  
        <RegistryCheck  
            Property  
            Key  
            Value  
        />  
        <ExternalCheck   
            PackageFile  
            Property  
            Arguments  
            Log  
        />  
        <FileCheck   
            Property  
            FileName  
            SearchPath  
            SpecialFolder  
            SearchDepth  
        />  
        <MsiProductCheck   
            Property  
            Product  
            Feature  
        />  
        <RegistryFileCheck   
            Property  
            Key  
            Value  
            File  
            SearchDepth  
        />  
    </InstallChecks>  
  
    <Commands  
        Reboot  
    >  
        <Command  
            PackageFile  
            Arguments  
            EstimatedInstallSeconds  
            EstimatedDiskBytes  
            EstimatedTempBytes  
            Log  
        >  
            <InstallConditions>  
                <BypassIf   
                    Property  
                    Compare  
                    Value  
                    Schedule  
                />  
                <FailIf   
                    Property  
                    Compare  
                    Value  
                    String  
                    Schedule  
                />  
            </InstallConditions>  
            <ExitCodes>  
                <ExitCode   
                    Value  
                    Result  
                    String  
                />  
            </ExitCodes>  
        </Command>  
    </Commands>  
  
    <PackageFiles  
        CopyAllComponents  
    >  
        <PackageFile   
            Name  
            Path  
            HomeSite  
            PublicKey  
        />  
    </PackageFiles>  
  
    <Strings>  
        <String  
            Name  
        >  
        </String>  
    </Strings>  
  
    <Schedules>  
        <Schedule  
            Name  
        >  
           <BuildList />  
           <BeforePackage />  
           <AfterPackage />  
        </Schedule>  
    </Schedules>  
</Package>  
```  
  
## <a name="elements-and-attributes"></a>元素和屬性  
 `Package`需要元素。 它具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Culture`|必要。 定義此封裝的文化特性，以決定要使用的語言。 這個屬性是元素中的索引鍵 `Strings` ，它會在安裝期間列出產品名稱和錯誤訊息的文化特性特定字串。|  
|`Name`|必要。 在工具中顯示給開發人員的封裝名稱，例如 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 這個屬性是元素中的索引鍵 `Strings` ，它應該包含一個專案，其中 `String` 的 `Name` 和 `Culture` 屬性設定為符合 `Name` `Culture` 的和屬性 `Package` 。|  
|`LicenseAgreement`|選擇性。 指定散發套件中的檔案名，其中包含 (EULA) 的使用者授權合約。  這個檔案可以是純文字 ( .txt) 或 Rich Text 格式。  ( .rtf) |  
  
## <a name="example"></a>範例  
 下列程式碼範例顯示可轉散發的完整封裝檔案 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.rtf"  
>  
  
    <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
    </PackageFiles>  
  
    <!-- Defines a localizable string table for error messages-->  
    <Strings>  
        <String Name="DisplayName">.NET Framework 2.0</String>  
        <String Name="Culture">en</String>  
        <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>  
        <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>  
        <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>  
        <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>  
        <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>  
        <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>  
        <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>  
        <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>  
        <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>  
        <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>  
        <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>  
    </Strings>  
  
</Package>  
```  
  
## <a name="see-also"></a>另請參閱  
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)
