---
title: '&lt;命令&gt;元素 （啟動載入器） |Microsoft 文件'
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
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac3ae61012bec5f8134a48714678110951c03b76
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31566195"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;命令&gt;元素 （啟動載入器）
`Commands`項目實作的項目底下所描述的測試`InstallChecks`項目，並宣告哪一個套件[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]啟動載入器應該安裝，如果測試失敗。  
  
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
 `Commands`項目為必要。 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Reboot`|選擇性。 決定系統是否應該重新啟動的任何封裝傳回重新開機結束代碼。 下列清單顯示有效值：<br /><br /> `Defer`. 重新啟動延後到未來。<br /><br /> `Immediate`. 如果其中一個封裝傳回重新開機結束代碼，會導致立即重新啟動。<br /><br /> `None`. 會導致任何重新啟動的要求會被忽略。<br /><br /> 預設值為 `Immediate`。|  
  
## <a name="command"></a>命令  
 `Command` 項目是 `Commands` 項目的子項目。 A`Commands`元素可以有一或多個`Command`項目。 項目具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`PackageFile`|必要。 若要安裝封裝的名稱應該一或多個所指定的條件`InstallConditions`傳回 false。 封裝必須在同一個檔案中定義，使用`PackageFile`項目。|  
|`Arguments`|選擇性。 一組命令列引數傳遞至封裝檔案。|  
|`EstimatedInstallSeconds`|選擇性。 估計的時間，以秒為單位，它會安裝封裝。 這個值會決定啟動載入器向使用者顯示進度列的大小。 預設為在此情況下 0，不會指定估計的時間。|  
|`EstimatedDiskBytes`|選擇性。 已完成的單位為位元組，封裝會在安裝後所佔用的磁碟空間估計的量。 此值用於啟動載入器會顯示給使用者的硬碟空間需求。 預設值為的 0，啟動載入器的情況下不會顯示任何硬碟空間需求。|  
|`EstimatedTempBytes`|選擇性。 以位元組為單位，封裝將會需要的暫存磁碟空間估計的量。|  
|`Log`|選擇性。 記錄檔套件所產生、 相對於套件的根目錄路徑。|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions`元素是子系`Command`項目。 每個`Command`元素可以有最多一個`InstallConditions`項目。 如果沒有`InstallConditions`元素存在，所指定的封裝`Condition`永遠會執行。  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf`元素是子系`InstallConditions`項目，並說明正數條件下應該不會執行命令。 每個`InstallConditions`元素可以有零或多個`BypassIf`項目。  
  
 `BypassIf` 具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Property`|必要。 要測試的屬性名稱。 屬性必須先前已定義的子系`InstallChecks`項目。 如需詳細資訊，請參閱[ \<InstallChecks > 項目](../deployment/installchecks-element-bootstrapper.md)。|  
|`Compare`|必要。 要執行的比較類型。 下列清單顯示有效值：<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必要。 要與屬性比較的值。|  
|`Schedule`|選擇性。 名稱`Schedule`定義何時應該評估此規則的標記。|  
  
## <a name="failif"></a>FailIf  
 `FailIf`元素是子系`InstallConditions`項目，並說明正值條件下應該停止安裝。 每個`InstallConditions`元素可以有零或多個`FailIf`項目。  
  
 `FailIf` 具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Property`|必要。 要測試的屬性名稱。 屬性必須先前已定義的子系`InstallChecks`項目。 如需詳細資訊，請參閱[ \<InstallChecks > 項目](../deployment/installchecks-element-bootstrapper.md)。|  
|`Compare`|必要。 要執行的比較類型。 下列清單顯示有效值：<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必要。 要與屬性比較的值。|  
|`String`|選擇性。 要在發生錯誤時對使用者顯示的文字。|  
|`Schedule`|選擇性。 名稱`Schedule`定義何時應該評估此規則的標記。|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes`元素是子系`Command`項目。 `ExitCodes`元素包含一或多個`ExitCode`項目，可決定安裝應該執行以回應從封裝的結束代碼。 可以有一個選擇性`ExitCode`下方的項目`Command`項目。 `ExitCodes` 沒有任何屬性。  
  
## <a name="exitcode"></a>ExitCode  
 `ExitCode`元素是子系`ExitCodes`項目。 `ExitCode`元素會決定安裝應該執行以回應從封裝的結束代碼。 `ExitCode` 包含沒有子項目，並具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Value`|必要。 結束代碼值，這個`ExitCode`元素會套用。|  
|`Result`|必要。 如何安裝應該回應此結束程式碼。 下列清單顯示有效值：<br /><br /> `Success`. 旗標為已成功安裝封裝。<br /><br /> `SuccessReboot`. 封裝已經順利安裝，加上旗標，指示系統重新啟動。<br /><br /> `Fail`. 標記為失敗的封裝。<br /><br /> `FailReboot`. 套件標記為失敗，並指示重新啟動系統。|  
|`String`|選擇性。 要顯示給使用者，以回應此結束程式碼的值。|  
|`FormatMessageFromSystem`|選擇性。 決定是否要使用對應的結束代碼，系統提供的錯誤訊息，或使用中提供的值`String`。 有效值為`true`，這表示若要使用系統提供的錯誤和`false`，這表示若要使用所提供的字串`String`。 預設值為 `false`。 如果這個屬性是`false`，但`String`未設定，將使用系統提供的錯誤。|  
  
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