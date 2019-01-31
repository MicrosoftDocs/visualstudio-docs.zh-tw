---
title: 管理專案中的參考 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- Visual C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
ms.assetid: 05d1c51b-44f3-4973-8a11-6c919b08ad62
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3da4501d472949a89ad9120a07da99aaff3ebd1b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763646"
---
# <a name="managing-references-in-a-project"></a>管理專案中的參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在您針對外部元件或已連線服務撰寫程式碼之前，您的專案首先必須包含所需的參考。 參考其實是在專案檔中的項目，包含 Visual Studio 找出該元件或該服務所需的資訊。  
  
 若要加入參考，請在方案總管中的 [參考] 節點上按一下滑鼠右鍵，然後選擇 [加入參考] 。 如需詳細資訊，請參閱[＜How to：使用參考管理員新增或移除參考](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)。  
  
 ![在 Visual C&#43;&#43; 中新增參考](../ide/media/vs2015-cpp-add-reference.png "vs2015_cpp_add_reference")  
  
 您可以進行下列元件/服務類型的參考：  
  
-   Windows 市集應用程式參考  
  
-   .NET framework 類別庫或組件  
  
-   COM 元件  
  
-   其他組件或相同解決方案中專案的類別庫  
  
-   XML Web Service  
  
## <a name="windows-store-app-references"></a>Windows 市集應用程式參考  
  
### <a name="project-references"></a>專案參考  
 以 Windows 10 為目標的通用 Windows 平台 (UWP) 專案可以建立對方案中其他 UWP 專案的參考，或建立以 [!INCLUDE[win81](../includes/win81-md.md)] 為目標之 Windows 市集專案或二進位檔的參考，前提是這些專案不使用 Windows 10 中已被取代的 API。 如需詳細資訊，請參閱 [從 Windows 執行階段 8 移至 UWP](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx)。  
  
 如果選擇將 [!INCLUDE[win81](../includes/win81-md.md)] 專案的目標重定為 Windows 10，請參閱[移植、移轉和升級 Visual Studio 專案](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)  
  
### <a name="extension-sdk-references"></a>擴充功能 SDK 參考  
 以通用 Windows 平台 (UWP) 為目標的 Visual Basic、C#、C++ 和 JavaScript Windows 市集專案可以參考以 [!INCLUDE[win81](../includes/win81-md.md)] 為目標的擴充功能 SDK，前提是這些擴充功能 SDK 不使用在 Windows 10 中已被取代的 API。 請檢查擴充功能 SDK 廠商網站，以確定是否可透過以 UWP 為目標的 Windows 市集專案進行參考。  
  
 如果您判定不支援您的應用程式所參考的擴充功能 SDK，則需要執行下列步驟：  
  
1.  查看造成錯誤的專案名稱。 您專案的目標平台加註在專案名稱旁邊的括號中。 例如，**MyProjectName (Windows 8.1)** 表示您的專案 **MyProjectName** 的目標平台版本為 [!INCLUDE[win81](../includes/win81-md.md)]。  
  
2.  移至擁有不受支援之擴充功能 SDK 的廠商網站，並安裝相依性與您專案的目標平台版本相容的擴充功能 SDK 版本。  
  
    > [!NOTE]
    >  若要找出擴充功能 SDK 是否具有其他擴充功能 SDK 的相依性，其中一個方法是重新啟動 Visual Studio，建立新的 C# Windows 市集專案，在專案按右鍵並選擇 [加入參考] ，移至 [Windows]  索引標籤，再移至 [擴充功能]  子索引標籤，選取擴充功能 SDK 並查看 [參考管理員] 的右窗格。 如果有相依性，則會在那裡列出。  
  
    > [!IMPORTANT]
    >  如果您的專案是以 Windows 10 為目標，且在先前步驟中安裝的擴充功能 SDK 相依於 Microsoft Visual C++ Runtime Package，則與 Windows 10 相容的 Microsoft Visual C++ Runtime Package 版本為 v14.0 ，並隨著 Visual Studio 2015 一起安裝。  
  
3.  如果您在先前步驟中安裝的擴充功能 SDK 具有其他擴充功能 SDK 的相依性，請移至擁有相依性的廠商網站，並安裝與您專案的目標平台版本相容的這些相依性版本。  
  
4.  重新啟動 Visual Studio，然後開啟您的應用程式。  
  
5.  在導致錯誤專案中的 [參考]  節點上按右鍵，然後選擇 [加入參考]   
  
6.  依序按一下 [Windows]  索引標籤和 [擴充功能]  子索引標籤，然後針對舊擴充功能 SDK 取消核取方塊，並核取新擴充功能 SDK 的核取方塊。 按一下 [確定] 。  
  
## <a name="adding-a-reference-at-design-time"></a>在設計階段加入參考  
 當您在專案中參考組件時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會搜尋下列位置中的組件：  
  
-   目前專案目錄。 (您可以使用 [瀏覽]  索引標籤尋找這些組件)。  
  
-   同一方案中的其他專案目錄。 (您可以使用 [專案]  索引標籤尋找這些組件。)  
  
> [!NOTE]
>  所有專案都包含 mscorlib 的隱含參考。 Visual Basic 專案包含 `Microsoft.VisualBasic`的隱含參考。  
>   
>  在 Visual Studio 中，所有專案都包含 `System.Core`的隱含參考，即使 `System.Core` 已從參考清單中移除也一樣。  
  
## <a name="references-to-shared-components-at-run-time"></a>在執行階段參考共用元件  
 在執行階段中，元件必須位於專案的輸出路徑或 [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC) 中。 如果專案包含不在這些位置其中之一的物件參考，您必須在建置專案時，將參考複製至專案的輸出路徑。 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 屬性表示是否要進行此複製。 如果值為 **True**，則當您建置專案時，會將參考複製至專案目錄。 如果值為 **False**，則不會複製參考。  
  
 如果您部署的應用程式中包含在 GAC 中已註冊自訂元件的參考，則不論 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 設定為何，該元件都不會隨著應用程式一起部署。 在舊版的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中，您可以在參考上設定 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 屬性以確保組件已部署。 現在，您必須手動將組件加入 \Bin 資料夾。 這會使所有自訂程式碼受到監督，降低您在不熟悉的情況下發行自訂程式碼的風險。  
  
 根據預設，如果組件或元件位於全域組件快取或 Framework 元件，則 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 屬性會設定為 **False** 。 否則，值會設定為 **True**。 專案對專案參考一律會設定為 **True**。  
  
## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>參考以不同 .NET Framework 版本為目標的專案或元件  
 您可以建立參考目標為不同 .NET Framework 版本之專案或組件的應用程式。 例如，您可以建立目標為 [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] (參考目標為 [!INCLUDE[dnprdnext](../includes/dnprdnext-md.md)] 的組件) 的應用程式。 如果您建立之專案的目標是舊版 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]，則無法在該專案中設定目標為 [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] 或 .NET Framework 第 4 版之專案或組件的參考。  
  
 如需詳細資訊，請參閱[以特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)。  
  
## <a name="project-to-project-references"></a>專案對專案參考  
 專案對專案參考是包含組件的專案參考；您可以使用 [專案]  索引標籤建立專案對專案參考。當給定專案路徑時，Visual Studio 即可找出組件。  
  
 當您有會產生組件的專案時，您應該參考該專案，而不要使用檔案參考 (請參閱下文)。 專案對專案參考的優點是它會在組建系統中建立專案之間的相依性。 如果自上次建置的參考專案已變更，則將會建立相依專案。 檔案參考不會建立組建相依性，因此可以建置參考專案而不需建置相依專案，且參考可能會遭到淘汰。 (也就是專案可以參考先前建置的專案版本。)這會導致在 bin 目錄中需要單一 DLL 的數個版本，但這不可能達成。 發生這個衝突時，您會看到類似[警告：無法將專案 'project' 中的相依性 'file' 複製至執行目錄，因為它會覆寫參考 'file'](/visualstudio/vs-2015/misc/warning-the-dependency-file-in-project-project-cannot-be-copied) 的訊息。 如需詳細資訊，請參閱 <<c0> [ 疑難排解中斷的參考](../ide/troubleshooting-broken-references.md)和[How to:建立及移除專案相依性](../ide/how-to-create-and-remove-project-dependencies.md)。  
  
> [!NOTE]
>  如果某個專案的 .NET Framework 目標版本為 4.5 版，而其他專案的目標版本為第 2 版、第 3 版、3.5 版或 4.0 版，則會建立檔案參考而非專案對專案參考。  
  
## <a name="file-references"></a>檔案參考  
 檔案參考是 Visual Studio 專案內容外部之組件的直接參考；您可以使用 [參考管理員]  的 [瀏覽] 索引標籤建立檔案參考。 當您只有組件或元件，而且不需要會建立檔案參考做為輸出的專案時，請使用檔案參考。  
  
## <a name="see-also"></a>請參閱  
 [Troubleshooting Broken References](../ide/troubleshooting-broken-references.md)   
 [使用組件設計程式](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)   
 [如何：使用參考管理員新增或移除參考](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
