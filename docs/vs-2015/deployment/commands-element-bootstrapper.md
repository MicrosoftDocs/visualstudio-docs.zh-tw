---
title: '&lt;命令&gt;項目 （啟動載入器） |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 309f93658cee6663c2b5673c03c6621330e7fa39
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276571"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;命令&gt;項目 （啟動載入器）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Commands`項目實作下方的項目所描述的測試`InstallChecks`項目，並宣告哪些封裝[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]測試失敗時，應該安裝啟動載入器。  
  
## <a name="syntax"></a>語法  
  
```  
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
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `Commands`是必要元素。 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Reboot`|選擇性。 決定系統是否應該重新啟動的任何封裝傳回重新開機結束代碼。 下列清單顯示有效的值：<br /><br /> `Defer`. 重新啟動會延遲，直到某些未來的時間。<br /><br /> `Immediate`. 如果其中一個封裝傳回重新開機結束代碼，會導致立即重新啟動。<br /><br /> `None`. 會導致任何重新啟動的要求會被忽略。<br /><br /> 預設為 `Immediate`。|  
  
## <a name="command"></a>命令  
 `Command` 項目是 `Commands` 項目的子項目。 A`Commands`項目可以有一或多個`Command`項目。 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`PackageFile`|必要。 若要安裝封裝的名稱應該一或多個所指定的條件`InstallConditions`傳回 false。 封裝必須在相同的檔案中定義，使用`PackageFile`項目。|  
|`Arguments`|選擇性。 一組命令列引數傳遞至封裝檔案。|  
|`EstimatedInstallSeconds`|選擇性。 估計的時間，以秒為單位，它會安裝套件。 這個值會決定啟動載入器會對使用者顯示進度列的大小。 預設值為在此情況下 0，不會指定估計的時間。|  
|`EstimatedDiskBytes`|選擇性。 已完成的以位元組為單位，封裝會在安裝後所佔用的磁碟空間估計的量。 這個值會在啟動載入器會顯示給使用者的硬碟空間需求。 預設值為的 0，啟動載入器的情況下不會顯示任何硬碟空間需求。|  
|`EstimatedTempBytes`|選擇性。 以位元組為單位，這個套件所需的暫存磁碟空間估計的量。|  
|`Log`|選擇性。 記錄檔套件所產生，相對於根目錄的封裝路徑。|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions`項目是子系`Command`項目。 每個`Command`項目可以有最多一個`InstallConditions`項目。 如果沒有`InstallConditions`項目存在，所指定的封裝`Condition`一定會執行。  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf`項目是子系`InstallConditions`項目，並說明正值條件下應該不會執行命令。 每個`InstallConditions`項目可以有零或多個`BypassIf`項目。  
  
 `BypassIf` 具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Property`|必要。 要測試之屬性的名稱。 屬性必須先前所定義的子系`InstallChecks`項目。 如需詳細資訊，請參閱 < [ \<InstallChecks > 項目](../deployment/installchecks-element-bootstrapper.md)。|  
|`Compare`|必要。 要執行的比較類型。 下列清單顯示有效的值：<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必要。 要與屬性比較的值。|  
|`Schedule`|選擇性。 名稱`Schedule`定義何時應該評估此規則的標記。|  
  
## <a name="failif"></a>FailIf  
 `FailIf`項目是子系`InstallConditions`項目，並說明正值條件下應該停止安裝。 每個`InstallConditions`項目可以有零或多個`FailIf`項目。  
  
 `FailIf` 具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Property`|必要。 要測試之屬性的名稱。 屬性必須先前所定義的子系`InstallChecks`項目。 如需詳細資訊，請參閱 < [ \<InstallChecks > 項目](../deployment/installchecks-element-bootstrapper.md)。|  
|`Compare`|必要。 要執行的比較類型。 下列清單顯示有效的值：<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必要。 要與屬性比較的值。|  
|`String`|選擇性。 要在失敗時對使用者顯示的文字。|  
|`Schedule`|選擇性。 名稱`Schedule`定義何時應該評估此規則的標記。|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes`項目是子系`Command`項目。 `ExitCodes`元素包含一或多個`ExitCode`項目，判斷安裝應該執行的結束代碼來回應來自套件。 可以有一個選擇性`ExitCode`底下的項目`Command`項目。 `ExitCodes` 沒有任何屬性。  
  
## <a name="exitcode"></a>ExitCode  
 `ExitCode`項目是子系`ExitCodes`項目。 `ExitCode`元素會決定安裝應該執行的結束代碼來回應來自套件。 `ExitCode` 包含沒有子項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Value`|必要。 結束代碼值，這個`ExitCode`項目會套用。|  
|`Result`|必要。 如何安裝應該因應此結束代碼。 下列清單顯示有效的值：<br /><br /> `Success`. 旗標為已成功安裝套件。<br /><br /> `SuccessReboot`. 封裝已成功安裝，加上旗標，指示系統在重新啟動。<br /><br /> `Fail`. 標記為失敗的封裝。<br /><br /> `FailReboot`. 套件標記為失敗，並指示重新啟動系統。|  
|`String`|選擇性。 要顯示給使用者，以回應此結束程式碼的值。|  
|`FormatMessageFromSystem`|選擇性。 決定是否要使用的結束程式碼中，對應的系統提供的錯誤訊息，或使用中提供的值`String`。 有效值`true`，這表示若要使用系統提供的錯誤，並`false`，這表示若要使用提供的字串`String`。 預設為 `false`。 如果這個屬性是`false`，但`String`未設定，將使用系統提供的錯誤。|  
  
## <a name="example"></a>範例  
 下列程式碼範例會定義可用來安裝.NET Framework 2.0 命令。  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## <a name="see-also"></a>另請參閱  
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > 項目](../deployment/installchecks-element-bootstrapper.md)



