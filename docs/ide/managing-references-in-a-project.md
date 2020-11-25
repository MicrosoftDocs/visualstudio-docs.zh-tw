---
title: 管理專案中的參考
description: 瞭解如何在專案中管理外部元件和已聯機服務的參考。
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fdf737d26ec14c2a108125425a3b66cdf4a0e519
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870946"
---
# <a name="manage-references-in-a-project"></a>管理專案中的參考

在您針對外部元件或已連線服務撰寫程式碼之前，您的專案首先必須包含所需的參考。 參考其實是在專案檔中的項目，包含 Visual Studio 找出該元件或該服務所需的資訊。

若要新增參考，請以滑鼠右鍵按一下方案總管中的 [參考] 或 [相依性] 節點，然後選擇 [新增參考]。 您也可以用滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **參考**]。 如需詳細資訊，請參閱 [如何：加入或移除參考](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)。

![在 Visual C&#43;&#43; 中新增參考](../ide/media/vs2015_cpp_add_reference.png)

您可以新增下列元件及服務類型的參考：

- .NET 類別庫或組件

- UWP 應用程式

- COM 元件

- 其他組件或相同解決方案中專案的類別庫

- 共用的專案

- XML Web Service

## <a name="uwp-app-references"></a>UWP 應用程式參考

### <a name="project-references"></a>專案參考

通用 Windows 平台 (UWP) 專案可以建立對方案中其他 UWP 專案或者 Windows 8.1 專案或二進位檔的參考，前提是這些專案不使用 Windows 10 中已淘汰的 API。 如需詳細資訊，請參閱 [從 Windows 執行階段 8 移至 UWP](/windows/uwp/porting/w8x-to-uwp-root)。

如果您選擇將 Windows 8.1 專案的目標重定為 Windows 10，請參閱 [移植、遷移及升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md)。

### <a name="extension-sdk-references"></a>延伸模組 SDK 參考

Visual Basic、C#、C++ 和 JavaScript 通用 Windows 平台 (UWP) 應用程式可以參考以 Windows 8.1 為目標的延伸模組 SDK，前提是這些延伸模組 SDK 不使用 Windows 10 中已淘汰的 API。 請檢查延伸模組 SDK 廠商網站，確定是否可 UWP 應用程式參考。

如果您判定不支援您的應用程式所參考的擴充功能 SDK，則需要執行下列步驟：

1. 查看造成錯誤的專案名稱。 您專案的目標平台加註在專案名稱旁邊的括號中。 例如，**MyProjectName (Windows 8.1)** 表示您的專案 **MyProjectName** 的目標平台版本為 Windows 8.1。

1. 移至擁有不受支援之延伸模組 SDK 的廠商網站，並安裝相依性與您專案的目標平台版本相容的延伸模組 SDK 版本。

    > [!NOTE]
    > 找出延伸模組 SDK 是否有其他延伸模組 SDK 相依性的一種方法，是在 **參考管理員** 中尋找。 重新啟動 Visual Studio、建立新的 C# UWP 應用程式專案，然後以滑鼠右鍵按一下專案並選擇 [新增參考]。 依序移至 [Windows] 索引標籤和 [延伸模組] 子索引標籤，然選取延伸模組 SDK。 在 **參考管理員** 的右窗格中尋找。 如果有相依性，則會在那裡列出。

    > [!IMPORTANT]
    > 如果您的專案是以 Windows 10 為目標，且在先前步驟中安裝的延伸模組 SDK 相依於 Microsoft Visual C++ Runtime Package，則與 Windows 10 相容的 Microsoft Visual C++ Runtime Package 版本為 v14.0，並隨著 Visual Studio 一起安裝。

1. 如果您在先前步驟中安裝的延伸模組 SDK 具有其他延伸模組 SDK 的相依性，請移至擁有相依性的廠商網站，並安裝與您專案的目標平台版本相容的這些相依性版本。

1. 重新啟動 Visual Studio，然後開啟您的應用程式。

1. 以滑鼠右鍵按一下導致錯誤之專案中的 [參考] 或 [相依性] 節點，然後選擇 [新增參考]。

1. 依序按一下 [Windows] 索引標籤和 [延伸模組] 子索引標籤，然後針對舊延伸模組 SDK 取消核取方塊，並核取新延伸模組 SDK 的核取方塊。 按一下 [確定]。

## <a name="add-a-reference-at-design-time"></a>在設計階段新增參考

當您在專案中參考組件時，Visual Studio 會搜尋下列位置中的組件：

- 目前專案目錄。 (您可以使用 [瀏覽]  索引標籤尋找這些組件)。

- 同一方案中的其他專案目錄。 (您可以使用 [專案]  索引標籤尋找這些組件。)

> [!NOTE]
> - 所有專案都包含 **mscorlib** 的隱含參考。
> - 所有專案都包含 `System.Core` 的隱含參考，即使 `System.Core` 已從參考清單中移除也一樣。
> - Visual Basic 專案包含 <xref:Microsoft.VisualBasic>的隱含參考。

## <a name="references-to-shared-components-at-run-time"></a>在執行階段參考共用元件

在執行階段中，元件必須位於專案的輸出路徑或全域組件快取 (GAC) 中。 如果專案包含不在這些位置其中之一的物件參考，您必須在建置專案時，將參考複製至專案的輸出路徑。 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 屬性表示是否要進行此複製。 如果值為 **True**，則當您建置專案時，會將參考複製至專案目錄。 如果值為 **False**，則不會複製參考。

如果您部署的應用程式中包含在 GAC 中已註冊自訂元件的參考，則不論 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 設定為何，該元件都不會隨著應用程式一起部署。 在舊版的 Visual Studio 中，您可以在參考上設定 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 屬性以確保組件已部署。 現在，您必須手動將組件加入 \Bin 資料夾。 這會使所有自訂程式碼受到監督，降低您在不熟悉的情況下發行自訂程式碼的風險。

根據預設，如果組件或元件位於全域組件快取或 Framework 元件，則 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 屬性會設定為 **False** 。 否則，值會設定為 **True**。 專案對專案參考一律會設定為 **True**。

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-net"></a>參考以不同 .NET 版本為目標的專案或組件

您可以建立會參考以不同 .NET 版本為目標之專案或組件的應用程式。 例如，您可以建立目標為 .NET Framework 4.6 (參考目標為 .NET Framework 4.5 的組件) 的應用程式。 如果您建立的專案是以舊版 .NET 為目標，則無法在該專案中設定針對以新版為目標之專案或組件的參考。

如需詳細資訊，請參閱 [Framework 目標概觀](../ide/visual-studio-multi-targeting-overview.md)。

## <a name="project-to-project-references"></a>專案對專案參考

專案對專案參考是包含組件的專案參考；您可以使用 [參考管理員] 對話方塊的 [專案] 索引標籤來新增專案參考。 當給定專案路徑時，Visual Studio 即可找出組件。

當您有會產生組件的專案時，您應該參考該專案，而不要使用檔案參考 (請參閱下文)。 專案對專案參考的優點是它會在組建系統中建立專案之間的相依性。 如果自上次建置的參考專案已變更，則將會建立相依專案。 檔案參考不會建立組建相依性，因此可以建置參考專案而不需建置相依專案，且參考可能會遭到淘汰。  (亦即，專案可以參考先前建立的專案版本。 ) 這可能會導致 *bin* 目錄中需要有數個版本的單一 DLL，但這是不可能的。 當發生此衝突時，您會看到一則訊息，例如「警告: 無法將專案 'project' 中的相依性 'file' 複製至執行目錄，因為它會覆寫參考 'file'」。 如需詳細資訊，請參閱[針對中斷參考進行疑難排解](../ide/troubleshooting-broken-references.md)以及[如何：建立和移除專案相依性](../ide/how-to-create-and-remove-project-dependencies.md)。

> [!NOTE]
> 如果某個專案的 .NET Framework 目標版本為 4.5 版，而其他專案的目標版本為第 2 版、第 3 版、3.5 版或 4.0 版，則會建立檔案參考而非專案對專案參考。

## <a name="shared-project-references"></a>共用的專案參考

與大多數其他專案類型不同，「共用的專案」沒有任何二進位輸出。 取而代之的是，程式碼會編譯至參考它的每個專案中。 [共用的專案](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows)可讓您撰寫由一些不同應用程式專案所參考的通用程式碼。 此程式碼會編譯成每個參考專案的一部分，並且可以包含編譯器指示詞，以協助將平台專用功能併入到共用程式碼基底中。 在 [參考管理員] 對話方塊的 [共用的專案] 索引標籤上，新增對共用專案的參考。

## <a name="file-references"></a>檔案參考

檔案參考是 Visual Studio 專案內容外部組件的直接參考。 您可以使用 [參考管理員] 對話方塊的 [瀏覽] 索引標籤來建立它們。 當您只有組件或元件時，請使用檔案參考，不要使用會建立檔案參考作為輸出的專案。

## <a name="see-also"></a>另請參閱

- [針對中斷參考進行疑難排解](../ide/troubleshooting-broken-references.md)
- [如何：新增或移除參考](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
