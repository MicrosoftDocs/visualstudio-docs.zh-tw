---
title: HOW TO：新增或移除參考，可以使用 參考管理員 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- Visual C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
ms.assetid: 1aabb520-99b0-46c6-9368-21b4d84793eb
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 54d64fd59e71b582548aa5efade8d45a24ddb560
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701161"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>作法：新增或移除參考，可以使用 參考管理員
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

針對由您本身、Microsoft 或其他公司所開發的元件，您可以使用 [參考管理員] 對話方塊新增並管理這些元件的參考。 如果您正在開發通用 Windows app，您的專案會自動參考所有正確的 Windows SDK DLL。 如果您正在開發 .NET 應用程式，您的專案會自動參考 mscorlib.dll。 某些 .NET API 是在您手動加入的元件中公開。 您必須手動加入對 COM 元件或自訂元件的參考。  
  
## <a name="adding-and-removing-a-reference"></a>加入和移除參考  
  
#### <a name="to-add-a-reference"></a>加入參考  
  
1. 在方案總管中，以滑鼠右鍵按一下 [參考] 節點，然後選擇 [加入參考]。  
  
2. 指定要新增的參考，然後選擇 [確定] 按鈕。  
  
   [參考管理員] 隨即開啟，並依群組列出可用的參考。 專案類型決定下列哪些群組會出現：  
  
- 組件，包含 [Framework] 和 [擴充功能] 子群組。  
  
- 方案，包含 [專案] 子群組。  
  
- Windows，包含 [核心] 和 [擴充功能] 子群組。 您可以使用 [物件瀏覽器] 探索 Windows SDK 或延伸模組 SDK 中的參考。  
  
- 瀏覽，包含 [最近] 子群組。  
  
## <a name="assemblies-tab"></a>組件索引標籤  
 [組件] 索引標籤會列出可供參考的所有 .NET Framework 組件。 [組件] 索引標籤不會列出全域組件快取 (GAC) 中的任何組件，因為 GAC 中的組件是執行階段環境的一部分。 如果您部署或複製的應用程式中包含在 GAC 中註冊之元件的參考，則不論 [複製到本機] 設定為何，該組件都不會隨著應用程式一起部署或複製。 如需詳細資訊，請參閱[專案參考](http://go.microsoft.com/fwlink/?LinkId=238512)。  
  
 當您手動將參考加入任一個 EnvDTE 命名空間 (EnvDTE、EnvDTE80、EnvDTE90、EnvDTE90a 或 EnvDTE100) 的參考時，請在 [屬性] 視窗中將參考的 [內嵌 Interop 類型] 屬性設定成 False。 如果將此屬性設成 True，可能會導致組建問題，因為某些 EnvDTE 屬性是無法內嵌的。  
  
 所有傳統型專案都包含 mscorlib 的隱含參考。 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 專案包含 Microsoft.VisualBasic 的隱含參考。 在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 中，所有專案都包含 System.Core 的隱含參考，即使已從參考清單中移除也一樣。  
  
 如果專案類型不支援 [組件]，這個索引標籤就不會出現在 [參考管理員] 對話方塊中。  
  
 [組件] 索引標籤包括兩個子索引標籤：  
  
1. [Framework] 會列出組成目標 Framework 的所有組件。  
  
   - 通告的組件為完整 Framework，並且會在您的專案以目標 Framework 的設定檔為目標時，於 [Framework] 清單中列舉。 通告的組件會以灰色顯示，以便與專案的目標 Framework 設定檔中的組件做出區分。 例如，如果專案是以 .NET Framework 4 Client 為目標，則 [Framework] 清單中會顯示 .NET Framework 4 中通告的組件。 當使用者新增通告的組件時，系統會告知使用者，專案將在 [參考管理員] 對話方塊關閉之後，重定目標為 .NET Framework 4，並新增通告的組件。  
  
   - [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]應用程式的專案預設包含專案建立時，目標[!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] 中所有組件的參考。 在 Managed 專案中，方案總管 [參考] 資料夾下的唯讀節點表示整個 Framework 的參考。 因此，[Framework] 索引標籤不會列舉任何從 Framework 組件，並改為顯示下列訊息：「 所有 Framework 組件都已經被參考。 請使用物件瀏覽器瀏覽 Framework 中的參考」。 對於傳統型專案，[Framework] 索引標籤會列舉目標 Framework 中的組件，而且使用者必須加入應用程式所需的參考。  
  
2. [擴充功能] 會列出外部元件和控制項廠商為了擴充目標 Framework 所開發的全部組件。 根據使用者應用程式的用途，可能會需要這些組件。  
  
   - 填入擴充功能的方式是列舉下列位置所註冊的組件：  
  
       ```  
       32-bit machine:  
       HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       64-bit machine:  
       HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       And older versions of the [Target Framework Identifier]  
       ```  
  
        例如，如果專案在 32 位元電腦上的目標是 .NET Framework 4，則延伸模組會列舉 \Microsoft\\.NETFramework\v4.0\AssemblyFoldersEx\\、\Microsoft\\.NETFramework\v3.5\AssemblyFoldersEx\\、\Microsoft\\.NETFramework\v3.0\AssemblyFoldersEx\\ 及 \Microsoft\\.NETFramework\v2.0\AssemblyFoldersEx\\ 下註冊的組件。  
  
   視專案的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本而定，清單中的部分元件可能不會顯示。 在下列狀況下可能會發生這種情形：  
  
- 使用最近版本 .NET Framework 的元件，與目標針對舊版 .NET Framework 的專案並不相容。  
  
     如需如何為專案變更目標 .NET Framework 版本的資訊，請參閱[如何：以一個 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
- 使用 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 的元件與目標針對 [!INCLUDE[net_v45](../includes/net-v45-md.md)] 的專案不相容。  
  
     當您建立新的應用程式時，有些專案預設會以 [!INCLUDE[net_v45](../includes/net-v45-md.md)] 為目標。 如需詳細資訊，請參閱 [.NET Framework Client Profile](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)。  
  
- 您應該避免將檔案參考加入至同一方案中的其他專案輸出，因為這麼做可能會造成編譯錯誤。 請改用 [加入參考] 對話方塊中的 [專案] 索引標籤，來建立專案對專案間的參考。 這樣一來就能夠更有效的管理在專案中所建立的類別庫，使得小組開發更為容易。 如需詳細資訊，請參閱[針對中斷參考進行疑難排解](../ide/troubleshooting-broken-references.md)。  
  
- > [!NOTE]
    > 在 Visual Studio 2015 中，如果某個專案的 .NET Framework 目標版本為第 4.5 版，而其他專案的目標版本為第 2 版、第 3 版、第 3.5 版或第 4.0 版，則會建立檔案參考而非專案參考。  
  
#### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>若要在加入參考對話方塊中顯示組件  
  
- 將組件移動或複製至下列其中一個位置：  
  
  - 目前專案目錄。 (您可以使用 [瀏覽]  索引標籤尋找這些組件)。  
  
  - 同一方案中的其他專案目錄。 (您可以使用 [專案] 索引標籤尋找這些組件)。  
  
    \-或-  
  
- 設定用以指定組件顯示位置的登錄機碼：  
  
   針對 32 位元的作業系統，請加入下列登錄機碼之一。  
  
  - [HKEY_CURRENT_USER\SOFTWARE\Microsoft\\.NETFramework\\<最低版本>\AssemblyFoldersEx\MyAssemblies]@="組件位置"  
  
  - [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\\<最低版本>\AssemblyFoldersEx\MyAssemblies]@="組件位置"  
  
    針對 64 位元的作業系統，請在 32 位元登錄區中，加入下列登錄機碼之一。  
  
  - [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\<最低版本>\AssemblyFoldersEx\MyAssemblies]@="組件位置"  
  
  - [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\<最低版本>\AssemblyFoldersEx\MyAssemblies]@="組件位置"  
  
    <最低版本> 是適用的最低 .NET Framework 版本。 如果 <最低版本>是 3.0 版，則 AssemblyFoldersEx 中指定的資料夾適用於以 .NET Framework 3.0 (含) 以後版本為目標的專案。  
  
    <組件位置> 代表您想要在 [加入參考] 對話方塊中顯示的組件目錄，例如 C:\MyAssemblies\\。  
  
    在 HKEY_LOCAL_MACHINE 節點下建立登錄機碼，可讓所有使用者都能在 [加入參考] 對話方塊中看到指定位置的組件。 在 HKEY_CURRENT_USER 節點下建立登錄機碼，只會影響目前使用者的設定。  
  
    再次開啟 [加入參考] 對話方塊。 組件應該會出現在 [.NET] 索引標籤上。如果沒有顯示，請確認組件位於指定的 <組件位置> 目錄中，然後重新啟動 Visual Studio 並再試一次。  
  
## <a name="com-tab"></a>COM 索引標籤  
 [COM] 索引標籤會列出所有可供參考的 COM 元件。 如果您要將參考加入包含內部資訊清單的已註冊 COM DLL，請先移除註冊 DLL。 否則 Visual Studio 會將組件參考加入為 ActiveX 控制項，而不是原生 DLL。  
  
 如果專案類型不支援 [COM]，這個索引標籤就不會出現在 [參考管理員] 對話方塊中。  
  
## <a name="solution-tab"></a>方案索引標籤  
 [方案] 索引標籤會列出目前方案的 [專案] 子索引標籤內所有相容的專案。  
  
 專案可以參考以不同 .NET Framework 版本為目標的其他專案。 例如，您可以建立以 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 為目標，但是參考針對 .NET Framework 2 所建置之組件的專案。 不過，.NET Framework 2 專案無法參考 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 專案。 如需詳細資訊，請參閱[以特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)。  
  
 目標為 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 的專案與目標為 [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] 的專案不相容。  
  
 在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 中，如果專案的目標為 .NET Framework 4，而另一個專案的目標為舊版，則會建立檔案參考而不是專案參考。  
  
 目標為 [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] 的專案無法將專案參考加入至目標為 .NET Framework 的專案，反之亦然。  
  
## <a name="windows-tab"></a>Windows 索引標籤  
 [Windows] 索引標籤會列出 Windows 作業系統執行所在平台專用的 SDK。  
  
 您可以在 Visual Studio 中透過兩種方式產生 WinMD 檔案：  
  
- **[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式 Managed 專案**：[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式專案可以透過設定 [專案屬性 &#124; 輸出類型 = WinMD 檔案] 的方式輸出 WinMD 二進位檔。 WinMD 檔案名稱必須是本身包含之所有命名空間的超集命名空間。 例如，如果專案包括命名空間 A.B 和 A.B.C，則其輸出的 WinMD 可能名稱為 A.winmd 和 A.B.winmd。 如果使用者輸入專案屬性&#124;組件名稱或專案屬性&#124;是從專案中的命名空間集合不相鄰的命名空間值或在專案內沒有超集命名空間，會產生建置警告：'A.winmd' 不是這個組件的有效.winmd 檔案名稱。 Windows 中繼資料檔中的所有類型都必須存在檔案名稱的子命名空間內。 在執行階段將找不到不存在檔案名稱之子命名空間中的類型。 在這個組件中，最小通用命名空間為 'CSWSClassLibrary1'。 傳統型 Visual Basic 或 Visual C# 專案只能使用以 [!INCLUDE[win8](../includes/win8-md.md)] SDK 產生的 WinMD，它稱為第一方 WinMD 而且無法產生 WinMD。  
  
- **[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式的原生專案**:原生 WinMD 檔案只包含中繼資料。 它的實作會出現在個別 DLL 中。 在 [新增專案] 對話方塊中選擇 Windows 執行階段元件專案範本，或是從空白專案開始並修改專案屬性來產生 WinMD 檔案，就可以產生原生二進位檔。 如果專案包含不相鄰的命名空間，則會產生建置錯誤，告訴使用者將其命名空間結合或執行 MSMerge 工具。  
  
  [Windows] 索引標籤包括兩個子群組。  
  
### <a name="core-subgroup"></a>核心子群組  
 [核心] 子群組會列出目標版本 Windows 的 SDK 中所有的 WinMD (針對 Windows 執行階段項目)。  
  
 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式專案預設包含專案建立時，[!INCLUDE[win8](../includes/win8-md.md)] SDK 中的所有 WinMD 參考。 在 Managed 專案中，方案總管 [參考] 資料夾下的唯讀節點表示整個 [!INCLUDE[win8](../includes/win8-md.md)] 的參考。 因此，在參考管理員 中的 [核心] 子群組不會列舉任何組件從[!INCLUDE[win8](../includes/win8-md.md)]SDK，並改為顯示一則訊息：「 Windows SDK 已經被參考。 請使用物件瀏覽器瀏覽 Windows SDK 中的參考」。  
  
 根據預設，在傳統型專案中，[核心] 子群組不會出現。 您可以開啟專案節點的捷徑功能表、選擇 [卸載專案]、加入下列程式碼片段，然後重新開啟專案 (在專案節點上選擇 [重新載入專案])，即可新增 Windows 執行階段。 當您叫用 [參考管理員] 對話方塊時，[核心] 子群組隨即出現。  
  
```  
<PropertyGroup>  
  <TargetPlatformVersion>8.0</TargetPlatformVersion>  
</PropertyGroup>  
```  
  
 確定已在這個子群組上選取 [Windows] 核取方塊。 接著您應該就能使用 Windows 執行階段項目。 不過，您可能也會想要加入 System.Runtime，讓 Windows 執行階段定義一些標準類別和介面，例如 IEnumerable，以便在整個 Windows 執行階段程式庫中使用。 如需如何加入 System.Runtime 的詳細資訊，請參閱[受管理的傳統型應用程式與 Windows 執行階段](https://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types)。  
  
### <a name="extensions-subgroup"></a>擴充功能子群組  
 [擴充功能] 會列出擴充目標 Windows 平台的使用者 SDK。 這個索引標籤只會針對 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式專案顯示。 傳統型專案不會顯示這個索引標籤，因為這類專案只能使用第一方 .winmd 檔案。  
  
 SDK 是檔案集合，Visual Studio 會將這個集合視為單一元件。 在 [延伸模組] 索引標籤中，適用於叫用 [參考管理員] 對話方塊所在專案的 SDK 會以單一項目形式列出。 加入至專案時，Visual Studio 會使用所有 SDK 內容，因此使用者不需要採取任何進一步動作就可以在 IntelliSense、工具箱、設計工具、物件瀏覽器、組建、部署、偵錯和封裝中利用 SDK 內容。 如需如何在 [延伸模組] 索引標籤中顯示 SDK 的詳細資訊，請參閱[建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)。  
  
> [!NOTE]
> 如果專案參考的 SDK 取決於另一個 SDK，除非使用者手動加入另一個 SDK 的參考，否則 Visual Studio 不會使用另一個 SDK。 當使用者在 [延伸模組] 索引標籤上選擇 SDK 時，[參考管理員] 對話方塊除了列出 SDK 的名稱和版本之外，還會在詳細資料窗格中列出所有 SDK 相依性的名稱，藉此幫助使用者識別 SDK。 如果使用者未注意到相依性而只加入該 SDK，MSBuild 將會提示使用者加入相依性。  
  
 如果專案類型不支援 [延伸模組]，這個索引標籤就不會出現在 [參考管理員] 對話方塊中。  
  
## <a name="browse-button"></a>瀏覽按鈕  
 您可以使用 [瀏覽] 按鈕，瀏覽檔案系統中的元件。  
  
 專案可以參考以不同 .NET Framework 版本為目標的元件。 例如，您可以建立目標為 .NET Framework 4 Client Profile，但參考目標為 .NET Framework 2 之元件的應用程式。 如需詳細資訊，請參閱[以特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)。  
  
 您應該避免將檔案參考加入至同一方案中的其他專案輸出，因為這種做法可能會造成編譯錯誤。 請改用 [參考管理員] 對話方塊中的 [方案] 索引標籤來建立專案對專案間的參考。 這種做法能夠更有效的管理您在專案中所建立的類別庫，使得小組開發更為容易。 如需詳細資訊，請參閱[針對中斷參考進行疑難排解](../ide/troubleshooting-broken-references.md)。  
  
 您無法瀏覽至 SDK，並將它加入至您的專案。 您只能瀏覽至檔案 (例如，組件或 .winmd)，並將它加入至專案。  
  
 進行對 WinMD 的檔案參考時，預期的配置是將 <檔案名稱>.winmd、<檔案名稱>.dll 和 <檔案名稱>.pri 檔案全部放置在一起。 如果您在下列情境中參考 WinMD，會將不完整的檔案集合複製到專案輸出目錄中，因此造成建置和執行階段失敗發生。  
  
- **原生元件**：原生專案會為每一個不相鄰的命名空間集合建立一個 WinMD，並且建立一個包含實作的 DLL。 WinMD 會有不同的名稱。 參考這個原生元件檔時，MSBuild 不會將採用不同名稱的 WinMD 辨識為同一個元件。 因此，只會複製名稱相同的 <檔案名稱>.dll 和 <檔案名稱>.winmd，並會發生執行階段錯誤。 若要解決這個問題，請建立擴充功能 SDK。 如需詳細資訊，請參閱[建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)。  
  
- **使用控制項**：XAML 控制項至少包含 <檔案名稱>.winmd、<檔案名稱>.dll、<檔案名稱>.pri、<XAML 名稱>.xaml 和 <影像名稱>.jpg。 專案建置後，系統不會將已與檔案參考建立關聯的資源檔複製到專案的輸出目錄中，而只會複製 <檔案名稱>.winmd、<檔案名稱>.dll 和 <檔案名稱>.pri。 此時會記錄建置錯誤，通知使用者遺漏 <XAML 名稱>.xaml 和 <影像名稱>.jpg 資源。 若要成功，使用者必須手動將這些資源檔複製到專案輸出目錄中供建置和偵錯/執行階段使用。 若要解決這個問題，請遵循[建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)中的步驟建立延伸模組 SDK，或編輯專案檔以新增下列屬性：  
  
    ```  
    <PropertyGroup>  
    <GenerateLibraryOutput>True</GenerateLibraryOutput>  
    </PropertyGroup>  
    ```  
  
    > [!NOTE]
    > 如果您加入屬性，建置執行速度可能會變慢。  
  
## <a name="recent"></a>最近  
 [組件]、[COM]、[Windows] 和 [瀏覽] 各支援一個 [最近] 索引標籤，其中會列舉最近加入專案中的元件清單。  
  
## <a name="search"></a>搜尋  
 [參考管理員] 對話方塊中的搜尋列會在成為焦點的索引標籤上運作。 好比說，如果使用者在 [方案] 索引標籤成為焦點時於搜尋列中鍵入 "System"，除非方案擁有包含 "System" 的專案名稱，否則搜尋不會傳回任何結果。  
  
## <a name="see-also"></a>另請參閱  
 [NIB 如何：新增或移除參考使用加入參考對話方塊](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [管理專案中的參考](../ide/managing-references-in-a-project.md)
