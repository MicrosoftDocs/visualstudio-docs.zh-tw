---
title: "在 Visual Studio SDK |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e8b1374b6934e09bbf3ce1012d551dab2831292c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="inside-the-visual-studio-sdk"></a>深入探索 Visual Studio SDK
本節提供有關 Visual Studio 擴充功能，包括 Visual Studio 架構、 元件、 服務、 結構描述、 公用程式，以及類似的深入資訊。  
  
## <a name="extensibility-architecture"></a>擴充性架構  
 下圖顯示 Visual Studio 擴充性架構。 Vspackage 提供應用程式功能，以服務的形式在 IDE 之間共用。 標準 IDE 也提供廣泛的服務，例如<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>，這兩個提供 IDE 視窗化功能的存取權。  
  
 ![環境架構圖形](../../extensibility/internals/media/environment.gif "環境")  
Visual Studio 架構一般化的檢視  
  
## <a name="vspackages"></a>VSPackages  
 VSPackage 是使用 UI 項目、服務、專案、編輯器和設計工具來構成和擴充 Visual Studio 的軟體模組。 Vspackage 是 Visual Studio 的中央架構單位。 如需詳細資訊，請參閱[Vspackage](../../extensibility/internals/vspackages.md)。  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 Visual Studio shell 提供基本功能，並支援其元件 Vspackage 和 MEF 擴充功能之間的互通。 如需詳細資訊，請參閱[Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md)。  
  
## <a name="user-experience-guidelines"></a>使用者體驗指南  
 如果您計劃適用於 Visual Studio 中設計新功能，您應該看看這些指導方針來設計和可用性的秘訣： [Visual Studio 使用者經驗指導方針](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## <a name="commands"></a>命令  
 命令是完成工作 (例如，列印文件、重新整理檢視，或建立新檔案) 的功能。  
  
 當您擴充 Visual Studio 時，您可以建立命令，並向 Visual Studio shell。 您可以指定這些命令中將如何顯示在 IDE 中，例如功能表或工具列上。 自訂命令通常會出現在**工具**功能表上，顯示工具視窗的命令就會出現在上**其他視窗** 子功能表**檢視**功能表。  
  
 當您建立的命令時，您也必須為它建立事件處理常式。 事件處理常式決定命令的顯示和啟用，可讓您修改其文字，而且可保證，適當地回應命令時，它便啟動。 在大部分情況下，IDE 會處理命令使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 Visual Studio 中的命令會根據本機選取範圍，並繼續到最外層的內容，根據全域選取範圍的最內層命令內容開始進行處理。 加入主功能表的命令可立即用於指令碼編寫。  
  
 如需詳細資訊，請參閱[命令、 功能表和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)。  
  
## <a name="menus-and-toolbars"></a>功能表和工具列  
 功能表和工具列會提供使用者叫用命令的方式。 功能表是資料列或資料行的命令，通常會顯示為個別的文字工具視窗頂端的項目。 子功能表是當使用者按一下 包含的小箭號的命令時出現的第二個功能表。 當使用者以滑鼠右鍵按一下特定 UI 項目，則會出現內容功能表。 某些常見的功能表名稱是**檔案**，**編輯**，**檢視**，和**視窗**。 如需詳細資訊，請參閱[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 工具列是資料列或資料行的按鈕和其他控制項，例如下拉式方塊、 清單方塊和文字方塊。 工具列按鈕通常會有圖示的影像的資料夾圖示**開啟檔案**命令或印表機**列印**命令。 所有的工具列項目是與命令相關聯。 當您按一下工具列按鈕時，會執行其相關聯的命令。 在下拉式清單控制項，在下拉式清單中的每個項目是與不同的命令相關聯的。 某些工具列控制項，例如分隔器控制項，是混合。 控制項的一邊是工具列按鈕，另一邊則是按一下時其顯示數個命令的向下箭號。  
  
## <a name="tool-windows"></a>工具視窗  
 工具視窗在 IDE 中用於顯示資訊。 **工具箱**，**方案總管 中**，**屬性**視窗中，和**網頁瀏覽器**是工具視窗的範例。  
  
 工具視窗通常會提供各種控制項，使用者可以與之互動。 比方說，**屬性**視窗可讓使用者設定的特定用途的物件屬性。 **屬性**視窗是特製化就這個意義而言，但也廣泛，因為可以用於許多不同情況。 同樣地，**輸出**視窗特製化，因為它會提供以文字為基礎的輸出，但一般，因為 Visual Studio 中的許多子系統可以用它來提供輸出給 Visual Studio 使用者。  
  
 請考慮下列 Visual Studio 中，其中包含數個工具視窗的圖片。  
  
 ![螢幕擷取畫面](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 某些工具視窗會一起停駐在單一的窗格會顯示 [方案總管] 工具視窗也會隱藏其他工具視窗，但可讓它們透過按一下索引標籤上。 圖中會顯示兩個其他工具視窗，**錯誤清單**和**輸出**視窗中，一起停駐單一窗格。  
  
 也顯示是主要的文件窗格中，會顯示數個編輯器視窗。 雖然工具視窗通常會有一個執行個體 (例如，您可以開啟只有一個**方案總管 中**)，編輯器視窗可以有多個執行個體，其中每一個都用來編輯個別的文件，但全部都是停駐在相同的窗格。 圖片顯示文件 窗格具有兩個編輯器視窗、 一個表單設計工具視窗和一個瀏覽器視窗，顯示起始頁。 文件 窗格中的所有視窗都都可以透過按一下索引標籤，但包含 EditorPane.cs 檔案 編輯器 視窗可見且作用中。  
  
 當您擴充 Visual Studio 時，您可以建立與您的擴充功能的工具視窗，可讓 Visual Studio 使用者互動。 您也可以建立您自己的編輯器，讓 Visual Studio 使用者可以編輯文件。 因為編輯器和工具視窗將會整合至 Visual Studio 中，您不必撰寫這些固定或正確的索引標籤會顯示。 當它們正確註冊 Visual Studio 中時，它們會自動提供工具視窗與文件視窗，在 Visual Studio 中的一般的功能。 如需詳細資訊，請參閱[延伸和自訂工具視窗](../../extensibility/extending-and-customizing-tool-windows.md)。  
  
## <a name="document-windows"></a>文件視窗  
 文件視窗是多重文件介面 (MDI) 視窗的框架的子視窗。 文件視窗通常用來裝載在文字編輯器、 表單編輯器 （也稱為設計工具） 或編輯控制項，但它們也可以裝載其他功能的類型。 **新檔案**對話方塊包含 Visual Studio 提供的文件視窗的範例。  
  
 大部分的編輯器的特定程式的語言或檔案類型，例如 HTML 頁面、 框架、 c + + 檔案或標頭檔。 選取的範本**新檔案**對話方塊中，使用者會動態建立的文件視窗與範本相關聯之檔案類型的編輯器。 當使用者開啟現有的檔案，也會建立文件視窗。  
  
 文件視窗會限制為在 MDI 工作區。 每個文件視窗的最上方有索引標籤，並且可能在 MDI 區開啟其他視窗連結 索引標籤順序。 以滑鼠右鍵按一下文件視窗的索引標籤顯示捷徑功能表，其中包括 MDI 區域分割成多個水平或垂直索引標籤群組的選項。 分割 MDI 區域可讓同時檢視多個檔案。 如需詳細資訊，請參閱[文件視窗](../../extensibility/internals/document-windows.md)。  
  
## <a name="editors"></a>編輯器  
 Visual Studio 編輯器可讓您自訂，並使用您自己的內容類型的 Managed Extensibility Framework (MEF) 使用。 在許多情況下您不需要建立 VSPackage 也可以擴充編輯器，不過如果您想要包含在命令介面 （例如，功能表命令或快速鍵） 中的功能，您可以結合 MEF 擴充功能的 VSPackage。  
  
 您也可以建立自訂編輯器，例如，如果您想要讀取和寫入至資料庫，或如果您想要使用的設計工具。 您也可以使用外部編輯器例如記事本或 Microsoft WordPad。 如需詳細資訊，請參閱[編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。  
  
## <a name="language-services"></a>語言服務  
 如果您想要支援新的程式設計關鍵字或甚至新的程式設計語言的 Visual Studio 編輯器，您可以建立語言服務。 每個語言服務可能會實作特定編輯器功能完整、 部分，或完全無法執行。 根據其設定方式，語言服務可提供語法反白顯示、 括號對稱、 IntelliSense 支援，與編輯器中的其他功能。  
  
 語言服務的核心是剖析器與掃描器。 掃描器 （或 lexer） 的原始程式檔分成稱為 「 語彙基元的項目，剖析器會建立這些語彙基元之間的關聯性。 當您建立語言服務時，您必須實作剖析器與掃描器，如此語彙基元和文法的語言，可以了解 Visual Studio。 您可以建立 managed 或 unmanaged 語言服務。 如需詳細資訊，請參閱[舊版語言服務擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)。  
  
## <a name="projects"></a>專案  
 在 Visual Studio 專案是開發人員用來組織和建立原始程式碼與其他資源的容器。 專案可讓您組織、 建置、 偵錯及部署原始程式碼，請參考 Web 服務、 資料庫和其他資源。 Vspackage 可以擴充 Visual Studio 專案系統提供的專案類型和專案子類型，並自訂工具。  
  
 專案也可能會收集到解決方案，這是一個或多個一起工作，以建立應用程式的專案分組。 屬於方案的專案及狀態資訊會儲存在兩個方案檔案，以文字為基礎的方案 (.sln) 檔案和二進位的解決方案使用者選項 (.suo) 檔案。 這些檔案是較舊版本中所使用的群組 (.vbg) 檔案類似[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]，和工作區 (.dsw) 和使用者選項 (.opt) 檔案中的舊版本所使用的[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]。  
  
 如需詳細資訊，請參閱[專案](../../extensibility/internals/projects.md)和[解決方案](../../extensibility/internals/solutions.md)。  
  
## <a name="project-and-item-templates"></a>專案和項目範本  
 Visual Studio 包含預先定義的專案範本和專案項目範本。 您可以也會使您自己的範本或取得來自社群的範本，並再將它們整合到 Visual Studio。 [MSDN Code Gallery](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio)是範本和擴充功能的地方。  
  
 範本中包含的專案結構和建立特定種類的應用程式、 控制項、 程式庫或類別所需的基本檔案。 當您想要開發軟體，類似於其中一個範本時，建立範本為基礎的專案，然後修改 該專案中的檔案。  
  
> [!NOTE]
>  不支援此範本架構[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案。 如需如何建立[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案範本，請參閱[設計精靈](/cpp/ide/designing-a-wizard)。  
  
 如需詳細資訊，請參閱[加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
## <a name="properties-and-options"></a>屬性和選項  
 **屬性**視窗會顯示單一或多個選取的項目屬性：[擴充屬性](../../extensibility/internals/extending-properties.md)選項 頁面包含設定的選項，例如屬於特定元件，程式設計語言或 VSPackage:[選項和 [選項] 頁](../../extensibility/internals/options-and-options-pages.md)。 設定是通常與 UI 相關的功能，可以匯入和匯出：[支援使用者設定](../../extensibility/internals/support-for-user-settings.md)。  
  
## <a name="visual-studio-services"></a>Visual Studio 服務  
 提供一組特定的介面元件，以取用服務。 Visual Studio 會提供一組可供任何元件，包括擴充功能的服務。 例如，Visual Studio 服務可讓工具視窗以顯示或隱藏起來，以動態方式啟用說明、 狀態列或使用者事件的存取權。 在 Visual Studio 編輯器也提供可匯入的編輯器延伸模組的服務。 如需詳細資訊，請參閱[使用並提供服務](../../extensibility/using-and-providing-services.md)。  
  
## <a name="debugger"></a>偵錯工具  
 偵錯工具是特定語言偵錯元件使用者介面。 如果您已經建立新的語言服務，您必須建立偵錯工具中攔截特定的偵錯引擎。 如需詳細資訊，請參閱[Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)。  
  
## <a name="source-control"></a>原始檔控制  
 實作原始檔控制外掛程式或 VSPackage 的詳細資訊，請參閱[原始檔控制](../../extensibility/internals/source-control.md)。  
  
## <a name="wizards"></a>精靈  
 您可以使用新的專案類型搭配建立精靈，在建立新的專案，該類型時，您的使用者，讓此精靈可協助做出正確的決策。 如需詳細資訊，請參閱[精靈](../../extensibility/internals/wizards.md)。  
  
## <a name="custom-tools"></a>自訂工具  
 自訂工具可讓您將工具與專案中的項目產生關聯，並執行該工具，每次您儲存檔案。 如需詳細資訊，請參閱[自訂工具](../../extensibility/internals/custom-tools.md)。  
  
## <a name="vssdk-utilities"></a>VSSDK 公用程式  
 VSSDK 包含一組公用程式，您可能需要為了使用 Vspackage 的不同層面。 如需詳細資訊，請參閱[VSSDK 公用程式](../../extensibility/internals/vssdk-utilities.md)。  
  
## <a name="using-windows-installer"></a>使用 Windows Installer  
 在某些情況下，您可能需要使用 Windows Installer，而不是 VSIX 安裝程式： 例如，您可能需要寫入登錄。 如需使用 Windows 安裝程式搭配您的擴充功能資訊，請參閱[與 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。  
  
## <a name="help-viewer"></a>說明檢視器  
 您可以整合您自己的說明和 F1 說明檢視器。 如需詳細資訊，請參閱[Microsoft 說明檢視器 SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)。