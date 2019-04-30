---
title: 深入探索 Visual Studio SDK |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078bf457c798c0be9ac56aad1859c6750881922a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909655"
---
# <a name="inside-the-visual-studio-sdk"></a>深入探索 Visual Studio SDK

本節提供有關 Visual Studio 擴充功能，包括 Visual Studio 架構、 元件、 服務、 結構描述、 公用程式，以及類似的深入資訊。

## <a name="extensibility-architecture"></a>擴充性架構
 下圖顯示 Visual Studio 擴充性架構。 Vspackage 提供的應用程式功能，它會在 IDE 之間共用，為服務。 標準的 IDE 也提供各種服務，例如<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>，提供 IDE 視窗化功能的存取權。

 ![環境架構圖形](../../extensibility/internals/media/environment.gif "環境")一般化的 Visual Studio 架構檢視

## <a name="vspackages"></a>VSPackages
 VSPackage 是使用 UI 項目、服務、專案、編輯器和設計工具來構成和擴充 Visual Studio 的軟體模組。 Vspackage 是 Visual Studio 的中央架構單位。 如需詳細資訊，請參閱 [VSPackages](../../extensibility/internals/vspackages.md)。

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Visual Studio shell 提供的基本功能，並支援其元件的 Vspackage 和 MEF 擴充功能之間的跨通訊。 如需詳細資訊，請參閱 < [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md)。

## <a name="user-experience-guidelines"></a>使用者體驗指南
 如果您計劃適用於 Visual Studio 中設計的新功能，您應該看看這些指導方針來設計和可用性的秘訣：[Visual Studio 使用者經驗指導方針](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。

## <a name="commands"></a>命令
 命令是完成工作 (例如，列印文件、重新整理檢視，或建立新檔案) 的功能。

 當您擴充 Visual Studio 時，您可以建立命令，並向 Visual Studio shell。 您可以指定如何這些命令會顯示在 IDE 中，例如功能表或工具列上。 自訂命令通常會出現在**工具**功能表，然後顯示工具視窗的命令會出現在**其他 Windows**  子功能表**檢視**功能表。

 當您建立的命令時，則您也必須為其建立事件處理常式。 事件處理常式會判斷命令可看見或是已啟用，可讓您修改它的文字，以及保證，適當地回應命令何時啟動。 在大部分情況下，IDE 會處理命令使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 在 Visual Studio 中的命令會開始根據本機選取範圍，並繼續到最外層的內容，根據全域選取範圍的最內層命令內容來處理。 加入主功能表的命令可立即用於指令碼編寫。

 如需詳細資訊，請參閱 <<c0> [ 命令、 功能表和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)。

## <a name="menus-and-toolbars"></a>功能表和工具列
 功能表和工具列為使用者提供方法來叫用命令。 功能表是資料列或資料行的命令，通常會顯示為個別的文字工具視窗頂端的項目。 子功能表會出現在使用者按一下包含的小箭號的命令時的第二個功能表。 當使用者以滑鼠右鍵按一下特定 UI 項目，則會出現內容功能表。 部分常見的功能表名稱不**檔案**，**編輯**，**檢視**，以及**視窗**。 如需詳細資訊，請參閱 <<c0> [ 擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。

 工具列是資料列或資料行的按鈕和其他控制項，例如下拉式方塊、 清單方塊和文字方塊。 工具列按鈕通常會有圖示的影像的資料夾圖示**開啟的檔案**命令或印表機**列印**命令。 所有的工具列項目都與命令相關聯。 當您按一下工具列按鈕時，會執行其相關聯的命令。 在下拉式清單控制項，在下拉式清單中的每個項目是與不同的命令相關聯。 某些工具列控制項，例如分隔器控制項，是混合環境。 控制項的一邊是工具列按鈕和的另一面是它按一下就會顯示數個命令的向下箭號。

## <a name="tool-windows"></a>工具視窗
 工具視窗可在 IDE 中顯示的資訊。 **工具箱**，**方案總管**，**屬性**視窗中，並**網頁瀏覽器**是工具視窗範例。

 工具視窗通常會提供各種使用者可以與之互動的控制項。 比方說，**屬性**視窗可讓使用者設定屬性的物件，提供特定的用途。 **屬性**視窗是在這種情況下，特製化，但也一般，因為它可以用於許多不同的情況。 同樣地，**輸出**視窗特製化，因為它會提供以文字為基礎的輸出，但一般，因為在 Visual Studio 中的許多子系統可以用它來提供輸出給 Visual Studio 使用者。

 請考慮下圖的 Visual Studio 中，其中包含數個工具視窗：

 ![螢幕擷取畫面](../../extensibility/internals/media/t1gui.png "T1gui")

 部分工具視窗會一起停駐的單一窗格會顯示 [方案總管] 工具視窗，也會隱藏其他工具視窗但使其可供透過按一下索引標籤。 圖中會顯示兩個其他的工具視窗中，**錯誤清單**並**輸出**視窗中，一起停駐的單一窗格。

 也會顯示為主要的文件 窗格會顯示數個編輯器視窗。 雖然工具視窗通常會有一個執行個體 (例如，您可以在此處開啟只有一個**方案總管 中**)，編輯器視窗可以有多個執行個體，每一個都用來編輯個別的文件，但全部都停駐在同一個窗格中。 圖顯示具有兩個編輯器視窗、 一個表單設計工具視窗的文件 窗格。 文件 窗格中的所有視窗都都可以透過按一下索引標籤上，但包含 EditorPane.cs 檔案的 編輯器 視窗可見且作用中。

 當您擴充 Visual Studio 時，您可以使用您的延伸模組來建立的工具視窗，可以讓 Visual Studio 使用者互動。 您也可以建立您自己的編輯器，可讓 Visual Studio 使用者編輯文件。 因為您的工具視窗和編輯器將會整合到 Visual Studio 中，您不必撰寫它們來停駐或正確地顯示在索引標籤。 當它們正確地註冊 Visual Studio 中時，它們會自動在工具視窗和文件視窗，在 Visual Studio 中的一般功能。 如需詳細資訊，請參閱 <<c0> [ 延伸和自訂工具 Windows](../../extensibility/extending-and-customizing-tool-windows.md)。

## <a name="document-windows"></a>文件視窗
 文件視窗是一個已框架處理的子視窗之多重文件介面 (MDI) 視窗。 文件視窗通常用來裝載在文字編輯器、 表單編輯器 （也稱為設計工具） 或編輯控制項，但它們也可以裝載其他功能的類型。 **新的檔案**對話方塊包含 Visual Studio 提供的文件視窗的範例。

 大部分的編輯器的程式設計語言或檔案類型，例如 HTML 頁面，框架，特定C++檔案或標頭檔。 選取的範本**新的檔案** 對話方塊中，使用者以動態方式建立的文件視窗與範本相關聯的檔案類型的編輯器。 當使用者開啟現有的檔案，也會建立文件視窗。

 文件視窗僅限於在 MDI 工作區。 每個文件視窗具有 索引標籤的上方、 且定位順序連結至其他可能是 MDI 區域中開啟的視窗。 以滑鼠右鍵按一下  索引標籤的文件視窗會顯示捷徑功能表，其中包括將 MDI 區域分割成多個水平或垂直索引標籤群組的選項。 分割 MDI 區域可讓同時檢視多個檔案。 如需詳細資訊，請參閱 <<c0> [ 文件 Windows](../../extensibility/internals/document-windows.md)。

## <a name="editors"></a>編輯器
 Visual Studio 編輯器可讓您自訂它，並使用您自己的內容類型的 Managed Extensibility Framework (MEF) 透過。 在許多情況下您不需要建立 VSPackage 也可以擴充編輯器，但如果您想要包含從殼層 （例如，功能表命令或攠摝坫） 的功能，您可以結合 MEF 擴充功能和 VSPackage。

 您也可以建立自訂編輯器，例如，如果您想要讀取和寫入至資料庫，或如果您想要使用設計工具。 您也可以使用外部編輯器例如記事本或 Microsoft WordPad。 如需詳細資訊，請參閱 <<c0> [ 編輯器和語言服務延伸模組](../../extensibility/editor-and-language-service-extensions.md)。

## <a name="language-services"></a>語言服務
 如果您想要支援新的程式設計關鍵字或甚至是新的程式設計語言的 Visual Studio 編輯器，您會建立語言服務。 每個語言服務可能會實作特定編輯器功能完整、 部分，或完全不用。 根據其設定方式，語言服務可以提供語法反白顯示、 括號對稱、 IntelliSense 支援，以及在編輯器中的其他功能。

 語言服務的核心是剖析器和掃描器。 掃描器 （或 lexer） 的原始程式檔分成稱為 「 語彙基元的項目，並剖析器會建立這些語彙基元之間的關聯性。 當您建立語言服務時，您必須實作剖析器和掃描器，使 Visual Studio 可以了解語彙基元和語言的文法。 您可以建立 managed 或 unmanaged 的語言服務。 如需詳細資訊，請參閱 <<c0> [ 舊版語言服務的擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)。

## <a name="projects"></a>專案

在 Visual Studio 中，專案會是開發人員用來組織及建置的原始程式碼和其他資源的容器。 可讓您組織、 建置、 偵錯及部署來源的程式碼的專案，請參考 Web 服務、 資料庫和其他資源。 Vspackage 可以擴充 Visual Studio 專案系統所提供的專案類型、 專案子類型，以及自訂的工具。

專案可能也一起收集*解決方案*，這是一群共同運作以建立應用程式的一或多個專案。 屬於方案的專案和狀態資訊會儲存在兩個方案檔，以文字為基礎[方案 (.sln) 檔案](solution-dot-sln-file.md)和二元[方案使用者選項 (.suo) 檔案](solution-user-options-dot-suo-file.md)。 這些檔案是類似於在舊版的 Visual Basic 中，所使用的群組 (.vbg) 檔案，以及工作區 (.dsw) 和使用者選項 (.opt) 檔案中較早版本所使用的C++。

如需詳細資訊，請參閱 <<c0> [ 專案](../../extensibility/internals/projects.md)並[解決方案](../../extensibility/internals/solutions-overview.md)。

## <a name="project-and-item-templates"></a>專案與項目範本
 Visual Studio 包含預先定義的專案範本和專案項目範本。 您可以也讓您自己的範本或取得社群中的範本，並再將它們整合到 Visual Studio。 [MSDN Code Gallery](https://code.msdn.microsoft.com/site/search?query=visual%20studio)是範本和擴充功能的位置。

 範本包含的專案結構和基本建置特定類型的應用程式、 控制項、 程式庫或類別所需的檔案。 當您想要開發的軟體，類似於其中一個範本時，建立以範本為基礎的專案，然後修改 該專案中的檔案。

> [!NOTE]
> 此範本架構不支援[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案。

 如需詳細資訊，請參閱 <<c0> [ 加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。

## <a name="properties-and-options"></a>屬性和選項
 **屬性**視窗會顯示單一或多個選取的項目屬性：[擴充屬性](../../extensibility/internals/extending-properties.md)選項 頁面包含屬於特定的元件，例如程式設計語言或 VSPackage 選項組：[選項和選項頁](../../extensibility/internals/options-and-options-pages.md)。 這是通常與 UI 相關的功能，可以匯入和匯出設定：[支援使用者設定](../../extensibility/internals/support-for-user-settings.md)。

## <a name="visual-studio-services"></a>Visual Studio Services
 服務提供一組特定的元件使用的介面。 Visual Studio 提供一組可供任何元件，包括擴充功能的服務。 例如，Visual Studio 服務可讓工具視窗，顯示或隱藏起來，以動態方式啟用 Help、 狀態列或使用者介面事件的存取。 Visual Studio 編輯器也提供服務，可以匯入的編輯器延伸模組。 如需詳細資訊，請參閱 <<c0> [ 使用和提供服務](../../extensibility/using-and-providing-services.md)。

## <a name="debugger"></a>偵錯工具
 偵錯工具是語言特有的偵錯元件的使用者介面。 如果您已建立新的語言服務，您必須建立連結至偵錯工具的特定偵錯引擎。 如需詳細資訊，請參閱 < [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)。

## <a name="source-control"></a>原始檔控制
 實作原始檔控制外掛程式或 VSPackage 的詳細資訊，請參閱[原始檔控制](../../extensibility/internals/source-control.md)。

## <a name="wizards"></a>精靈
 您可以搭配使用新的專案類型來建立精靈，在建立該類型的新專案時，您的使用者，讓此精靈可協助做出正確決策。 如需詳細資訊，請參閱 <<c0> [ 精靈](../../extensibility/internals/wizards.md)。

## <a name="custom-tools"></a>自訂工具
 自訂的工具可讓您在專案中的項目相關聯的工具，並執行該工具，每次您儲存檔案。 如需詳細資訊，請參閱 <<c0> [ 自訂工具](../../extensibility/internals/custom-tools.md)。

## <a name="vssdk-utilities"></a>VSSDK 公用程式
 VSSDK 包含一組公用程式，您可能需要為了使用 Vspackage 的不同層面。 如需詳細資訊，請參閱 < [VSSDK 公用程式](../../extensibility/internals/vssdk-utilities.md)。

## <a name="using-windows-installer"></a>使用 Windows 安裝程式
 在某些情況下，您可能需要使用 Windows 安裝程式，而不是 VSIX 安裝程式： 例如，您可能需要寫入登錄。 如需使用您的擴充功能的 Windows Installer 資訊，請參閱[使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。

## <a name="help-viewer"></a>說明檢視器
 您可以將您自己的說明和 F1 頁面整合到說明檢視器中。 如需詳細資訊，請參閱 < [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)。