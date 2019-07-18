---
title: 如需在 ClickOnce 部署的必要條件的支援 URL
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78ba7398694e097f324695b6357abc0b35f8d3ee
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745572"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>作法：在 ClickOnce 部署中指定個別必要條件的支援 URL
A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署可以測試數目的用戶端電腦必須要有的必要條件[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]執行的應用程式。 這些相依性包括所需的最低版本.NET framework 版本的作業系統，以及必須預先安裝在全域組件快取 (GAC) 中的任何組件。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]不過，無法安裝任何必要條件本身;如果找不到必要元件，它只是中止安裝，並顯示對話方塊，說明安裝失敗的原因。

 有兩種方法來安裝必要條件。 您可以使用啟動載入器應用程式進行安裝。 或者，您可以指定個別必要條件、 支援 URL 找不到必要條件時，會顯示在對話方塊中的使用者。 參考該 URL 的頁面可以包含連結安裝必要的先決條件的指示。 如果應用程式未指定為個別的必要條件、 支援 URL[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]顯示整個應用程式的部署資訊清單中指定的支援 URL，如果已定義。

 雖然[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]， *Mage.exe*，以及*MageUI.exe*所有可用來產生[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署中，這些工具都不直接支援指定為個別的支援 URL必要條件。 本文件說明如何修改您部署的應用程式資訊清單和部署資訊清單，以加入這些程式庫支援 Url。

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>指定個別必要條件的支援 URL

1. 開啟應用程式資訊清單 ( *.manifest*檔案) 的[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]在文字編輯器應用程式。

2. 針對作業系統的必要條件，新增`supportUrl`屬性設定為`dependentOS`項目：

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. 針對特定版本的通用語言執行平台的必要條件，新增`supportUrl`屬性設定為`dependentAssembly`指定通用語言執行階段相依性的項目：

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. 對於必須預先安裝在全域組件快取中的組件的必要條件、 設定`supportUrl`針對`dependentAssembly`指定必要的組件的項目：

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. 選擇性。 以.NET Framework 4 為目標的應用程式開啟部署資訊清單 ( *.application*檔案) 的[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]在文字編輯器應用程式。

6. 針對.NET Framework 4 先決條件是，新增`supportUrl`屬性設定為`compatibleFrameworks`項目：

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. 一旦您以手動方式已改變應用程式資訊清單，您必須重新簽署應用程式資訊清單中使用您的數位憑證，然後更新並重新簽署部署資訊清單。 使用*Mage.exe*或是*MageUI.exe*若要完成這項工作，以重新產生這些檔案使用的 SDK 工具[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]會清除您手動變更。 如需有關如何使用 Mage.exe 來重新簽署資訊清單的詳細資訊，請參閱[How to:重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。

## <a name="net-framework-security"></a>.NET Framework 安全性
 支援 URL 不會顯示在對話方塊中，如果應用程式標記為在部分信任中執行。

## <a name="see-also"></a>另請參閱
- [Mage.exe (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks > 項目](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)
- [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)